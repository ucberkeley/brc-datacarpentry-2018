% Data Carpentry workshop: Compational Resources at Berkeley and Beyond
% August 7, 2018
% Chris Paciorek


# Outline

Berkeley Research IT helps researchers through its Berkeley Research Computing (BRC) and Research Data Management (RDM) programs. 

This (brief) session will cover the following topics:

 - Savio campus cluster
     - Getting access to the system - faculty computing allowance, condo
     - Savio computing nodes
     - Cluster job submission/scheduling
 - Disk storage at Berkeley
     - Where can I put my stuff
     - Data transfer
 - National resources (XSEDE)
 - How to get help


# System capabilities and hardware

Berkeley Research Computing runs the campus cluster, Savio.

  - Savio is a >380-node, >8000-core, >169000-gpu-core Linux cluster rated at >350 peak teraFLOPS. 
     - about 174 compute nodes provided by the UC Berkeley for general access
     - about 211 compute nodes contributed by researchers in the Condo program


# Getting access to the system - FCA and condo

- All regular Berkeley faculty can request 300,000 service units (roughly core-hours) per year through the [Faculty Computing Allowance (FCA)](http://research-it.berkeley.edu/services/high-performance-computing/faculty-computing-allowance)
- Researchers can also purchase nodes for their own priority access and gain access to the shared Savio infrastructure and to the ability to *burst* to additional nodes through the [condo cluster program](http://research-it.berkeley.edu/services/high-performance-computing/condo-cluster-program)
- Instructors can request an [Instructional Computing Allowance (ICA)](http://research-it.berkeley.edu/programs/berkeley-research-computing/instructional-computing-allowance). 

Faculty/principal investigators can allow researchers working with them to get user accounts with access to the FCA or condo resources available to the faculty member.

# Savio computing nodes

[Savio](https://research-it.berkeley.edu/services/high-performance-computing) provides access to the following types of computational resources:

 - full 20/24/28 core nodes scheduled per-node
 - 'htc' nodes scheduled per-core
 - GPU nodes (scheduled per GPU)
 - big-memory nodes (scheduled per node)
 - Jupyter notebooks
 - a visualization/remote desktop node
 
Let's take a look at the hardware specifications of the computing nodes on the cluster [(see the *Hardware Configuration* section of this document)](https://research-it.berkeley.edu/services/high-performance-computing/user-guide/savio-user-guide).

The nodes are divided into several pools, called partitions. These partitions have different restrictions and costs associated with them [(see the *Scheduler Configuration* section of this document)](https://research-it.berkeley.edu/services/high-performance-computing/user-guide/savio-user-guide). Any job you submit must be submitted to a partition to which you have access.

# Submitting jobs: accounts and partitions

All computations are done by submitting jobs to the scheduling software that manages jobs on the cluster, called SLURM.

 - interactive jobs
 - batch/background jobs

Here's an example job script for a batch job. You'll need to modify the various "--" flags for your own work.

```
#!/bin/bash
# Job name:
#SBATCH --job-name=test
#
# Account:
#SBATCH --account=fc_paciorek
#
# Partition:
#SBATCH --partition=savio2
#
# Number of tasks (e.g., MPI tasks, here 2 nodes worth)
#SBATCH --ntasks=48
#
# Wall clock limit (30 minutes here):
#SBATCH --time=00:30:00
#
## Command(s) to run:
module load python/3.6
python calc.py >& calc.out
```

# Genomics on Savio: things to keep in mind

 - some standard genomics software may not be installed; in some cases we can help
 - three-day time limit for FCAs (but not condos)
 - long queue for jobs up to 10 days but limited cores and not high memory
 - memory limits sometimes are an issue

# Disk space options on Savio and on campus broadly

Here are some options for moderate-large disk storage options:

 - Savio project storage: 200 GB, backed up
 - Savio scratch: 1.5 PB shared across all users, not backed up, subject to removal
 - Savio condo (purchase) storage: roughly $6000 per 42 TB
 - Berkeley Box: unlimited, 15 GB file size limit
 - bDrive (Berkeley Google drive): unlimited
 

More details on Savio storage are here [here in the *Storage and Backup* section](https://research-it.berkeley.edu/services/high-performance-computing/user-guide/savio-user-guide).



# Data transfer for large data

Some options include:

 - [Globus](https://research-it.berkeley.edu/services/high-performance-computing/using-globus-connect-savio) (to/from Savio, laptop, XSEDE)
 - [rclone](https://research-it.berkeley.edu/services/research-data-management-service/take-advantage-unlimited-bdrive-storage-using-rclone) (to/from bDrive and Berkeley Box)

# NSF's XSEDE: To infinity and beyond

[XSEDE](https://xsede.org) provides free access to NSF-funded clusters around the US, e.g.,

 - Bridges and Comet: Savio-like clusters
    - CPUS, GPUs, big-memory
    - also generally have time limits
 - Jetstream cloud environment:
    - long-running VMs
    - GUIs
    - science gateways (e.g., interface to your own project's products)
 - there are other clusters as well

# Accessing XSEDE

Several modes of (free) access:

  - access through BRC (email brc@berkeley.edu)
  - startup allocation via application - proof of concept allocation, think 50000-100000 core-hours
  - research allocation via application

BRC can help with all of these.


# How to get additional help

 - For technical issues and questions about using Savio: 
    - brc-hpc-help@berkeley.edu
 - For questions about computing resources in general, including cloud computing: 
    - brc@berkeley.edu or research-it-consulting@berkeley.edu
 - For questions about data management (including HIPAA-protected data): 
    - researchdata@berkeley.edu or research-it-consulting@berkeley.edu
 - Office hours for any of the above topics:
     - Tues. 10-12, Wed. 1:30-3, Thur. 9:30-11:30 in AIS (Dwinelle 117)

Don't hesitate to contact us; we're friendly, even with basic questions.

# Upcoming events
 
 - Savio intro workshop Thursday September 17
 - Other trainings planned for the fall
