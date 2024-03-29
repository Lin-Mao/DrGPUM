# Preface

DrGPUM is a memory profiling tool for applications running on GPU clusters, with advanced features for value based profiling and analysis.

The following diagram describes how components communicate with each other.

```
                                                                                                                                           
   -------------       ---------------------       ------------------------      *************************************
   | GPU Patch |  <->  | Profiling Runtime |  <->  | Measurement Analysis |  ->  ** Program Analyzer and Aggregator **  ->  Performance Reports
   -------------       ---------------------       ------------------------      *************************************
                                                            |                                                                   /|\
                                                            |--------------------------------------------------------------------|

```

## HPCToolkit (Profiling Runtime)

[*HPCToolkit*](http://hpctoolkit.org/) is a powerful profiling tool that measures application performance on the world's largest supercomputers.
DrGPUM customizes HPCToolkit and uses it as the default profiling runtime.
Currently, we are developing on HPCToolkit's [*sanitizer*](https://github.com/Lin-Mao/hpctoolkit) version.

## Redshow

[*Redshow*](https://github.com/Lin-Mao/redshow) is a postmortem metrics analysis substrate.
It receives data from the profiling runtime, performs analysis enabled by the user, and store the analysis result onto the disk.
Besides, redshow maintains the information of data objects allocated at runtime.
Redshow also contains binary analysis modules to map virtual addresses to function index and symbol names and analyze GPU instruction characteristics.

## GPU Patch

*GPU Patch* includes several implementation of instrumentation callbacks and a GPU-CPU communication system.
It can collect GPU memory metrics, block enter/exit records, and GPU call/ret records (under development).
The collected data are stored on a GPU buffer.
The profiling runtime observes a signal once the GPU buffer is full and copies data from the GPU to the CPU.

## Program Analyzer and Aggregator

Some high level performance metrics are output to performance reports directly. 
Low level detailed performance metrics are associated with individual functions and lines.
Therefore, we analyze program structure to attribute these metrics.
Moreover, when analyzing application running on multiple nodes, we can aggregate performance data together to compute overall metrics that represent the entire execution.
