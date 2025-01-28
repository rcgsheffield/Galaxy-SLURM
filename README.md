# Using Galaxy with the HPC

This repository contains the configuration for [connecting the Galaxy to a HPC cluster](https://docs.galaxyproject.org/en/master/admin/cluster.html). [Galaxy](https://galaxyproject.org/) is a web-based biomedical research computing platform to a SLURM HPC.

# Installation

To install and run Galaxy on the HPC, [connect to the cluster using secure shell](https://docs.hpc.shef.ac.uk/en/latest/hpc/connecting.html#gsc.tab=0) (SSH).

Run an interactive session on a worker node

```bash
srun --pty bash -i
```

Load the [Anaconda Python](https://docs.hpc.shef.ac.uk/en/latest/stanage/software/apps/python.html#gsc.tab=0) module

```bash
module load Anaconda3
```

Create a virtual environment

```bash
conda create -n galaxy -c conda-forge python=3.12 glib yarn
source activate galaxy
export GALAXY_CONDA_ENV=galaxy
```

See: [Get Galaxy](https://galaxyproject.org/admin/get-galaxy/) on the Galaxy Community Hub.

```bash
galaxy_version="release_24.1"
git clone -b "$galaxy_version" https://github.com/galaxyproject/galaxy.git
cd galaxy
```

This script will install the dependencies for Galaxy and run the web server on port 8080


```bash
bash run.sh
```

# Usage

From your local machine, use secure shell to create a tunnel to the Galaxy port.

```bash
ssh -L 8080:10.10.1.1:8080 stanage
```

On your local machine, use a web browser to open http://localhost:8080/ 

# Further reading

- Galaxy Docs [Connecting to a Cluster](https://docs.galaxyproject.org/en/master/admin/cluster.html)
- Galaxy Docs [Galaxy Job Configuration](https://docs.galaxyproject.org/en/master/admin/jobs.html)
- Galaxy Docs [Debugging Galaxy: Slurm Compute Cluster](https://docs.galaxyproject.org/en/master/dev/debugging_galaxy_slurm.html)
- Galaxy Docs API reference [galaxy.jobs.runners.slurm module](https://docs.galaxyproject.org/en/master/lib/galaxy.jobs.runners.html#module-galaxy.jobs.runners.slurm)
