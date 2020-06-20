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

This guide will provide you help for compiling torch7 and waifu2x for Fedora. This is not a step by step guide, you can follow the commands but the result could be different on your maschine.

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

### torch7

### waifu2x

## torch7

You need to install the dependencies for torch7 from the previous section.

## waifu2x

You need to install the dependencies for waifu2x from the previous section.
