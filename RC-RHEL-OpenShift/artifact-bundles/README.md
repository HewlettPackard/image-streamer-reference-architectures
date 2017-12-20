--------------------------------------------------------------------------------

	            File name: HPE-RHEL-7.4-OpenShift-2017-11-27-v3.1.zip
		Name (in manifest): HPE-RHEL-7.4-OpenShift-2017-11-27-v3.1
		       Description: Deploy infrastructure for Red Hat OpenShift Container Platform
		             Dated: 2017-12-12 (05:47:37)

--------------------------------------------------------------------------------

Deployment Plans:

	        Name: HPE-RHEL7.4-OpenShiftWorker (Type:OEDeploymentPlan)
	 Description: Deployment plan for Red Hat OpenShift Container Platform: Master node


	        Name: HPE-Create Empty volume (Type:OEDeploymentPlan)
	 Description: Create a volume up to 50GB


	        Name: HPE-RHEL7.4-OCP-Infra (Type:OEDeploymentPlan)
	 Description: Deployment plan for Red Hat OpenShift Container Platform:  Infrastructure node


	        Name: HPE-RHEL7.4-OpenShiftLBNFS (Type:OEDeploymentPlan)
	 Description: Deploy Load Balancer / NFS node for OpenShift


	        Name: HPE-RHEL7.4-OpenShiftMaster (Type:OEDeploymentPlan)
	 Description: Deployment plan for Red Hat OpenShift Container Platform: Master node


	        Name: HPE-RHEL7.4-OpenShiftCNS (Type:OEDeploymentPlan)
	 Description: Deployment plan for Red Hat OpenShift Container Platform: Container-native storage node



Build Plans:

	       Name: HPE - Foundation 2.0 - create larger volume (Type:deploy)
	Description: Create empty OS Volume version 1.00 
	             Create an empty OS Volume to be the target for OS install.


	       Name: RHEL74-OpenShift-LB-NFS-11-9-2017 (Type:deploy)
	Description: Deploy the OpenShift load balancer / NFS server


	       Name: RHEL74-OpenShift-11-09-2017 (Type:deploy)
	Description: Deploy OpenShift ready server


	       Name: RHEL-7.4-generalize-2017-08-18 (Type:capture)
	Description: Remove personalization settings from RHEL 7.4.



Plan Scripts:

	       Name: 055-RHEL-7.4-register-DNSandSatellite (deploy)
	   FullName: 002a6ba3-f061-459d-99e8-9770c1a64317_planscript.json
	Description: Register the deployed host in DNS and with Red Hat Satellite


	       Name: 000-RHEL7.4-mount-and-validate (general)
	   FullName: 0375b858-b97b-4396-afaa-a8170055dd2e_planscript.json
	Description: mount RHEL partition and validate its contents


	       Name: HPE - Foundation 1.0 - create empty OS Volume (deploy)
	   FullName: 100b5377-cff8-48c1-ba32-d7839b3b9ae8_planscript.json
	Description: Create empty OS Volume - version 1.00
	             Create an empty OS Volume to be the target for OS install.


	       Name: RHEL-7.4-unmount-generalize (capture)
	   FullName: 11cb2377-6102-4fde-968c-31c08403c8ef_planscript.json
	Description: unmount RHEL partition after generalization


	       Name: RHEL-7.4-generalize-users (capture)
	   FullName: 1521ce38-4202-4db9-9ec4-b164a36e68f1_planscript.json
	Description: remove user settings


	       Name: 030-RHEL7.4-configure-network (deploy)
	   FullName: 25a2f4b2-d867-496e-a33b-c697c3668a53_planscript.json
	Description: configure NIC teaming


	       Name: RHEL-7.4-generalize-network (capture)
	   FullName: 2e1beaae-c522-4be2-bec4-575bdf5def86_planscript.json
	Description: remove network configuration


	       Name: 010-RHEL-7.4-set-iscsi-initiatorname (deploy)
	   FullName: 55762abc-433d-44cc-bea6-fdc94bfe0f5d_planscript.json
	Description: 010-RHEL-7.4-set-iscsi-initiatorname
	             
	             Check if this is still needed for OneView 3.1?


	       Name: 050-RHEL-7.4-configure-hostname (deploy)
	   FullName: 607213a0-7b48-490f-b222-e15868acfcf0_planscript.json
	Description: Configure the hostname for RHEL7.4


	       Name: 070-RHEL-7.4-enable-ansible-ssh (deploy)
	   FullName: 78e9c558-022f-40af-b2c9-cd249a63876d_planscript.json
	Description: Import the ansible ssh key to allow playbooks to run without requiring password


	       Name: 040-RHEL-7.4-configure-NTP (deploy)
	   FullName: 84c06390-2613-4caf-bdaf-d6d0babd319f_planscript.json
	Description: 040-RHEL-7.4-configure-ntp


	       Name: 085-RHEL-7.4-erase-all-datadrives (deploy)
	   FullName: a60bf327-1d5f-43f8-bda6-2cccd844af43_planscript.json
	Description: Erase all the drives so they can be used for docker volumes and container-native storage.


	       Name: 090-RHEL-7.4-configure-docker (deploy)
	   FullName: c445132e-55c5-4129-b261-0c19df90824e_planscript.json
	Description: configure the docker_storage_setup file and then run the openshift script to configure the volume and then start docker service


	       Name: RHEL-7.4-generalize-host (capture)
	   FullName: c48383f2-029d-4d0c-b1bc-94bdf25b257a_planscript.json
	Description: remove host configuration


	       Name: 999-RHEL7.4-unmount (deploy)
	   FullName: cd06ca58-3ee3-467c-9605-7e518a38548d_planscript.json
	Description: 999-RHEL-7.4-unmount


	       Name: 100-RHEL-7.4-manage-security-services (deploy)
	   FullName: f2dc2031-2f7d-4e9e-842c-e2071ab6ad43_planscript.json
	Description: 100-RHEL-7.4-manage-security-services


	       Name: RHEL-7.4-mount-generalize (capture)
	   FullName: f3c816dc-0f7a-48ba-a336-dd0c8ae9b6d8_planscript.json
	Description: mount RHEL partition for generalization


	       Name: 020-RHEL-7.4-change-root-password (deploy)
	   FullName: f79ebcb2-d7ce-4dc5-9713-0cc504e3d523_planscript.json
	Description: 020-RHEL-7.3-change-root-password



