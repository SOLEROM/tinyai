# preapre

## DEPS

```
sudo apt-get install -y texinfo byacc flex libncurses5-dev zlib1g-dev \
  libexpat1-dev texlive build-essential git wget gawk bison xz-utils make \
  python3 rsync locales
```

## DW

```
mkdir arc_gnu
cd arc_gnu
git clone https://github.com/foss-for-synopsys-dwc-arc-processors/toolchain.git
git clone https://github.com/foss-for-synopsys-dwc-arc-processors/binutils-gdb.git    binutils
git clone https://github.com/foss-for-synopsys-dwc-arc-processors/gcc.git
git clone --reference binutils https://github.com/foss-for-synopsys-dwc-arc-processors/binutils-gdb.git gdb
git clone https://github.com/foss-for-synopsys-dwc-arc-processors/newlib.git
# For Linux uClibc toolchain:
git clone https://github.com/wbx-github/uclibc-ng.git
# or for Linux glibc toolchain:
git clone https://github.com/foss-for-synopsys-dwc-arc-processors/glibc.git
git clone https://git.kernel.org/pub/scm/linux/kernel/git/stable/linux-stable.git linux
```
* tree

```
/tensor/arc_gnu$ tree -L 1 .
.
├── bd-elf32
├── bd-uclibc
├── binutils
├── gcc
├── gdb
├── glibc
├── INSTALL
├── linux
├── logs
├── newlib
├── toolchain
├── uclibc-ng

```
