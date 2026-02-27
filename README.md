Azure-Cloud-backup(GitFilesBackup)

Concept:
	To build an automatic backup cloud setup using Azure cloud VM for the GitRepository.

Creation:
	Build an Azure VM in portal.azure.
	Create an git repository.

Steps:
	 Ceate VM in Azure
		| Field   | Value                   |
		| ------- | ----------------------- |
		| VM Name | git-backup-vm           |
		| Region  | East US                 |
		| Image   | Ubuntu Server 24.04 LTS |
		| Size    | B1s                     |
		| Auth    | Password                |
		| Port    | SSH (22)                |

	Git -> Azure
	
	ssh azureuser@<your-public-ip> 
	
	sudo apt update
	sudo apt install git -y

	git --version

	mkdir cloud-backup
	cd cloud-backup

	Create a repo
		git clone https://github.com/<your-username>/azure-cloud-backup.git
		ls

	Automate Sync

	nano autosync.sh
	
	#!/bin/bash
	cd /home/azureuser/cloud-backup/azure-cloud-backup
	git pull origin main

	ToSave → CTRL + X → Y → Enter

	chmod +x autosync.sh

	Create a corn to run automatic for every 5 mins
	crontab -e
	*/5 * * * * /home/azureuser/cloud-backup/autosync.sh


	cd ~/cloud-backup/azure-cloud-backup
	ls



To Open Project
	Open Azure VM Terminal
