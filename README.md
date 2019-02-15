# pbs-torque

This profile configures Snakemake to run on the [Torque Scheduler](http://www.adaptivecomputing.com/products/open-source/torque/).

## Setup

### Deploy profile

To deploy this profile, run

    mkdir -p ~/.config/snakemake
    cd ~/.config/snakemake
    cookiecutter https://github.com/meono/pbs-torque.git

Then, you'll need to customize/modify the config.yaml file in ~/.config/snakemake. Pay attention to the script paths (eg.):

     cluster: "/home/user/.config/snakemake/pbs-torque/pbs-submit.py -A cu_10010 -W group_list=cu_10010 --depend \"{dependencies}\""
     cluster-status: "/home/user/.config/snakemake/pbs-torque/pbs-status.py"
     jobscript: "/home/user/.config/snakemake/pbs-torque/pbs-jobscript.sh"
     jobs: 100
     immediate-submit: true
     verbose: true
     notemp: true
     max-jobs-per-second: 1
     local-cores: 1
     rerun-incomplete: true
     keep-going: true

Then, you can run Snakemake with

    snakemake --profile pbs-torque ...


### Parameters

The following resources are supported by on a per-rule basis:

**node** - set the ppn resource request (defaults to the thread declaration).  
**mem** - set the memory resource request (bytes).  
**walltime** - set the walltime resource (secs).  
