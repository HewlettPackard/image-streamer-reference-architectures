# Artifact Bundle Contents for ImageStreamer v4.0 release

## Note:
- All artifact bundles in this repository are compatible with HPE Image Streamer v4.0 release
- The documentation how to prepare the systems and use the artifact bundles is in the [docs](../docs/) folder.

## Version History:
- **[HPE-RHEL7.x-SAP-HANA-DB-RA-2018-06-01-v4.0.zip](HPE-RHEL7.x-SAP-HANA-DB-RA-2018-06-01-v4.0.zip)**
  - For usage on Red Hat Enterprise Linux for SAP Applications 7.x
  - Lifecycle activities (Install SAP HANA, update Operating System & SAP HANA DB, switch workloads)
- **[HPE-SLES12-SAP-HANA-DB-RA-2018-06-01-v4.0.zip](HPE-SLES12-SAP-HANA-DB-RA-2018-06-01-v4.0.zip)**
  - For usage on SUSE Linux Enterprise Server for SAP Applications 12
  - Lifecycle activities (Install SAP HANA, update Operating System & SAP HANA DB, switch workloads)
- **[HPE-SLES12-SAP-HANA-DB-RA-2018-03-06-v3.1.zip](HPE-SLES12-SAP-HANA-DB-RA-2018-03-06-v3.1.zip)**
  - Changed default value for attribute DepotHost in deployment plan to fulfill ImageStreamer 4.0 requirements
- **[HPE-SLES12-SAP-HANA-DB-RA-2017-10-20-v3.1.zip](HPE-SLES12-SAP-HANA-DB-RA-2017-10-20-v3.1.zip)**
  - First version

## Latest Artifact Bundle Contents:

**Artifact Bundles:**

      File name: HPE-RHEL7.x-SAP-HANA-DB-RA-2018-06-01-v4.0.zip
           Name: HPE-RHEL7.x-SAP-HANA-DB-RA-2018-06-01
    Description: Artifacts for image capturing and SAP HANA deployment on RHEL7.x.

      File name: HPE-SLES12-SAP-HANA-DB-RA-2018-06-01-v4.0.zip
           Name: HPE-SLES12-SAP-HANA-DB-RA-2018-06-01
    Description: Artifacts for image capturing and SAP HANA deployment on SLES12.


**Deployment Plans:**

           Name: HPE - RHEL7.x - SAP HANA DB - deploy
    Description: Deploy SAP HANA into a RHEL7.x golden image.

           Name: HPE - SLES12 - SAP HANA DB - deploy
    Description: Deploy SAP HANA into a SLES12 golden image.


**OS Build Plans:**

           Name: HPE - RHEL7.x - SAP HANA DB - deploy
    Description: Install and maintain SAP HANA on a RHEL7.x golden image.

           Name: HPE - RHEL7.x - SAP HANA DB - generalize
    Description: Removes personalization settings from RHEL7.x.

           Name: HPE - SLES12 - SAP HANA DB - deploy
    Description: Install and maintain SAP HANA on a SLES12 golden image. 

           Name: HPE - SLES12 - SAP HANA DB - generalize
    Description: Removes personalization settings from SLES12.


**Plan Scripts for personalization:**

           Name: HPE - RHEL7.x - SAP HANA DB - mount and validate
                 HPE - SLES12 - SAP HANA DB - mount and validate
           Type: General
    Description: Mounts the root partition and validates the golden image.

           Name: HPE - Linux - SAP HANA DB - configure multiple NICs
           Type: Deploy
    Description: Configures the network and sets gateway.

           Name: HPE - Linux - SAP HANA DB - change root password
           Type: Deploy
    Description: Sets the root user password.

           Name: HPE - Linux - SAP HANA DB - configure hostname
           Type: Deploy
    Description: Updates the hostname.

           Name: HPE - Linux - SAP HANA DB - manage security services
           Type: Deploy
    Description: Enables or disables security services.

           Name: HPE - Linux - SAP HANA DB - partition SAN disk using LVM
           Type: Deploy
    Description: Partitions the attached SAN storage using LVM.

           Name: HPE - RHEL7.x - SAP HANA DB - update OS settings
                 HPE - SLES12 - SAP HANA DB - update OS settings
           Type: Deploy
    Description: Customize kernel parameters for SAP HANA.

           Name: HPE - Linux - SAP HANA DB - create local input file
           Type: Deploy
    Description: Creates the input file required for the SAP HANA installation.

           Name: HPE - Linux - SAP HANA DB - create install script
           Type: Deploy
    Description: Creates the installation script install_SAP.sh. 
                 The script will mount the software depot, create the SAP HANA config file, start the 
                 installation or database update and create backup services for SAP HANA specific OS 
                 settings. The script will be executed after the first boot of the OS.

           Name: HPE - RHEL7.x - SAP HANA DB – unmount
                 HPE - SLES12 - SAP HANA DB – unmount
           Type: General
    Description: Cleans up the temporary directory created during mount and unmounts the root partition.


**Plan Scripts for generalization:**

           Name: HPE - RHEL7.x - SAP HANA DB - mount generalize
                 HPE - SLES12 - SAP HANA DB - mount generalize
           Type: Capture
    Description: Mount root partition for generalization.

           Name: HPE - Linux - SAP HANA DB - generalize host
           Type: Capture
    Description: Remove host specific configuration.

           Name: HPE - RHEL7.x - SAP HANA DB - generalize network
                 HPE - SLES12 - SAP HANA DB - generalize network
           Type: Capture
    Description: Remove network settings.

           Name: HPE - Linux - SAP HANA DB - unmount generalize
           Type: Capture
    Description: Unmount root partition after generalization.
