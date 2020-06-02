## Getting SciDAP up and running


### Mac OSX

**Installation video**

[![installation](http://img.youtube.com/vi/HvOBZuABVeM/0.jpg)](http://www.youtube.com/watch?v=HvOBZuABVeM "How to install")

OSX must be version 10.13 or newer: i.e. High Sierra (10.13), Mojave (10.14) or Catalina (10.15).
Mac hardware must be a 2013 or a newer model with at least 32GB of RAM. *We recommend 2018 [Mac mini](https://www.apple.com/mac-mini/specs/)
with 6-core i7 CPU and 32GB or 64GB memory.*

Download and install [Docker](https://hub.docker.com/editions/community/docker-ce-desktop-mac)
and

Change the default [preferences](https://docs.docker.com/docker-for-mac/#preferences#resources) for Docker
([docs](https://docs.docker.com/docker-for-mac/#preferences#resources))

* CPUs number - 2 or more
* Memory - 24GB or more (leave about 6GB to OSX)

Once the software is installed and launched you can go back to [scidap.com satellite settings](/platform/profile/satellites) add available genomes
and start the analysis.

### Linux

Follow instructions for each required package:

* [Docker](https://docker.com/)
* [CWL-Airflow](https://github.com/Barski-lab/cwl-airflow) - python3 pipeline manager
* [aria2c](https://aria2.github.io/) - download manager
* [MongoDB 4.2.x](https://www.mongodb.com/download-center/community) - NoSQL database
* [BioWardrobe-NG](https://github.com/Barski-lab/biowardrobe-ng) - micro-service to proxy commands from scidap.com to CWL-Airflow
* [pm2.io](pm2.io) - process management [https://github.com/Unitech/pm2](https://github.com/Unitech/pm2)

### Windows 10 WSL2

SciDAP satellite works on latest Windows 10 with at least WSL2. [Follow Windows 10 WSL installation guide](https://docs.microsoft.com/en-us/windows/wsl/install-win10#update-to-wsl-2)

Follow instructions for each required package:

* [Docker](https://docker.com/)
* [CWL-Airflow](https://github.com/Barski-lab/cwl-airflow) - python3 pipeline manager
* [aria2c](https://aria2.github.io/) - download manager
* [MongoDB 4.2.x](https://www.mongodb.com/download-center/community) - NoSQL database
* [BioWardrobe-NG](https://github.com/Barski-lab/biowardrobe-ng) - micro-service to proxy commands from scidap.com to CWL-Airflow
* [pm2.io](pm2.io) - process management [https://github.com/Unitech/pm2](https://github.com/Unitech/pm2)

