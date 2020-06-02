## Windows Installation

### Windows 10 WSL2

SciDAP satellite works on latest Windows 10 with at least WSL2. [Follow Windows 10 WSL installation guide](https://docs.microsoft.com/en-us/windows/wsl/install-win10#update-to-wsl-2)

Follow instructions for each required package:

* [Docker](https://docker.com/)
* [CWL-Airflow](https://github.com/Barski-lab/cwl-airflow) - python3 pipeline manager
* [aria2c](https://aria2.github.io/) - download manager
* [MongoDB 4.2.x](https://www.mongodb.com/download-center/community) - NoSQL database
* [BioWardrobe-NG](https://github.com/Barski-lab/biowardrobe-ng) - micro-service to proxy commands from scidap.com to CWL-Airflow
* [pm2.io](pm2.io) - process management [https://github.com/Unitech/pm2](https://github.com/Unitech/pm2)

