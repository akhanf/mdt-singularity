# mdt-singularity
Singularity recipe for Microstructure Diffusion Toolbox (MDT), a fast and flexible python toolbox for microstructural modelling (including NODDI etc..). *Note:*  I am not a developer/contributor of MDT, for more info on MDT see here:
*Code:* https://github.com/cbclab/MDT
*Docs:* http://mdt-toolbox.readthedocs.io/en/latest/index.html

I made this Singularity container for utilizing the CPUs for OpenCL on Linux systems that either have an incompatible GPU (Quadro), or no GPU (HPC systems). Installs Intel OpenCL drivers on Ubuntu 14.04 (newer versions not supported), and then installs MDT (pip3) and all dependencies (since PPA not supported on older Ubuntu version that Intel OpenCL supports). Big props to the MDT developers for creating this great toolbox -- this should hopefully make it easier for anyone to run it on an Intel CPU-based compute cluster.

*Note:* This requires Singularity to be installed (http://singularity.lbl.gov/), requires sudo privilege to build the container (local machine), but can be used without sudo privilege by copying the container to another system.

Build:
Step 1: 
```
git clone http://github.com/akhanf/mdt-singularity
cd mdt-singularity
sudo singularity build mdt.simg Singularity
```

Test:
```
singularity exec mdt.simg mdt-list-devices
```


Preliminary testing: CPU - Intel(R) Xeon(R) CPU E5-2687W v3 @ 3.10GHz (Intel(R) OpenCL), with 20 cores takes ~2.5 hours to run NODDI (Cascade) on a HCP dataset (very slow compared to what you could do with a proper GPU, but amazingly fast compared to NODDI toolbox!! (would take several days..)

