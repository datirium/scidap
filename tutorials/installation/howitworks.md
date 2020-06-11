## How SciDAP works

### Overview

SciDAP  consists of a central server (https://scidap.com/) that provides user interface and satellites that process and store the data. The satellite is typically installed on your hardware or cloud service. This can be a desktop, laptop, server, cluster or cloud running MacOs X, Linux or Windows operating systems. Alternatively, we can provide users with access to our satellite to try out SciDAP.

This design allows us to provide users with the most up-to-date interface and to quickly deploy new pipelines through the central server. At the same time, to reduce HIPAA and data security concerns, the data are kept on satellites that are controlled by users and do not leave user's network. The users can access SciDAP from any computer by logging into (https://scidap.com/).

SciDAP serves as a data processing and exchange center for the whole laboratory or institution. All authorised laboratory members can add data, execute analyses and view the results. **Do not invite strangers** to your laboratory.



![scidap-satellite explained](https://raw.githubusercontent.com/datirium/scidap/master/tutorials/installation/satellite-explained.svg)


### Technical details:
 SciDAP-satellite is the back-end data analysis and storage component of SciDAP platform. It downloads requested data files e.g. from GEO or other urls with aria2c and executes CWL pipelines with CWL-Airflow. It provides authorized access to data (raw and analyzed) via the interface provided by SciDAP central server and authorized by secure JWT tokens. In order to receive commands from the master server your satellite needs access to the Internet. However, the satellite does not need to be accessible from the Internet but in order to work with a satellite, the user needs to be in the same local network.

### Satellite software 


To perform the analysis [scidap.com](https://scidap.com) uses a private `scidap-satellite` installation. There are two types of `scidap-satellite` installation: single laboratory and institutional. See instructions for a single laboratory installation on the [tutorials page] (https://scidap.com/tutorials)
*For institutional installation please contact us*


Datirium provides `scidap-satellite` bundle to simplify setup process on Mac OS X.
On other OSes all its components have to be installed and configured manually. `Scidap-satellite` pckage includes the following pre-configured open-source software packages:

* [CWL-Airflow](https://github.com/Barski-lab/cwl-airflow) - CWL pipeline manager
* [aria2c](https://aria2.github.io/) - Download manager
* [MongoDB 4.2.x](https://www.mongodb.com/download-center/community) - NoSQL database
* [BioWardrobe-NG](https://github.com/Barski-lab/biowardrobe-ng) - Micro-service for sending commands from scidap.com to CWL-Airflow
* [pm2.io](pm2.io) - process management [https://github.com/Unitech/pm2](https://github.com/Unitech/pm2)

The analysis runs on your hardware (where `scidap-satellite` is installed - desktop/server/cluster or cloud).
Some of our pipelines require at least 24GB of memory. We recommend **at least 32GB** per processing unit.

### Data exchange

[scidap.com](https://scidap.com) can start a pipeline from any place with the Internet. However, to access all the results a **direct connection**
to the satellite is required.
Only limited information is transferred between a `scidap-satellite` installation and [scidap.com](https://scidap.com):

* Sample's metadata
* Sample's [CWL](https://www.commonwl.org/) file (CWL files can be checked at [https://github.com/datirium/workflows](https://github.com/datirium/workflows))
* Sample's status like running, failed, finished
* Sample's mapping statistics for basic analysis
