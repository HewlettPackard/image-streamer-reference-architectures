# HPE Reference Configuration for Deploying Docker Datacenter on HPE Synergy with Aquasec Container Security solution

---------------------------------------------			
About
---------------------------------------------
This repo contains HPE Image Streamer plan scripts and artifact bundles to personalize and deploy 
the RHEL 7.3 Operating System and Docker Datacenter on HPE Synergy compute modules.

This specific documents details the integration with Aquasec Container Security Solution

	
Contents of the repo are:
	
	artifact-bundles : contains artifact bundles in zip format. User can import these into Image Streamer
	plan-scripts     : list of scripts to personalize the OS and Docker Datacenter

---------------------------------------------			
Pre-requisites
---------------------------------------------
	Access to Synergy platform
	Synergy composer configured with OS Deployment server 'Image Streamer'
	Access to RHEL 7.3 with Docker EE Golden image (instruction to build this image to be supplied)
	Docker Datacenter subscription license (or trial license)
	Access to the Aquasec Container Security software and license

-------------------------------------------
Custom Attributes
--------------------------------------------
	When you create a server profile in the Synergy Composer GUI, you can attach the deployment plan shipped 
	in the artifact bundle found in this repo. This example deployment plan only exposes a subset of the parameters 
	(known as "custom attributes") supported by the underlying OS build plan. It is your decision to make a custom 
	attribute visible or not in the deployment plan. Keep in mind that the less input is required for a deployment, 
	the better the user experience.

	AquaAgent
		This string specifies the location and version of the Aqua Enforcer (or repo name and tag). 

	AquaIp
		This is the IP address of the Aqua Management Console.

	AquaToken
		This is the token to use for the Agent "Batch Install". These tokens can be generated in the Aqua Console GUI. Refer to the documentation for
		more information.
		
	DeviceMapperAllocation
		A docker node deployed using this solution has two drives, the boot drive and a data drive provisionned
		from a D3940 storage module. This parameter relates to the data drive and expresses the percentage of
		the storage on this data drive which will be used for storing docker images. The rest of the space 
		available will be used by the Docker root dir (typically /var/lib/docker)

	DeviceMapperDrive
		This is the device name of the D3940 drive (see DeviceMapperAllocation above) as seen by the operating
		system. The default value is /dev/sda and you normally don't need to change this value

	DeviceMapperForceDelete
		If the D3940 data drive is not clean, the deployment plan will fail. Specify "Yes" if you want to destroy
		all the data on this drive. This custom attribute is made visible so that you know exactly that you are 
		going to erase the data on the corresponding data drive.

		
	TotalNicTeamings
		The OSBP and reference configuration configure a single network team using two network interfaces. Leave this value to "1"
		
	Team0NIC1	NIC	none
		Interface number 1 to use for management. Make sure this attribute is made visible in the Deployment Plan.
		
	Team0NIC2	NIC	none
		Interface number 2 to use for management. Make sure this attribute is made visible in the Deployment Plan.

	Team1NIC1	NIC	none
		Not used. Make sure this attribute is NOT visible in the Deployment Plan
		
	Team1NIC2	NIC	none
		Not used. Make sure you this attribute is NOT visible in the Deployment Plan

	FirstNicTeamName
	SecondNicTeamName
		This is the name of the network team(s) which will be configured on the deployed Docker node. You can leave the default names.
		
	NewRootPassword
		The root account of the deployed docker node will be configured with the password specified with this custom attribute.
		
	NtpServer	FQDN
		The IP address of an NTP server in your environment. 
	
	ProxyExclusionList	String	.cloudra.local
		A comma separated list of domain names or IP adresses which should be accessed without going thru the proxy. For those utilities (including the
		Docker daemon) which honor the http_proxy, https_proxy and no_proxy environment variables. This string is used to configure the no_proxy environment
		variable in various places in the deployed server including /etc/environment and a systemd drop-in file for use by the Docker daemon.
		
	ProxyHost	FQDN	proxy.cloudra.local
		FQDN or IP adress of the proxy server. If there is one. If you have a direct (or transparent) access to internet, remove the correspoding plan
		script from the OS Build Plan.
		
	ProxyPort	Number	8080
		Port number the proxy server is listening on.
		
	ServerFQDN	FQDN	workerXXX.cloudra.local
		The provisioned server will be configured with the FQDN you specify with this custom attribute
		
	SSH	Option	Enabled
		Specify "Enabled" if you want to enable the SSH daemon on the provisionned server, anything else (eg "Disabled") otherwise
		
	
	UcpAdminName	String	admin
		Name of the Admin account of your UCP cluster. This account must exists.
		
	UcpAdminPassword	Password	••••••••
		Password for the Admin account of your UCP cluster.
		
	UcpIp	FQDN	ucp1.cloudra.local
		IP address of one of your existing UCP node (also swarm managers). This node should be up and running.
		
	
		
---------------------------------------------			
How to use
---------------------------------------------
Option 1: Import artifact bundles found in this repo.

	Step1 : Import the artifact bundles into Image streamer and extract
	Step2 : Create a new deployment plan by copying  the supplied deployment plan (named RHEL-7.3-Docker-Worker-With-AquaSec-YYYY-MM-DD)
	Step3 : Adjust the custom attributes (see above) so that they match your environment. It is recommended to make invisible those attributes which 
			correspond to default values that never change in your environment.
	Step4 : Add golden image to the deployment plan
	Step5 : Create the server profile using the deployment plan in OneView and provide attributes required values
	
Option 2: Leverage plan scripts and customize them as per user need

-----------------------------------------------
Summary
-----------------------------------------------
These plan scripts have been tested for personalizing
    
	RHEL 7.3
	Docker EE 17.03.2-ee-4
	Docker UCP 2.1.4
	Docker DTR 2.2.4
	Aqua Container Security 2.1.6
	Aqua Agent 2.1.11103
