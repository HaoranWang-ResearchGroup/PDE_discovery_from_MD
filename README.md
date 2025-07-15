# PDE-Discovery from MD
1. Dataset title: PDE-Discovery from MD
2. Principal Investigator: 
   - Name: Haoran Wang, Ph.D.
   - Institution: Utah State University
   - Email: haoran.wang@usu.edu
   - ORCiD ID: 0000-0002-0769-600X
3. First Author:
   - Name: Wongelemengist Nadew  
   - Institution: Utah State University
   - Email: wongelemengist.nadew@usu.edu
   - ORCiD ID: 0009-0003-9448-2249
4. Funding source: NSF 
   - Grant Number: NSF-CMMI-2138431
5. Abstract:
Governing partial differential equations (PDEs) play a critical role in materials research and applications, as they describe essential physics underlying materials behavior. Traditionally, these equations are developed through phenomenological modeling of experimental results or first-principles analysis based on conservation laws. Meanwhile, molecular dynamics (MD) simulations capture atomistic-scale behavior with detailed physics. However, translating atomistic insights into continuum-scale governing equations remains a significant challenge. Empowered by recent advances in data-driven modeling, we develop a computational framework to learn governing PDEs directly from atomistic simulation data. The framework integrates numerical differentiation of MD data with the identification of constitutive relationships. It proves effective and efficient in learning governing PDEs from noisy and small MD datasets, without requiring prior knowledge of the final PDEs. Using this framework, we identify a nonlinear PDE governing solid-state diffusion in nickel-hydrogen alloys. This PDE reveals a highly concentration-dependent diffusivity that varies over an order of magnitude. Our data- driven computational framework paves the way for cross-scale constitutive modeling.
6. Data Desciption:
   - ".mat" files can be opened by both Matlab and Python (needs scipy package)  
   - LAMMPS input files can be run using the LAMMPS software to generate the validation Dataset
   1. Monte Carlo (MC) random walk simulation data  used for PDE identification:
         - These files can be accessed by both Matlab and Python [using scipy.io.loadmat]
         - The initial condition (IC) and boundary conditions (BCs) are also given for each file.
         - It contains: Concentration data(C), Flux data (J), and First-order spatial Derivative(Cz)
         - Each data is a 2D matrix: 
               - Axis 1: Position (z); dz = 1
               - Axis 2: Time(ns); dt = 100
       1. MC_0_boundary_flux.mat
               - IC: c(z) = 0.2-0.001*z
               - BCs: j(z=0) = 0   and j(z=200) = 0 
       2. MC_delete.mat
               - IC: c(z) = 0.1
               - BCs: j(z=0) = -0.000625      and j(z=200) = 0
       3. MC_deposit.mat
               - IC: c(z) = 0.0
               - BCs: j(z=0) = 0.0003125    and j(z=200) = 0

   2.  Molecular dynamics (MD) simulation data for H diffusion in Ni used for PDE identification:
         - These files can be accessed by both Matlab and Python [using scipy.loadmat]
         - The initial condition (IC) and boundary conditions (BCs) are also given for each file.
         - It contains: Concentration data(C), Flux data (J), and First-order spatial Derivative(Cz)
         - Each data is a 2D matrix: 
               - Axis 1: Position (z); dz = 1
               - Axis 2: Time(ns); dt = 0.25 ns
       1. MD_0_boundary_flux.mat
               - IC: c(z) = 1 -(1/160)*z
               - BCs: j(z=0) = 0   and j(z=160) = 0 
       2. MD_delete.mat
               - IC: c(z) = 0.1
               - BCs: c(z=0) = 0 every 0.1 ns      and j(z=160) = 0
       3. MD_deposit.mat
               - IC: c(z) = 0.0
               - BCs: j(z=0) = 1/ns    and j(z=160) = 0
   3. LAMMPS files used for validation:
      1. in.LinearC_ValidateCase1: LAMMPS input file for Case 1
            IC: linear initial c Profile
      2. in.ExpC_ValidateCase2: LAMMPS input file for Case 2
            IC: exponential initial c Profile
      3. Ni_H.alloy: EAM Interatomic potential
      4. data.center_layer_H_800K: LAMMPS data file containing coordinates of H-atoms used for deposition simulations.
7. Desciption of parameters/variables and units:
   - c: "Concentration": dimensionless
   - j: "Flux": dimensionless for MC, 1/ns for MD
   - ns: "nano-seconds"
8. Desciption of data collection and processing:
   - Monte Carlo data are generated using Matlab from 10 simulations with different random seeds.
   - Molecular dynamics data are generated  from 10 simulations with different random seeds.
9. Publication that uses this dataset:
   - Journal: Proceedings of Royal Society A
   - Title: Learning the Governing Partial Differential Equation of Solid Diffusion from Atomistic Simulations
   - Year: 2025
