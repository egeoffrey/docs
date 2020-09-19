# Backup and Restore

There is nothing worse than losing your data after spending time to configure your eGeoffrey. Luckily, eGeoffrey does not spread files all over the filesystem so the backup process is pretty straightforward. The backup procedure detailed below, will take care of the following:

* **Software**: eGeoffrey comes in Docker containers. There is no need to back them up since are stateless, self-contained and can be quickly pulled down again at any time. Which package is installed and your login information are instead stored in the `docker-compose.yml` and `.env` files located in the directory where eGeoffrey has been installed
* **Data**: all your configuration files, database and logs are stored within the directory where eGeoffrey has been installed


## Backup Procedure

Feel free to stop eGeoffrey before backing up its data even if there is no risk to perform a hot backup:

* Log into the system hosting your eGeoffrey
* Go into the directory where eGeoffrey has been installed (e.g. `/opt/egeoffrey`)
* Backup with your favorite utility the entire directory (you must be root to do so)
    * If you want to just copy out the files, it is recommended to create an archive first (e.g. `sudo tar zcfv egeoffrey-backup.tar.gz /opt/egeoffrey`)
    
## Restore Procedure

To restore eGeoffrey in a brand new system:

* Install eGeoffrey as [you would normally do](/installation/install)
* Stop eGeoffrey with `sudo egeoffrey-cli stop`
* Optionally remove the directory just created (e.g. `/opt/egeoffrey`) in case would be in the same location of your backed up data
* Move the latest backup to the system and, if an archive, uncompress it (e.g. `sudo tar zxfv egeoffrey-backup.tar.gz`) 
* relocate the directory to the location you prefer (e.g. `/opt/egeoffrey`)
* Go into the directory (e.g. `cd /opt/egeoffrey`)
* Start eGeoffrey with `sudo egeoffrey-cli start`. All the packages configured will be then downloaded again and eGeoffrey will be started with the configuration saved in the backup