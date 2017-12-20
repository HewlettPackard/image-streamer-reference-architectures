## Artifact Bundle Contents:

--------------------------------------------------------------------------------

	            File name: HPE-SLES12-SAP-HANA-DB-RA-2017-10-20-v3.1.zip
		Name (in manifest): HPE-SLES12-SAP-HANA-DB-RA-2017-10-20-v3.1
		       Description: Artifacts for image capturing and SAP HANA deployment on SLES12. 
		             Dated: 2017-11-24 (13:19:45)

--------------------------------------------------------------------------------

Deployment Plans:

	        Name: HPE - SLES12 - SAP HANA DB - deploy - 2017-10-20 (Type:OEDeploymentPlan)
	 Description: Deploy SAP HANA into a SLES12 golden image.


Build Plans:

	       Name: HPE - SLES12 - SAP HANA DB - generalize - 2017-10-20 (Type:capture)
	Description: Removes personalization settings from SLES12.

	       Name: HPE - SLES12 - SAP HANA DB - deploy - 2017-10-20 (Type:deploy)
	Description: Install SAP HANA into a SLES 12 golden image.

Plan Scripts:

	       Name: HPE - SLES12 - SAP HANA DB - mount and validate - 2017-10-20 (general)
	   FullName: 04b7a703-92aa-4f84-b337-b5aecf597046_planscript.json
	Description: Mounts the root partition and validates the golden image.


	       Name: HPE - SLES12 - SAP HANA DB - configure multiple NICs - 2017-10-20 (deploy)
	   FullName: 0c5faa56-2e51-454d-b4ca-2006dec3f561_planscript.json
	Description: Configures the network.


	       Name: HPE - SLES12 - SAP HANA DB - mount generalize - 2017-10-20 (capture)
	   FullName: 3940f4df-65cd-46ec-8eee-abe4ecc619fc_planscript.json
	Description: Mount root partition for generalization.


	       Name: HPE - SLES12 - SAP HANA DB - create local input file - 2017-10-20 (deploy)
	   FullName: 74475518-a779-4584-bc86-68846fb87deb_planscript.json
	Description: Creates the input file required for the SAP HANA installation.


	       Name: HPE - SLES12 - SAP HANA DB - create install script - 2017-10-20 (deploy)
	   FullName: 8524d4f8-1728-4b43-a538-58948d14a27e_planscript.json
	Description: Copies the installation script install_SAP.sh for installing SAP HANA to the OS. The script will mount the software depot, create the SAP HANA config file, and start the installation. The script will be executed after the first boot of the OS.


	       Name: HPE - SLES12 - SAP HANA DB - manage security services - 2017-10-20 (deploy)
	   FullName: 9250c1e9-db45-45af-828b-a2147c4479c7_planscript.json
	Description: Deactivates the firewall and set ssh settings.


	       Name: HPE - SLES12 - SAP HANA DB - generalize host - 2017-10-20 (capture)
	   FullName: 96753b8d-600e-42b5-b5b9-150cfa5aa044_planscript.json
	Description: Remove host specific configuration.


	       Name: HPE - SLES12 - SAP HANA DB - partition SAN disk using LVM - 2017-10-20 (deploy)
	   FullName: 9ae2166b-e62b-42eb-ac46-b8682fda77a5_planscript.json
	Description: Partitions the attached SAN storage using LVM.


	       Name: HPE - SLES12 - SAP HANA DB - unmount generalize - 2017-10-20 (capture)
	   FullName: 9d25b407-ff63-48f9-83e3-77761f82272c_planscript.json
	Description: unmount volume after generalization


	       Name: HPE - SLES12 - SAP HANA DB - generalize network - 2017-10-20 (capture)
	   FullName: aae9e67b-a92d-467b-8562-ed0d82d10fee_planscript.json
	Description: Remove network settings.


	       Name: HPE - SLES12 - SAP HANA DB - unmount - 2017-10-20 (general)
	   FullName: b17cdf9b-f52c-4b5b-b023-813afcef28d5_planscript.json
	Description: Unmounts the root partition.


	       Name: HPE - SLES12 - SAP HANA DB - change root password - 2017-10-20 (deploy)
	   FullName: cc36732e-ad58-4d19-b103-6941f90e8384_planscript.json
	Description: Sets the root user password.


	       Name: HPE - SLES12 - SAP HANA DB - configure hostname - 2017-10-20 (deploy)
	   FullName: e05b96bb-266a-4ad5-a7db-0a9fb5094d6a_planscript.json
	Description: Updates the hostname and configures the gateway.


	       Name: HPE - SLES12 - SAP HANA DB - update OS settings - 2017-10-20 (deploy)
	   FullName: f0f032ff-ab95-4d97-8078-6afdcaf089ec_planscript.json
	Description: Customize kernel parameters and block devices for SAP HANA.




