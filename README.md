# Matzke_R_binaries
 Archiving CRAN binaries of R packages (as CRAN does not)

This repository simply copies of CRAN-generated binaries of R packages necessary/useful for [BioGeoBEARS](https://github.com/nmatzke/BioGeoBEARS).  

It seems to be a regular issue that CRAN changes its choice of compilers for `C++` and `FORTRAN`. Most recently, in October 2019, packages were tested against `gfortran`/`gcc10`, which is still in beta). When this happens, legacy `FORTRAN` code can throw CRAN warnings, despite having passed all previous checks, and then CRAN can decide to archive a package. This means it will no longer be visible in the "package search" functions in R.app or RStudio.

For archived packages, CRAN does keep the source code available, but the compiled binaries for Windows and Mac OS X disappear.  This can be very inconvenient, because:

1. Binaries install very quickly, installing from source can take minutes (if it succeeds at all).
2. Binaries do not require compilation of the source code on the user's computer.
3. Therefore, binaries do not require that the user install the compilers `gfortran` and `gcc`, a process which can take hours (see e.g. [https://solarianprogrammer.com/2017/05/21/compiling-gcc-macos/](https://solarianprogrammer.com/2017/05/21/compiling-gcc-macos/) for the Mac instructions, regularly updated for each new version of OS X). (See also [macports for gcc10](https://ports.macports.org/port/gcc10/).)
4. GitHub versions of the packages also require compilation-from-source. If you have a "pure R" package (like [BioGeoBEARS](https://github.com/nmatzke/BioGeoBEARS)), this is easy and fast, but if the source code contains `C++` or `FORTRAN`, getting the right compilers and settings can be onerous for non-advanced users.

Getting non-technical users to install `gcc` and `gfortran` is onerous at best, and impossible in a 4-hour workshop.

# Method

After a CRAN package is accepted, the binaries are typically made available by CRAN within a few days. They are in this section of the package page (this section is for the [CRAN cladoRcpp page](https://CRAN.R-project.org/package=cladoRcpp)):

```
Windows binaries:	r-devel: cladoRcpp_0.15.1.zip, r-release: cladoRcpp_0.15.1.zip, r-oldrel: cladoRcpp_0.15.1.zip
OS X binaries:	r-release: cladoRcpp_0.15.1.tgz, r-oldrel: cladoRcpp_0.15.1.tgz
```

All I have done in the "Matzke_R_binaries" repository is put up the saved versions of these files. 

# Instructions

Download the most recent version number of a package, and install manually.

- In R.app on Macs, you would click `Packages & Data -> Package Installer -> Packages Repository ("Local Binary Package" option) -> click "Install..." -> navigate to the saved binary file`.
- From the R command line, type something like this: 

```
install.packages(pkgs="/GitHub/Matzke_R_binaries/cladoRcpp/cladoRcpp_0.15.1_MacRrelease.tgz", lib="/Library/Frameworks/R.framework/Resources/library/", repos=NULL, type="binary")
```

...or, if you have used `setwd()` to have the working directory set to where the binary was saved, and if you are happy with the default install location, this will probably work:

```
install.packages(pkgs="cladoRcpp_0.15.1_MacRrelease.tgz", repos=NULL, type="binary")
```

# License

All of these package versions are released under [GPL-3]. [cladoRcpp](https://CRAN.R-project.org/package=cladoRcpp) (see also [GitHub cladoRcpp](https://github.com/nmatzke/cladoRcpp)) and [rexpokit](https://CRAN.R-project.org/package=rexpokit) (see also [GitHub rexpokit](https://github.com/nmatzke/rexpokit)) are maintained by Nick Matzke. [kexpmv](https://CRAN.R-project.org/package=kexpmv) is maintained by Meabh G. McCurdy.

If you have issues getting cladoRcpp or rexpokit installed, please use the [BioGeoBEARS Google Group](http://phylo.wikidot.com/biogeobears#help) to ask for help.
