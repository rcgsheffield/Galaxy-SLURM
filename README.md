# Using Galaxy with the HPC

This repository contains the configuration for [connecting the Galaxy to a HPC cluster](https://docs.galaxyproject.org/en/master/admin/cluster.html). [Galaxy](https://galaxyproject.org/) is a web-based biomedical research computing platform to a SLURM HPC.

# Installation

To install and run Galaxy on a local Linux machine

See: [Get Galaxy](https://galaxyproject.org/admin/get-galaxy/) on the Galaxy Community Hub.

```bash
galaxy_version="release_24.1"
git clone -b "$galaxy_version" https://github.com/galaxyproject/galaxy.git
cd galaxy
```

This script will install the dependencies for Galaxy and run a local web server at [port 8080](http://localhost:8080/)


```bash
bash run.sh
```

# Usage

TODO

# Further reading

- Galaxy Docs [Connecting to a Cluster](https://docs.galaxyproject.org/en/master/admin/cluster.html)
- Galaxy Docs [Galaxy Job Configuration](https://docs.galaxyproject.org/en/master/admin/jobs.html)
- Galaxy Docs [Debugging Galaxy: Slurm Compute Cluster](https://docs.galaxyproject.org/en/master/dev/debugging_galaxy_slurm.html)
- Galaxy Docs API reference [galaxy.jobs.runners.slurm module](https://docs.galaxyproject.org/en/master/lib/galaxy.jobs.runners.html#module-galaxy.jobs.runners.slurm)
