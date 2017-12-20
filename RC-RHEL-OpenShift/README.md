# HPE Reference Configuration for Deploying Red Hat OpenShift Container Platform on HPE Synergy 
________________________________________
## About ##
________________________________________
This repo contains HPE Image Streamer plan scripts and artifact bundles to personalize and deploy the RHEL 7.4 Operating System and prepares the OS volume for OpenShift deployment.  The actual deployment of OpenShift is done by Ansible scripts and not included in the Image Streamer scripts.

This specific documents details the Image Streamer scripts used for this Reference Configuration

Contents of the repo are:

**artifact-bundles:** contains artifact bundles in zip format. User can import these into Image Streamer.    Artifact bundle is composed of Deployment plans, os-build-plans and plan-scripts

**OS-deployment-plans:** Separate deployment plans are provided for each OpenShift component.

**OS-build-plans:** Build plan combines the plan scripts in the proper order and includes custom attribute default values

**plan-scripts:**  list of scripts to personalize the OS and prepare for OpenShift deployment 

________________________________________
## Pre-requisites ##
________________________________________


- Access to Synergy platform


- Synergy composer configured with OS Deployment server 'Image Streamer'
Access to RHEL 7.4 with customized OpenShift packages preinstalled in Golden images (instruction to build these images are included in the documentation)


- Red Hat Ansible Tower, OpenShift, Satellite and CloudForms licenses
________________________________________
## Custom Attributes ##
________________________________________
When you create a server profile in the Synergy Composer GUI, you can attach the deployment plans shipped in the artifact bundle found in this repo. The example deployment plans only expose a subset of the parameters (known as "custom attributes") supported by the underlying OS build plan. The deployment is done via Ansible scripts which make use of the default values for the custom attributes. 

**ActivationKey**	string


  The Red Hat Satellite activation key.  This name is used in combination with the OrgName to register with Red Hat Satellite.  

**AnsibleSSHKey**	string

The ssh key from the Ansible server is copied to the authorized key file on deployed servers and 
allows Ansible scripts to run without login prompting.  Key is found on the Ansible server at /root/.ssh/id_rsa.pub

	
**DeviceMapperDrive**  string

This is the device name of the local volumes or D3940 drives as seen by the operating
	system. This value varies depending on the OpenShift host being deployed, the server model, as well as whether or not internal drives are present in the compute host.  The drives specified are going to be wiped and used for container deployment and for gluster storage.  Only the Container-native storage nodes require 2 drives.  Examples:

 


- Container-native storage on Gen 10 with local storage:  /dev/sdc,/dev/sdb



- Master or Infra on Gen 10 with local storage: /dev/sdb



- Worker on Gen9: /dev/sda

Gen 10 deployments of RHEL7.4 used /dev/sda for the Image Streamer (boot volume). Do not specify /dev/sda for Gen 10 servers  The values to use depend on whether or not local storage is present or not.

Gen 9 deployments of RHEL 7.4 use /dev/sda as the D3940 volume and the Image Streamer boot volume appeared as the last volume in alphabetical order.  

To determine the values needed for your environment, create a server profile with a Deployment plan to deploy the golden image and include volumes from the D3940.  Boot the server and log in. Determine which volume is the boot volume using the ‘df’ command and identify whether local drives are present and the volumes you want to use- either internal volumes or D3940 volumes. All partitions can be seen using ‘cat /proc/partitions’. 

**DeviceMapperForceDelete**  Yes/No

If the D3940 data drives are not clean, the deployment plan will fail. Specify "Yes" if you want to destroy all the data on this drive. This custom attribute is made visible so that you know exactly that you are going to erase the data on the corresponding data drives.

**DNSKey**  password

The DNS key from the DNS server which allows deployed servers to register with DNS. This information can be found in /etc/rndc.key file on the DNS server.  Specify the key name followed by the secret, separated by a colon.	Stored as a password so it can be encrypted. 
	
**NewRootPassword**  password

The root account of the deployed server will be configured with the password specified with this custom attribute.
	
**NtpServer**	FQDN

The IP address of an NTP server in your environment. 

**OrgName**  string

The Red Hat Satellite organization name.  This name is used in combination with the Activation Key to register with Red Hat Satellite.  
	
**ServerFQDN**	FQDN	

The provisioned server will be configured with the FQDN you specify with this custom attribute
	
**SSH**	Option	Enabled

Specify "Enabled" if you want to enable the SSH daemon on the provisioned server, anything else (eg "Disabled") otherwise
	
**Team0NIC1**	 IPAddr

A static IP address for the deployed OpenShift server on your production network. Select Static User Assigned for this address. This value is set by the Ansible playbooks.

**Team0NIC2**	 IPAddr

This NIC is used for teaming. Leave the default value of static. No IP address is needed.  This value is set by the Ansible playbooks.

________________________________________
## How to use ##
________________________________________
Option 1: Import artifact bundles found in this repo.

Step1 : Import the artifact bundles into Image streamer and extract
Step2 : Create new deployments plan by copying  the supplied deployment plans 

Step3 : Adjust the custom attributes (see above) so that they match your environment. It is recommended to make invisible those attributes which correspond to default values that never change in your environment.

Step4 : Add golden images to the deployment plan

Step5 : For testing purposes, Create the server profile using the deployment plan in OneView and provide attributes required values.
 
Step6 : Use Ansible Tower to deploy the entire solution.  The ansible playbooks used for this solution are available at [https://github.com/RHsyseng/ocp-on-synergy](https://github.com/RHsyseng/ocp-on-synergy).

Option 2: Leverage plan scripts and customize them as per user need
________________________________________
## Summary ##
________________________________________
These plan scripts have been tested for personalizing

Red Hat Enterprise Linux 7.4

Red Hat OpenShift Container Platform 3.7

Red Hat Gluster Storage 3.3

Red Hat Satellite 6.2

Red Hat Ansible Tower 3.2.1


