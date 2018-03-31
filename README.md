# mdt-singularity
Singularity recipe for Microstructure Diffusion Toolbox (http://mdt-toolbox.readthedocs.io/en/latest/index.html)

Made this container for utilizing the CPUs for OpenCL on Linux systems that either have an incompatible GPU (Quadro), or no GPU (HPC systems). Installs Intel OpenCL drivers on Ubuntu 14.04 (newer versions not supported), and then installs MDT (pip3) and all dependencies (since PPA not supported on older Ubuntu version that Intel OpenCL supports). 

Tested on: CPU - Intel(R) Xeon(R) CPU E5-2687W v3 @ 3.10GHz (Intel(R) OpenCL), with 20 cores takes ~2.5 hours to run NODDI (Cascade) on a HCP dataset (very slow compared to what you could do with a proper GPU, but amazingly fast compared to NODDI toolbox!! (would take several days..)


Build:
```
git clone http://github.com/akhanf/mdt-singularity
cd mdt-singularity
sudo singularity build mdt.simg Singularity
```

Test:
```
singularity exec mdt.simg mdt-list-devices
```
