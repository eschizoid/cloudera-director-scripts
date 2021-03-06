# Azure RHEL 7.2 with Security Integration - Authentication and Authorization

This is a collection of scripts to help automate the build process of Cloudera Director in the Azure Cloud.  When modifying these scripts the REPLACE_ME tag has been used so it is best to find and replace with the appropriate values.

This script requires many security and networking pieces to be ready to go.  It is assumed that AD is used as the KDC, that you want to build and maintain an internal repo, and that a DNS server is allowed to be updated via the commands used in the script (nsupdate).


## Script Order

0. Create 2 VM's for MySQL HA and 1 VM for the Director Server.
1. mysql_repo_bootstrap.sh
  * Builds MySQL (MariaDB) instance and builds an internal repository.
2. mysql_ha_boostrap.sh
  * Turns the two MySQL instances into a Master/Slave configuration.
  * NOTE: Should be run line by line as it is not setup to be run as a script - a TO DO.
3. director_bootstrap.sh
  * Builds the director instance off of the internal repository and MySQL external databases.
4. director.sh
  * Builds a complete cluster with Authentication and Authorization configured.
