## How SciDAP works

### Overview

SciDAP is a data analysis, management and visualization system that consists of master server with web interface (https://scidap.com/) and clients (satellites) that are installed on user's hardware (server/cluster/cloud). SciDAP Master Server keeps up today web interface, stores and organizes experiment's description and data analysis pipelines in [CWL](https://commonwl.org) format. SciDAP-satellite (client) is the actual analysis executor that runs on desktops, laptops, servers, clusters, clouds with linux, windows, mac os x operational systems.

SciDAP-satellite is a free back-end data analysis component of SciDAP platform. It downloads requested data files e.g. from GEO or other urls with aria2c and executes CWL pipelines with CWL-Airflow. It provides authorized access to a requested data (raw and analyzed) from SciDAP master server by JWT tokens. In order to receive commands from the master server your satellite needs access to the Internet. However, in order to work with satellite from the web interface (https://scidap.com/) for a user the satellite does not need public access from the Internet but have to be accessible within the same local network.


### Software

In order to run the analysis [scidap.com](https://scidap.com) needs access to a private `scidap-satellite` installation. SciDAP provides a limited
and authorized access to the `scidap-satellite` installation. There are two types of `scidap-satellite` installation: per laboratory and corporate.
*For corporate installation please contact us*

**All laboratory members** can add the analysis and view the results. **Do not invite strangers** to the laboratory.

Datirium provides `scidap-satellite` bundle to simplify setup process. Otherwise
all it components must be installed and configured manually. `scidap-satellite` includes pre configured open-source software:

* [CWL-Airflow](https://github.com/Barski-lab/cwl-airflow) - python3 pipeline manager
* [aria2c](https://aria2.github.io/) - download manager
* [MongoDB 4.2.x](https://www.mongodb.com/download-center/community) - NoSQL database
* [BioWardrobe-NG](https://github.com/Barski-lab/biowardrobe-ng) - micro-service to proxy commands from scidap.com to CWL-Airflow
* [pm2.io](pm2.io) - process management [https://github.com/Unitech/pm2](https://github.com/Unitech/pm2)

The analysis runs on your hardware (where `scidap-satellite` is installed - desktop/server/cluster or cloud).
Some of our pipelines require at least 24GB of memory. We recommend **at least 32GB** per processing unit.

### Data exchange

[scidap.com](https://scidap.com) can start a pipeline from any place with the Internet. However, to access all the results a **direct connection**
to the satellite is required.
Limited information is transferred between a `scidap-satellite` installation and [scidap.com](https://scidap.com):

* Sample's metadata
* Sample's [CWL](https://www.commonwl.org/) file (CWL files can be checked at [https://github.com/datirium/workflows](https://github.com/datirium/workflows))
* Sample's status like running, failed, finished
* Sample's mapping statistics for basic analysis
