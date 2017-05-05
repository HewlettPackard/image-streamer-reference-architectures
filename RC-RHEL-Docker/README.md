# HPE Reference Configuration for Docker Enterprise Edition Standard on HPE Synergy with HPE Synergy Image Streamer 

---------------------------------------------			
About
---------------------------------------------
This repo contains HPE Image Streamer plan scripts and artifact bundles to personalize and deploy 
the RHEL 7.3 Operating System and Docker Datacenter on HPE Synergy compute modules

	
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

-------------------------------------------
Key Inputs
--------------------------------------------
	When you create a server profile in the Synergy Composer GUI, you can attach the deployment plan shipped 
	in the artifact bundle found in this repo. This deployment plan only exposes a subset of the parameters 
	(known as "custom attributes") supported by the underlying OS build plan. Custom attributes prefixed with 
	a * below are NOT exposed by the deployment plan, those WITHOUT a leading * are made visible to the end 
	users when they use the deployment plan.

	*DeviceMapperAllocation. 
		A docker node deployed using this solution has two drives, the boot drive and a data drive provisionned
		from a D3940 storage module. This parameter relates to the data drive and expresses the percentage of
		the storage on this data drive which will be used for storing docker images. The rest of the space 
		available will be used by the Docker root dir (typically /var/lib/docker)

	*DeviceMapperDrive
		This is the device name of the D3940 drive (see DeviceMapperAllocation above) as seen by the operating
		system. The default value is /dev/sda and you normally don't need to change this value

	DeviceMapperForceDelete
		If the D3940 data drive is not clean, the deployment plan will fail. Specify "Yes" if you want to destroy
		all the data on this drive. This custom attribute is made visible so that you know exactly that you are 
		going to erase the data on the corresponding data drive.

	*FirstNicTeamName
		The deployment plan expects a redundant connection to the production VLAN. It will configure a team 
		with the name specified by this parameter. The default value is team0 and end users would normally 
		not need to change this name. The reason why this attribute is not exposed by the deployment plan.

	NewRootPassword	password	Yes	********
		The root account will be configured with the pasword you specify for this attribute.

	NtpServer
		The IP adress of an NTP server in your environment.

	ProxyExclusionList
		A comma separated list of domain names which will be used to create the no_proxy environment variable
		on the deployed server. If you don't have a proxy in your environment, or use a transparent proxy, you 
		should edit the deployment plan and remove the step which configure the proxy (XXX-070-Docker-configure-proxy)
		example: .cloura.local

	ProxyHost
		The name or IP adress of your proxy server. If there is one. If you don;t have a proxy in your environment, 
		remove the plan script named XXX-070-Docker-configure-proxy.
		example: proxy.mydomain.com.  (do not specify http://proxy.mydomain.com)

	ProxyPort
		The port on which your proxy server is listening.
		example: 8080

	*SecondNicTeamName
		Reserved for future use. This attribute is not exposed by the deployment plan

	ServerFQDN
		Fully qualified domain name of the server you are about to deploy.
		example: worker3.cloudra.local

	*SSH
		Enable the SSH service and root login over ssh. The default is Enabled

	Team0NIC1
		First interface connected to your production network, when configuring this interface we recommend you use 
		manual assignment of the IP address

	Team0NIC2	
		Second interface connected to your production network, when configuring this interface we recommend you use
		manual assignment as well. Team0NIC1 and Team0NIC2 will be configured as the two slaves of a bond interface

	*Team1NIC1
		Reserved for future use

	*Team1NIC2
		Reserved for future use

	*TotalNicTeamings
		Must be set to 1. 

	UcpAdminName
		Name of the administrator account of the UCP control plane

	UcpAdminPassword
		PAssword of the Administrator account of the UCP control plans

	UcpIp
		IP address of one of your existing UCP node (also swarm managers)
		
---------------------------------------------			
How to use
---------------------------------------------
Option 1: Import artifact bundles found in this repo.

	Step1 : Import the artifact bundles into Image streamer and extract
	Step2 : Add golden image to the deployment plan
	Step3 : Create the server profile using the deployment plan in OneView and provide attributes required values
	
Option 2: Leverage plan scripts and customize them as per user need

Following are the plans scripts. Depending the use case, use the appropriate plan scripts. The numbering is just an helper. The plan script named 000-* should be the
first, the one named 999-* should be the last. Pure guestfish scripts can be placed anywhere between these two plan scripts (such as 110-*). Other plan scripts may
program actions to be performed at first boot and these actions might have to be run in a specific order. For example you want to have the network up and running before 
starting services that rely on the network

			
	000-RHEL-7.3-mount-and-validate
    010-RHEL-7.3-set-iscsi-initiatorname
	020-RHEL-7.3-change-root-password
	030-RHEL-7.3-configure-multiple-NIC-teaming
	040-RHEL-7.3-Docker-configure-ntp
	050-RHEL-7.3-configure-hostname
	060-RHEL-7.3-manage-security-services
	070-Docker-configure-proxy
	080-RHEL-7.3-erase-drive
	090-RHEL-7.3-Docker-configure-devicemapper
	100-RHEL-7.3-Docker-Bootstrap
	110-Docker-remove-key.json
	120-upload-bash-helpers
	130-RHEL-7.3-Docker-preconfig
	140-Docker-UCP-worker-configure
	150-RHEL-7.3-config-firewalld-for-Docker
	999-RHEL-7.3-unmount

			
Above plan scripts cover use cases like

	Network configuration 
	Configure multiple NICs
	Configure-NIC with NIC teamings
	Host name and alias configuration
	Changing root password
	Enabling/disabling services
			
-----------------------------------------------
Summary
-----------------------------------------------
These plan scripts have been tested for personalizing
    
	RHEL 7.3
	Docker EE 17.03.0-ee-3
	Docker UCP 2.1.1
	Docker DTR 2.2.3

