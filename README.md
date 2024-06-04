# 3sSLFMFoam-6

## General Information
A package for simulations of turbulent nonpremixed flames using three-feed stream steady laminar flamelet model (3s-SLFM) in OpenFOAM 6.0. It is also applicable for traditional two-feed stream configurations using steady laminar flamelet model (SLFM) in which main part of the code for SLFM is developed based on the _flameletFoam_ code (in OF.2.3.x)[1] by Muller et al. [2].

## Flamelet models can be used with this package
- Steady laminar flamelet model (SLFM) [2, 3].
- Three-feed stream steady laminar flamelet model (3s-SLFM) [4,5]

## Installation
- Since this solver is developed based on OpenFOAM 6.0 in Linux operating systems, the complete installation of OpenFOAM 6.0 framework is required. 
- Prepare a directory on your system, e.g., _yourDirectory_:

		mkdir ~/OpenFOAM/yourDirectory/
		cd ~/OpenFOAM/yourDirectory/	
- Download source files using git: 

		git clone https://github.com/danhnam11/3sSLFMFoam-6.git

- Specify the path of your _src_ directory to an environment variable, _LIB_3sSLFM_SRC_. For example:

		echo "export LIB_3sSLFM_SRC=~/OpenFOAM/yourDirectory/3sSLFMFoam-6/src/" >> ~/.bashrc
		source ~/.bashrc
- To compile the necessary libraries and solver, go to _3sSLFMFoam-6_ directory and run the _Allwmake_ script:

		cd ~/OpenFOAM/yourDirectory/3sSLFMFoam-6/
		./Allwmake

- Now all necessary libraries inlcuding _flameletCombustionModels_ library (for flame based models), solvers such as _SLFMFoam_, _3sSLFMFoam_, and pre- and post-processing utilities _flameletToFoam_, _3sFlameletToFoam_, _postSLFMFoam_, _post3sSLFMFoam_ are stored at _$FOAM_USER_LIBBIN_ and _$FOAM_USER_APPBIN_ directory. These newly compiled libraries, solvers, and utilities are ready to be used.

- To remove all compiled libraries and solvers, go to _3sSLFMFoam-6_ directory and run the _Allwclean_ script:

		cd ~/OpenFOAM/yourDirectory/3sSLFMFoam-6/
		./Allwclean

## Using this package 
- Upon completing the compilation process, all solvers and utilities can be utilized with different flamelet models by simply typing _SLFMFoam_ (for using SLFM) or _3sSLFMFoam_ (for using 3s-SLFM) in the terminal. All important instructions for case setting can be found in _tutorial_ directory. 
- Pre-processing: It is importance to note that the pre-processing step is essential. 1-D flamelet database for generating flamelet table can be prepared by using either _FlameMaster_ code [6], _Cantera_ [7], or _CHEMKIN_(OPPDIF) [8]. Details of the pre-processing step is provided in _documentations_ directory. 
- Post-processing: The _SLFMFoam_ and _3sSLFMFoam_ solvers are designed to not save all species mass fraction (Yi) files into time directories during running simulation. After running simulations, you have to use post-processing utilities to get Yi fields. To do so, just simply type _postSLFMFoam_ (for using SLFM) or _post3sSLFMFoam_ (for using 3s-SLFM) in the terminal. If you want to save all Yi fields during the simulation, you can see the guidline of the solver in the _documentations_ directory.

- Readers are referred to our paper for all validation data.

## Tutorials
Tutorials for RANS/LES of HM3 test case is available in the _tutorial_ directory.

	cd ~/OpenFOAM/yourDirectory/3sSLFMFoam-6/tutorials/

## Authors 
This package was developed at Clean Combustion & Energy Research Lab., Dept. of Mech. Engineering, Ulsan National Institute of Science and Technology (UNIST), Korea (Prof. C.S. Yoo: https://csyoo.unist.ac.kr/). If you publish results that are obtained using this package, please cite our papers as follows:
- D. N. Nguyen, C. S. Yoo, 3sSLFMFoam: A package for simulations of turbulent non-premixed flames using three-feed stream steady laminar flamelet model in OpenFOAM, Computer Physics Communications (2024)(submitted).

Contact:
- danhnam11@gmail.com or nam.nguyendanh@hust.edu.vn 

## Reference
- [1] original _flameletFoam_ code: https://github.com/flameletFoam/flameletFoam-2.3.x
- [2] H. Muller, F. Ferraro, M. Pfitzner, Implementation of a Steady Laminar Flamelet Model for non-premixed combustion in LES and RANS simulations, in 8th Int. OpenFOAM Workshop, Jeju, Korea, 2013.
- [3] N. Peters, Laminar diffusion flamelet models in non-premixed turbulent combustion, Prog. Engery Combust. Sci. 10 (1984) 319-339.
- [4] M. Ihme, Y. C. See, LES famelet modeling of a three-stream MILD combustor: Analysis of fame
sensitivity to scalar infow conditions, Proceedings of the Combustion Institute 33 (2011) 1309-1317
- [5] G. Indelicato, P. E. Lapenna, R. Concetti, M. Caputo, M. Valorani, G. Magnotti, F. Creta, Numerical
investigation of high pressure co2-diluted combustion using a famelet-based approach, Combustion
Science and Technology 192 (2020) 2028-2049.
- [6] H. Pitsch, FlameMaster: A C++ computer program for 0D combustion and 1D laminar fame calculations, https://www.itv.rwth-aachen.de/downloads/flamemaster.
- [7] D. G. Goodwin, R. L. Speth, H. K. Moffat, B. W. Weber, Cantera: An object-oriented software toolkit
for chemical kinetics, thermodynamics, and transport processes, https://www.cantera.org, version
2.5.1 (2021). doi:10.5281/zenodo.4527812. 
- [8] A. E. Lutz, R. J. Kee, J. F. Grcar, F. M. Rupley, OPPDIF: A FORTRAN program for computing
opposed-fow diffusion fames, Tech. Rep. SAND-96-8243, Sandia National Labs., Livermore, CA, USA
29(1997).
