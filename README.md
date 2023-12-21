# DrGPUM

[![DOI](https://zenodo.org/badge/DOI/10.5281/zenodo.7588406.svg)](https://doi.org/10.5281/zenodo.7588406)
[![CodeFactor](https://www.codefactor.io/repository/github/lin-mao/drgpum/badge)](https://www.codefactor.io/repository/github/lin-mao/drgpum)
[![Documentation Status](https://readthedocs.org/projects/drgpum/badge/?version=latest)](https://drgpum.readthedocs.io/en/latest/?badge=latest)


DrGPUM is a memory profiler for NVIDIA GPUs to explore memory inefficiencies in GPU-accelerated applications.

## Quick Start

```bash
git clone --recursive https://github.com/Lin-Mao/DrGPUM.git && cd DrGPUM

git submodule update --init --recursive

# Specify PyTorch dir
export PYTORCH_DIR=path_to_pytorch/torch

# Install DrGPUM
./bin/install

# Setup environment variables
export DrGPUM_PATH=$(pwd)/gvprof
export PATH=${DrGPUM_PATH}/bin:$PATH
export PATH=${DrGPUM_PATH}/hpctoolkit/bin:$PATH
export PATH=${DrGPUM_PATH}/redshow/bin:$PATH

# Test a sample
cd samples/vectorAdd.f32
make
gvprof -v -e memory_liveness ./vectorAdd
```

## Documentation

- [Installation Guide](https://drgpum.readthedocs.io/en/latest/install.html)
- [User's Guide](https://drgpum.readthedocs.io/en/latest/manual.html)
- [Developer's Guide](https://drgpum.readthedocs.io/en/latest/workflow.html)

## Papers

- Mao Lin, Keren Zhou, and Pengfei Su. 2023. [DrGPUM: Guiding Memory Optimization for GPU-accelerated Applications](https://doi.org/10.1145/3582016.3582044). In Proceedings of the 28th ACM International Conference on Architectural Support for Programming Languages and Operating Systems, Volume 3 (ASPLOS ’23), March 25–29, 2023, Vancouver, BC, Canada. ACM, New York, NY, USA, 15 pages.
