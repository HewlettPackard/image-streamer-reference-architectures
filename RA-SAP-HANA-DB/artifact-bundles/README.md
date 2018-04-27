# Artifact Bundle Contents for ImageStreamer v3.1 release
**Version History:**

HPE-SLES12-SAP-HANA-DB-RA-2018-03-06-v3.1.zip - Changed default value for attribute DepotHost 
												in Deployment plan
HPE-SLES12-SAP-HANA-DB-RA-2017-10-20-v3.1.zip - First version

**Deployment Plans:**

           Name: HPE - SLES12 - SAP HANA DB - deploy
    Description: Deploy SAP HANA into a SLES12 golden image.


**OS Build Plans:**

           Name: HPE - SLES12 - SAP HANA DB - deploy
    Description: Install SAP HANA into a SLES12 golden image.

           Name: HPE - SLES12 - SAP HANA DB - generalize
    Description: Removes personalization settings from SLES12.


**Plan Scripts:**

           Name: HPE - SLES12 - SAP HANA DB - mount and validate
           Type: General
    Description: Mounts the root partition and validates the golden image.

           Name: HPE - SLES12 - SAP HANA DB - configure multiple NICs
           Type: Deploy
    Description: Configures the network.

           Name: HPE - SLES12 - SAP HANA DB - change root password
           Type: Deploy
    Description: Sets the root user password.

           Name: HPE - SLES12 - SAP HANA DB - configure hostname
           Type: Deploy
    Description: Updates the hostname and configures the gateway.

           Name: HPE - SLES12 - SAP HANA DB - manage security services
           Type: Deploy
    Description: Deactivates the firewall and set ssh settings.

           Name: HPE - SLES12 - SAP HANA DB - partition SAN disk using LVM
           Type: Deploy
    Description: Partitions the attached SAN storage using LVM.

           Name: HPE - SLES12 - SAP HANA DB - update OS settings
           Type: Deploy
    Description: Customize kernel parameters and block devices for SAP HANA.

           Name: HPE - SLES12 - SAP HANA DB - create local input file
           Type: Deploy
    Description: Creates the input file required for the SAP HANA installation.

           Name: HPE - SLES12 - SAP HANA DB - create install script
           Type: Deploy
    Description: Copies the installation script install_SAP.sh for installing SAP HANA to the OS. The script 
                 will mount the software depot, create the SAP HANA config file, and start the installation. 
                 The script will be executed after the first boot of the OS.

           Name: HPE - SLES12 - SAP HANA DB – unmount
           Type: General
    Description: Unmounts the root partition.



           Name: HPE - SLES12 - SAP HANA DB - mount generalize
           Type: Capture
    Description: Mount root partition for generalization.

           Name: HPE - SLES12 - SAP HANA DB - generalize host
           Type: Capture
    Description: Remove host specific configuration.

           Name: HPE - SLES12 - SAP HANA DB - generalize network
           Type: Capture
    Description: Remove network settings.

           Name: HPE - SLES12 - SAP HANA DB - unmount generalize
           Type: Capture
    Description: Unmounts root partition after generalization.
