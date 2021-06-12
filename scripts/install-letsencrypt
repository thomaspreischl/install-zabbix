#!/bin/sh
#
# Created on June 16, 2021
#
# @author: thomaspreischl
#

#
# Change variables below to suit your needs.
#
# Thomas Preischl
#

# MySQL root password
publicDNS="zabbix.lab.thomaspreischl.com"


# stdout and stderr for commands logged
logfile="$PWD/install_letsencrypt.log"
rm -f $logfile

# Simple logger
log(){
	timestamp=$(date +"%m-%d-%Y %k:%M:%S")
	echo "$timestamp $1"
	echo "$timestamp $1" >> $logfile 2>&1
}

log "Removing temp dir $tmpdir"
rm -rf "$tmpdir" >> $logfile 2>&1
mkdir -p "$tmpdir" >> $logfile 2>&1

log "Installing Letsencrypt..."
sudo -E apt-get -y update >> $logfile 2>&1
sudo -E apt-get -y install software-properties-common >> $logfile 2>&1
sudo -E add-apt-repository -y universe >> $logfile 2>&1
sudo -E apt-get -y update >> $logfile 2>&1

sudo -E apt-get -y install certbot python3-certbot-apache >> $logfile 2>&1

# request certificate
log "requesting Certificate for '${publicDNS}' ..."
sudo -E certbot --apache -d '${publicDNS}' >> $logfile 2>&1




