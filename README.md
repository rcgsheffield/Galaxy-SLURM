# Using Galaxy with the HPC

This repository contains the configuration for [connecting the Galaxy to a HPC cluster](https://docs.galaxyproject.org/en/master/admin/cluster.html). [Galaxy](https://galaxyproject.org/) is a web-based biomedical research computing platform to a SLURM HPC.

The current version of Galaxy is incompatible with Centos 7, which is used on Stanage (as of January 2025) so a container image is provided which can be run using [Apptainer](https://docs.hpc.shef.ac.uk/en/latest/stanage/software/apps/apptainer.html).

# Installation

To install and run Galaxy on the HPC, [connect to the cluster using secure shell](https://docs.hpc.shef.ac.uk/en/latest/hpc/connecting.html#gsc.tab=0) (SSH).

## Build the container

On your local machine

```bash
apptainer build --force galaxy.sif galaxy.def
```

Upload the image to the cluster

```bash
rsync galaxy.sif stanage:~/galaxy.sif
```

Create a directory to contain the Galaxy database, used for its working operations.

```bash
ssh stanage "mkdir --parents galaxy/database"
```

# Usage

Access the cluster using a [graphical desktop session](https://docs.hpc.shef.ac.uk/en/latest/hpc/flight-desktop.html#gsc.tab=0).

Open a terminal and run the following command to run Galaxy.

```bash
/usr/local/bin/apptainer run --bind galaxy/database:/opt/galaxy/database --net --network-args "portmap=8080:8080/tcp" galaxy.sif
```

Open a web browser and open http://localhost:8080

# Further reading

- Galaxy Docs [Connecting to a Cluster](https://docs.galaxyproject.org/en/master/admin/cluster.html)
- Galaxy Docs [Galaxy Job Configuration](https://docs.galaxyproject.org/en/master/admin/jobs.html)
- Galaxy Docs [Debugging Galaxy: Slurm Compute Cluster](https://docs.galaxyproject.org/en/master/dev/debugging_galaxy_slurm.html)
- Galaxy Docs API reference [galaxy.jobs.runners.slurm module](https://docs.galaxyproject.org/en/master/lib/galaxy.jobs.runners.html#module-galaxy.jobs.runners.slurm)
