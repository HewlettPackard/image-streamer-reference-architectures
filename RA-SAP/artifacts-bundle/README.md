# Artifact Bundle Contents for ImageStreamer v4.1 release

## Note:
- All artifact bundles in this repository are compatible with HPE Image Streamer v4.1 release
- The documentation how to prepare the systems and use the artifact bundles is in the [docs](../docs/) folder.

## Version History:
- **[HPE-RHEL7.x-SAP-RA-2019-04-12-v4.1.zip](HPE-RHEL7.x-SAP-RA-2019-04-12-v4.1.zip)**
  - For usage on Red Hat Enterprise Linux for SAP Applications 7.x
  - Installation Options (Install SAP HANA only, install SAP Application like SAP S/4HANA)
  - Lifecycle activities (update Operating System, update SAP HANA DB, switch workloads)
  - Storage options: HPE 3PAR StoreServ or HPE Synergy D3940 Storage Module
- **[HPE-SLES12-SAP-RA-2019-04-12-v4.1.zip](HPE-SLES12-SAP-RA-2019-04-12-v4.1.zip)**
  - For usage on SUSE Linux Enterprise Server for SAP Applications 12
  - Installation Options (Install SAP HANA only, install SAP Application like SAP S/4HANA)
  - Lifecycle activities (update Operating System, update SAP HANA DB, switch workloads)
  - Storage options: HPE 3PAR StoreServ or HPE Synergy D3940 Storage Module


## Latest Artifact Bundle Contents:

**Artifact Bundles:**

      File name: HPE-RHEL7.x-SAP-RA-2019-04-12-v4.1.zip
           Name: HPE-RHEL7.x-SAP-RA-2019-04-12
    Description: Artifacts for image capturing and SAP deployment on RHEL7.x.

      File name: HPE-SLES12-SAP-RA-2019-04-12-v4.1.zip
           Name: HPE-SLES12-SAP-RA-2019-04-12
    Description: Artifacts for image capturing and SAP deployment on SLES12.


**Deployment Plans:**

           Name: HPE - RHEL7.x - SAP HANA - deploy
    Description: Deploy SAP HANA database into a RHEL7.x golden image.

           Name: HPE - RHEL7.x - SAP S4HANA - deploy
    Description: Deploy SAP S/4HANA into a RHEL7.x golden image.

           Name: HPE - SLES12 - SAP HANA - deploy
    Description: Deploy SAP HANA database into a SLES12 golden image.

           Name: HPE - SLES12 - SAP S4HANA - deploy
    Description: Deploy SAP S/4HANA into a SLES12 golden image.


**OS Build Plans:**

           Name: HPE - RHEL7.x - SAP - deploy
    Description: Install and maintain SAP on a RHEL7.x golden image.

           Name: HPE - RHEL7.x - SAP - generalize
    Description: Removes personalization settings from RHEL7.x.

           Name: HPE - SLES12 - SAP - deploy
    Description: Install and maintain SAP on a SLES12 golden image. 

           Name: HPE - SLES12 - SAP - generalize
    Description: Removes personalization settings from SLES12.


**Plan Scripts for personalization:**

           Name: HPE - RHEL7.x - SAP - mount and validate
                 HPE - SLES12 - SAP - mount and validate
           Type: General
    Description: Mounts the root partition and validates the golden image.

           Name: HPE - Linux - SAP - configure multiple NICs
           Type: Deploy
    Description: Configures the network and sets gateway.

           Name: HPE - Linux - SAP - change root password
           Type: Deploy
    Description: Sets the root user password.

           Name: HPE - Linux - SAP - configure hostname
           Type: Deploy
    Description: Updates the hostname.

           Name: HPE - Linux - SAP - manage security services
           Type: Deploy
    Description: Enables or disables security services.

           Name: HPE - Linux - SAP - partition disk using LVM
           Type: Deploy
    Description: Partitions the attached storage using LVM.

           Name: HPE - Linux - SAP - create local input file
           Type: Deploy
    Description: Creates the input file required for the SAP installation.

           Name: HPE - Linux - SAP - create install script
           Type: Deploy
    Description: The script will configure SAP specific OS settings, using 'saptune' for SLES12 or 'tuned' for RHEL7.x,
                 mount the software depot, create the SAP HANA config file and/or SAP application inifile, 
                 detect if SAP HANA and/or a SAP application shall be installed, start the 
                 installation or database update and create backup services for SAP specific OS 
                 settings. The script will be executed after the first boot of the OS.

           Name: HPE - RHEL7.x - SAP DB – unmount
                 HPE - SLES12 - SAP DB – unmount
           Type: General
    Description: Cleans up the temporary directory created during mount and unmounts the root partition.


**Plan Scripts for generalization:**

           Name: HPE - RHEL7.x - SAP - mount generalize
                 HPE - SLES12 - SAP - mount generalize
           Type: Capture
    Description: Mount root partition for generalization.

           Name: HPE - Linux - SAP - generalize host
           Type: Capture
    Description: Remove host specific configuration.

           Name: HPE - RHEL7.x - SAP - generalize network
                 HPE - SLES12 - SAP - generalize network
           Type: Capture
    Description: Remove network settings.

           Name: HPE - Linux - SAP - unmount generalize
           Type: Capture
    Description: Unmount root partition after generalization.
