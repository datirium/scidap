## How SciDAP works

### Overview

SciDAP  consists of a central server (https://scidap.com/) that provides user interface and data processing and storage satellites. The satellite is typically installed on your hardware or cloud service. This can be a desktop, laptop, server, cluster or cloud running MacOs X, Linux or Windows operating systems. Alternatively, we can provide users with access to our satellite to try out SciDAP.
This design allows us provide users with the most up to date interface and quickly deploy new pipelines through the central server. At the same time, the data are kept on satellites that are controlled by users reducing HIPAA and data security concerns. The users can access SciDAP from any computer by logging into (https://scidap.com/).

Technical details: SciDAP-satellite is the back-end data analysis and storage component of SciDAP platform. It downloads requested data files e.g. from GEO or other urls with aria2c and executes CWL pipelines with CWL-Airflow. It provides authorized access to data (raw and analyzed) via the interface SciDAP central server authorized by secure JWT tokens. In order to receive commands from the master server your satellite needs access to the Internet. However, the satellite does not need to be accessible from the Internet: in order to work with a satellite, the user needs to be in the same local network.

![scidap-satellite explained](https://raw.githubusercontent.com/datirium/scidap/master/tutorials/installation/satellite-explained.svg)


### Software

In order to run the analysis [scidap.com](https://scidap.com) needs access to a private `scidap-satellite` installation. SciDAP provides a limited
and authorized access to the `scidap-satellite` installation. There are two types of `scidap-satellite` installation: per laboratory and corporate.
*For corporate installation please contact us*

**All laboratory members** can add the analysis and view the results. **Do not invite strangers** to the laboratory.

Datirium provides `scidap-satellite` bundle to simplify setup process on Mac OS X.
On other OSes all its components have to be installed and configured manually. `scidap-satellite` includes pre configured open-source software:

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
