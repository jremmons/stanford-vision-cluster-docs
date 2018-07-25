# SVL Cluster Usage and SLURM Documentation

Personally, I recommend using the documentation in the sources linked below, as the documentation here is not very thorough.

## Useful SLURM Documentation Sources

* [https://cs.stanford.edu/sc](https://cs.stanford.edu/sc)
* [http://xstream.stanford.edu/docs/slurm/](http://xstream.stanford.edu/docs/slurm/)

## Resource Usage and Management

* [https://sc.stanford.edu](https://sc.stanford.edu): Web dashboard for Slurm (submitted jobs, etc.).
* [https://status.cs.stanford.edu/dashboard](https://status.cs.stanford.edu/dashboard): Useful hardware metrics, including all GPUs Mem, Util, Power, Temp.

## Basic Usage

### Login and Setup

#### Login

All logins should be through the headnode - `sc.stanford.edu`

#### Setup

Notice you have a fresh home (not AFS), so recreate your environment if necessary. If you need to, you can use the interactive bash shell (directions for accessing this are below). All the network storage (/cvgl, /cvgl2… etc) are mounted via autofs throughout the cluster.

### Useful commands

* `sinfo`: Shows partition (queue) info, note that there is “napoli-gpu" which contains all gpu nodes in the napoli cluster. There are napoli-cpu too for cpu machines.
* `squeue`: Shows your current job status. You can also use web dashboard at [http://sc.stanford.edu](http://sc.stanford.edu).
* Interactive bash shell: Get an interactive bash shell. This can only be done if you have an existing job, so if you don't already have one, you'll need to submit one. For example, on napoli111 with 1x 1080ti GPU, 16G RAM and 4CPUs,you can use the following command:
```bash
srun --partition=napoli-gpu --nodelist=napoli111 --gres=gpu:1080ti:1 --mem=16000 --cpus-per-task=4 --pty bash
```

* `sbatch`: Submit batch jobs. You can submit batch jobs via sbatch. A sample script (with comments) is available at /sailhome/software/sample-batch.sh sbatch sample-batch.sh

### Partitions

* `napoli-cpu`: Napoli CPU cluster machines
* `napoli-gpu`: Napoli GPU cluster machines
