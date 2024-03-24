# Toolchian

## MWDT
* https://www.synopsys.com/dw/ipdir.php?ds=sw_jtag_gnu 
* https://github.com/foss-for-synopsys-dwc-arc-processors/ARC-Development-Systems-Forum/issues/2


```
The MetaWare Development Toolkit (MWDT) is a software development environment developed by Synopsys. It’s a complete, highly optimized tool-chain (cross-compiler, assembler, linker and utilities) targeting the ARC CPU portfolio, intended for users looking for a high-quality commercial toolset backed by an industry-leading support team. The tools are available for use from an Eclipse-based IDE or directly from the command line MWDT also includes a source level debugger which can be invoked from within the IDE or as standalone GUI or command line-based applications. The debugger is fully “ARC-aware” and provides rich profiling capabilities to investigate application hot spots and to assist with size vs speed optimizations. The same debugger interface is used for connecting to the various supported simulators (ranging from RTL simulation through to instruction set simulators) as well as ASIC and FPGA targets. The debugger supports various 3rd-party JTAG probes for connections to hardware targets. This package is sold by Synopsys and is license-controlled software.

The MetaWare Lite toolset is a free version of the commercial MetaWare Development Toolkit with certain restrictions and features including:
-Final executable size is restricted to 32Kbytes
-Source code for run-time libraries not included – tool ships with pre-built libraries for a select set of configurations
It is available for download from the Synopsys website (http://www.synopsys.com/dw/ipdir.php?ds=sw_metaware).
Registration and annual activation is required

The ARC open source tools are an alternative toolset for ARC based on GCC and GDB. It is intended for both developers targeting the ARC Linux operating system as well as those working on bare metal systems. Because of the importance of open source tools in embedded software, Synopsys invests in open source projects, such as GNU and the Linux kernel for ARC processor cores. Synopsys ensures there is up-to-date open source GNU tools support for its processors and is continuously updating and optimizing the ARC GNU Toolchain. The ARC GNU Toolchain offers all of the benefits of open source tools, including complete source code and a large install base. The tools include the GCC compiler and GDB debugger as well a number of utilities and libraries that make up a complete software tool chain. The tools are available in source code format, and also as pre-built executables for both Windows and Linux. The pre-built Windows version includes an Eclipse-based IDE.
```


## repository for the ARC GNU toolchain.
* https://github.com/foss-for-synopsys-dwc-arc-processors/toolchain
* https://github.com/foss-for-synopsys-dwc-arc-processors/toolchain/releases/


## build env
* (1) [dw and preapre src](prepare.md)
* (2) [build](build.md)
