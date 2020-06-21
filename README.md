# Fedora waifu2x installation guide

Table of contents

- [Fedora waifu2x installation guide](#fedora-waifu2x-installation-guide)
  - [Motivation](#motivation)
  - [Background - Basic Setup](#background---basic-setup)
    - [installed Packages](#installed-packages)
  - [Dependencies](#dependencies)
    - [torch7](#torch7)
    - [waifu2x](#waifu2x)
  - [torch7](#torch7-1)
  - [waifu2x](#waifu2x-1)

This guide will provide you help for compiling torch7 ([torch7 Homepage](http://torch.ch/docs/getting-started.html)) and waifu2x ([waifu2x Github](https://github.com/nagadomi/waifu2x)) for Fedora. This is not a step by step guide, you can follow the commands but the result could be different on your maschine.

## Motivation

I write this because the information to compile this on Linux (if you are not running Ubuntu) are verly rare. To get this to work toke me 3 days and I was really frustrated from time to time.

## Background - Basic Setup

- creation date (MM-dd-yyyy): 06-10-2020
- Hardware: Intel i5 3579K, 16GB Ram, Nvidia GeForce GTX 660 Ti
- OS: Fedora 32 x86_64 (Kernel 5.6.16)
- Nvidia Driver Version: 440.82
- Cuda Version 10.2

### installed Packages

I did not know if it is really relevant what nvidia packages I have installed, but it also nice to know.

This 3 nvidia package will come when you have the nvidia driver is installed via the preconfigured Nvidia Repo.

- xorg-x11-drv-nvidia
- xorg-x11-drv-nvidia-devel
- xorg-x11-drv-nvidia-libs

I have this installed additionaly.

`dnf install xorg-x11-drv-nvidia-cuda xorg-x11-drv-nvidia-cuda-libs`

## Dependencies

lua: `dnf install lua luarocks`

### torch7

- gcc less then version 8 (required by Cuda 10.2), you will find a rpm package for gcc version 7.3 in this repo or you can take it from [stackoverflow](https://stackoverflow.com/questions/49018215/install-gcc-and-g-version-6-in-fedora-27)

### waifu2x

- cuda: can be installed from [RPM Fusion](https://rpmfusion.org/Howto/CUDA)
- some other libs: `dnf install snappy-devel GraphicsMagick-c++-devel openssl-devel`

## torch7

(this was for me the most difficult and frustrating part)

First you need to install the dependencies for torch7 from the previous section.

- clone it `git clone https://github.com/torch/distro.git torch7 --recursive`
- modify install.sh and add
  
  ``` bash
  export CC=gcc73
  export CXX=g++73
  ```

  this will tell cmake to use gcc version 7.3 as compiler
- install deps `bash install-deps`
- run `./install.sh`

Troubleshoot: if you have problem with compiling cutorch try this install command `TORCH_NVCC_FLAGS="-D__CUDA_NO_HALF_OPERATORS__" ./install.sh` ([Read more](https://github.com/torch/cutorch/issues/797#issuecomment-364602210))

Troubleshoot: if the install command can not find the installed cuda version try this [Github issue](https://github.com/torch/cutorch/issues/834#issuecomment-428767642)(I have done step 2 and 3, I removed the FindCUDA.cmake and applied the patch)

## waifu2x

First you need to install the dependencies for waifu2x from the previous section.

- clone the repo `git clone --depth 1 https://github.com/nagadomi/waifu2x.git`
- install `./install_lua_modules.sh`

Troubleshoot: if you get out of memory errors try to play around with the parameters crop_size and model_dir
