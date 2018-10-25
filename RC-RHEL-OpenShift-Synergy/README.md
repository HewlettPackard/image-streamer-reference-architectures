## About ##
________________________________________
This repo contains the HPE Image Streamer plan scripts and artifact bundle to personalize and deploy Red Hat Enterprise Linux 7.5 and prepare the OS volume for Red Hat OpenShift worker node deployment. The actual deployment of Red Hat OpenShift is done by Ansible scripts found in the deployment guide at https://github.com/HewlettPackard/hpe-openshift-solutions/DeploymentGuides/HPE3PAR and at https://github.com/HewlettPackard/hpe-solutions-openshift/tree/master/synergy/scalable
This document details the HPE Image Streamer artifacts used to create this solution. 

The contents of this repo are:

**artifact-bundles:** contains the artifact bundles in zip format. The user can import these into HPE Image Streamer. Artifact bundles are composed of os-build-plans and plan-scripts.

**OS-build-plans:** Build plans combine the plan scripts in the proper order and include custom attribute default values.

**plan-scripts:**  This is a list of scripts to personalize the OS and prepare for OpenShift deployment.

________________________________________
## Pre-requisites ##
________________________________________


- Access to an HPE Synergy platform


- A HPE Synergy Composer configured with OS Deployment Server ('HPE Image Streamer')
- Access to a Red Hat Enterprise Linux 7.5 ISO (instructions to build the image is included in the documentation at https://github.com/HewlettPackard/hpe-openshift-solutions/DeploymentGuides/3PAR. 
-The installer should read the HPE Synergy Image Streamer 4.0 Artifact Bundle for Red Hat Enterpise Linux 7.5.docx located in the Docs folder. 

________________________________________
## Custom Attributes ##
________________________________________

**NewRootPassword**  password

The root account of the deployed server will be configured with the password specified with this custom attribute.

**ServerFQDN**	FQDN	

The provisioned server will be configured with the FQDN you specify with this custom attribute.
	
**SSH**	Option	Enabled

Specify "Enabled" if you want to enable the SSH daemon on the provisioned server. Set to “Disabled” if you do not wish to access the host via SSH.
	
________________________________________
## How to use ##
________________________________________
Option 1: Import artifact bundles found in this repo.

Step1 : Import the artifact bundles into HPE Image streamer and extract them.
Step2 : Create a new deployment plan and attach the deploy build plan. 
Step3 : Adjust the custom attributes (see above) so that they match your environment. It is recommended to make invisible those attributes which correspond to default values that never change in your environment.
Step4 : Add golden images to the deployment plan.
Step5 : For testing purposes, Create the Server Profile in HPE Synergy Composer using the deployment plan and provide attributes for the required values.
 
Option 2: Leverage plan scripts and customize them to match your needs.
________________________________________
## Summary ##
________________________________________
These plan scripts have been tested for personalizing Red Hat Enterprise Linux 7.5.
