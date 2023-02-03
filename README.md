# DrGPUM

[![DOI](https://zenodo.org/badge/DOI/10.5281/zenodo.7588406.svg)](https://doi.org/10.5281/zenodo.7588406)
[![CodeFactor](https://www.codefactor.io/repository/github/gvprof/gvprof/badge/develop)](https://www.codefactor.io/repository/github/gvprof/gvprof/overview/develop)
[![Documentation Status](https://readthedocs.org/projects/gvprof/badge/?version=latest)](https://gvprof.readthedocs.io/en/latest/?badge=latest)


DrGPUM is a memory profiler for NVIDIA GPUs to explore memory inefficiencies in GPU-accelerated applications.

## Quick Start

```bash
git clone --recursive https://github.com/Lin-Mao/DrGPUM.git && cd DrGPUM

# Specify PyTorch dir
export PYTORCH_DIR=path_to_pytorch/torch

# Install DrGPUM
./bin/install

# Setup environment variables
export GVProfInstall=$(pwd)/gvprof
export PATH=${GVProfInstall}/bin:$PATH
export PATH=${GVProfInstall}/hpctoolkit/bin:$PATH
export PATH=${GVProfInstall}/redshow/bin:$PATH

# Test a sample
cd samples/vectorAdd.f32
make
gvprof -e redundancy ./vectorAdd
```

## Documentation

- [Installation Guide](https://gvprof.readthedocs.io/en/latest/install.html)
- [User's Guide](https://gvprof.readthedocs.io/en/latest/manual.html)
- [Developer's Guide](https://gvprof.readthedocs.io/en/latest/workflow.html)

## Papers

- Keren Zhou, Yueming Hao, John Mellor-Crummey, Xiaozhu Meng, and Xu Liu. [GVProf: A Value Profiler for GPU-based Clusters](https://dl.acm.org/doi/10.5555/3433701.3433819). In: *The International Conference for High Performance Computing, Networking, Storage, and Analysis* (SC), 2020
