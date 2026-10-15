# Transcriptomic-Data-Analysis-Pipeline-for-C.-elegans
A reproducible bioinformatics pipeline for analyzing RNAi-induced transcriptomic changes in C. elegans, including data preprocessing, statistical testing, and clustering.

# Server Guidelines
See server setup to configure access to the servers, setup conda, and add ssh keys for rsync (and other applications).

Access You can only use the legio.bioit.labnet server (short: halo)
Connection To connect with legio, first connect to the IDLab VPN, then use the same credentials to connect to the server through ssh.
Resource Limits Limit your usage to 20 nodes, 100GB RAM, 1TB disk, 100k files. Contact supervisors if you require additional resources.
Data Storage Store all data and scripts in legio:/data/dp4 so everyone in the group can access them. You can use personal subdirectories of this directory for individual work.
File Management
separate data, scripts, and results
use GitHub for version control of scripts and environment files
always specify software/script versions
regularly backup important results
clearly document each experiment

# Mockdata KRAS & TP53
directory 'mockdata'
first 100 lines of each datafile (head -n 100 file.csv)
sorted in directories 'KRAS' and 'TP53'
metadata and .mtx files still present
