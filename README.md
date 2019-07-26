# Nonreflecting Boundary Condtion Module
This module was developed by [ATA Engineering](http://www.ata-e.com) as an 
add-on to the Loci/CHEM computational fluid dynamics (CFD) solver. The module 
is useful to reduce reflections emanating from boundary conditions during 
unsteady simulations. This can be critical in analyses where accurately 
resolving pressure fluctuations is important. Such analyses include large
eddy simulations, aeroacoustic simulations, and combustion instability 
simulations.

# Dependencies
This module depends on both Loci and CHEM being installed. Loci is an open
source framework developed at Mississippi State University (MSU) by Dr. Ed 
Luke. The framework provides a rule-based programming model and can take 
advantage of massively parallel high performance computing systems. CHEM is a 
full featured open source CFD code with finite-rate chemistry built on the Loci 
framework. CHEM is export controlled under the International Traffic In Arms 
Regulations (ITAR). Both Loci and CHEM can be obtained from the 
[SimSys Software Forum](http://www.simcenter.msstate.edu) hosted by MSU.

# Installation Instructions
First Loci and CHEM should be installed. The **LOCI_BASE** environment
variable should be set to point to the Loci installation directory. The 
**CHEM_BASE** environment variable should be set to point to the CHEM 
installation directory. The installation process follows the standard 
make, make install procedure.

```bash
make
make install
```

# Usage
First the module must be loaded at the top of the **vars** file. 
The user can then specify nonreflecting inflow and/or outflow boundary 
conditions. The nonreflecting versions of inflow and outflow accept the same
input as their reflecting counterparts, but can also take additional input
regarding the simulation domain length scale and a boundary condition constant.
The moudle should only be used for time accurate simulations.

```
loadModule: nonreflecting

boundary_conditions:<BC_1=inflowNRBC(p=101300 Pa, T=300K, M=0.5, sigma=0.25, length=0.1 m),
                     BC_2=outflowNRBC(p=101300 Pa, sigma=0.25, length=0.1 m)>
```

