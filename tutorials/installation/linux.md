## Linux Installation and Configuration

For Linux-family operating systems **scidap-satellite** is shipped in a form of relocatable `scidap-satellite-ubuntu-vX.Y.Z.tar.gz` archive.

### Installation

- Install and configure **Docker** ([see details here](https://docs.docker.com/engine/install/ubuntu/))

- Install **Node 12.X** ([see details here](https://github.com/nodesource/distributions/blob/master/README.md#debinstall))
   ```bash
   curl -sL https://deb.nodesource.com/setup_12.x | sudo -E bash -  # to get Node 12.X and npm
   sudo apt-get install nodejs
   ```
- Install **PM2** process manager ([see details here](https://github.com/Unitech/pm2#installing-pm2))
   ```bash
   npm install pm2 -g
   ```

- Download the latest version of [scidap-satellite-ubuntu-v2.0.2.tar.gz](https://scidap.nyc3.digitaloceanspaces.com/ubuntu/scidap-satellite-ubuntu-v2.0.2.tar.gz)


- Extract downloaded `scidap-satellite-ubuntu-vX.Y.Z.tar.gz` into an empty folder. Here we use `satellite` folder.
  ```bash
  mkdir satellite
  # Note, the initial location of scidap-satellite-ubuntu-v2.0.2.tar.gz might be different
  mv scidap-satellite-ubuntu-v2.0.2.tar.gz satellite                  
  cd satellite
  tar xzf scidap-satellite-ubuntu-v2.0.2.tar.gz
  ```
### Configuration and Running

- Create `scidap_settings.json` configuration file in the `~/.config/scidap-satellite` folder
  ```bash
  mkdir -p ~/.config/scidap-satellite
  cp ./configs/scidap_default_settings.json ~/.config/scidap-satellite/scidap_settings.json
  ```

- In the created `scidap_settings.json` configuration file set a correct value for `satelliteSettings.rcServerToken` field. To obtain a token click on the **Get Token** button on your **Profile -> Satellites** page in [SciDAP](https://scidap.com/).

- If necessary refer to [default configuration parameters](#default-configuration-parameters) section to update other parameters.
  
- Start **scidap-satellite** with **PM2**
  ```bash
  pm2 start ./configs/ecosystem.config.js
  ```
  An alternative location of `scidap_settings.json` configuration file can be set with `SCIDAP_SETTINGS` environment variable.


### Default configuration parameters
- `defaultLocations.airflow` and `defaultLocations.pgdata` define the locations for airflow configuration and PostreSQL database files correspondingly. If they are set as relative paths, they by default will be resolved based on the `satelliteSettings.systemRoot`.
- `satelliteSettings` section is mainly used by NJS-Client. `systemRoot` defines the location where all analyses data will be saved. If it's set as a relative path, it will be resolved based on the user's home directory.
- all parameters from `airflowSettings` section will be applied to `airflow scheduler` and `cwl-airflow api`. It may include any valid parameter from `airflow.cfg` in a form of `"section__parameter": "value"`.
- all parameters from `aria2cSettings` section will be applied to `aria2c`. It may include any valid for Aria2c argument in a form of `"--flag": "value"`.
- `databaseSettings` section defines parameters for the running PostgreSQL database, that is always bound to `127.0.0.1` so it's safe keep default values unless additional security measures needed.
- `devel` section defines parameters used during developing and should not be changed.


```yaml
{
    "defaultLocations": {
        "airflow": "airflow",
        "pgdata": "pgdata"
    },
    "satelliteSettings": {
        "rcServerToken": "",
        "rcServer": "api-sync.scidap.com:8080",
        "port": 3069,
        "airflowAPIPort": 8080,
        "systemRoot": "./scidap",
        "aria2cPort": 6800,
        "pm2Port": 9615,
        "enableSSL": true,
        "localFiles": true,
        "proxy": "",
        "noProxy": "",
        "remotes": {
            "directurl": {
                "protocol": [
                    "ftp",
                    "http",
                    "https"
                ],
                "caption": "ftp"
            },
            "geo": {
                "protocol": "geo",
                "caption": "geo"
            }
        }
    },
    "airflowSettings": {
        "core__executor": "LocalExecutor",
        "core__parallelism": 1,
        "core__dag_concurrency": 1,
        "core__max_active_runs_per_dag": 1,
        "core__hostname_callable": "socket.gethostname"
    },
    "aria2cSettings": {
        "--console-log-level": "debug",
        "--remove-control-file": true,
        "--allow-overwrite": true,
        "--auto-file-renaming": false
    },
    "databaseSettings":{
        "db_port": 5432,
        "db_user": "airflow",
        "db_password": "airflow",
        "db_name": "airflow"
    },
    "devel":{
        "simulation": false,
        "mac_update_from_devel": false
    }
}
```