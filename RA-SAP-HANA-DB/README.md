# HPE Reference Architecture for deploying SAP HANA with HPE Synergy Image Streamer

---------------------------------------------			
About
---------------------------------------------
This repo contains HPE Image Streamer plan scripts and artifact bundles to personalize and deploy 
the SLES12 Operating System and install SAP HANA database on HPE Synergy compute modules.

Contents of the repo are:
	
    artifact-bundles : Contains artifact bundles in zip format. User can import these into Image Streamer.
    plan-scripts     : List of scripts to personalize the OS and SAP HANA database are shown below.

---------------------------------------------			
Pre-requisites
---------------------------------------------
    - Access to Synergy platform
    - Synergy composer configured with OS Deployment server 'Image Streamer'
    - Access to SLES for SAP Applications 12 (instruction to build this image is part of the documentation)
    - Access to SAP support webpages
    - Access to SAP software downloads

-------------------------------------------
Custom Attributes
--------------------------------------------
    When you create a server profile in the Synergy Composer GUI, you can attach the deployment plan shipped 
    in the artifact bundle found in this repo. This example deployment plan only exposes a subset of the parameters 
    (known as "custom attributes") supported by the underlying OS build plan. It is your decision to make a custom 
    attribute visible or not in the deployment plan. Keep in mind that the less input is required for a deployment, 
    the better the user experience.
    
    DepotCifsPassword
        Password for the CIFS software share. For NFS, either delete this attribute in plan script
        "HPE - SLES12 – SAP HANA DB - create local input file" or enter a dummy value.
    
    DepotCifsUsername
        Username for the CIFS software share. For NFS, either delete this attribute in plan script 
        "HPE - SLES12 – SAP HANA DB - create local input" file or enter a dummy value.
    
    DepotHost
        IP-Address of the software share.
    
    DepotLocalMountpoint
        Local mountpoint on the deployed host for the software share. 
        The directory will be created during deployment.
    
    DepotMountType
        Network protocol for the software share. Either CIFS or NFS is supported.
    
    DepotSapDirectory
        Directory on the software share that contains the SAP HANA installation media.
    
    DepotShareName
        Name of the software share.
    
    DomainName
        Full hostname (FQDN) for the deployed OS.
    
    HanaInstanceNumber
        The two-digit SAP HANA database Instance Number. Rules for SAP Instance Number apply.
    
    HanaMasterPassword
        The master password of the SAP HANA database that will be used for all SAP HANA users.
    
    HanaSID
        The SAP System Identification of the SAP HANA database host. Rules for SAP System ID definition apply.
    
    HanaStartAfterReboot
        Sets the autostart option for HANA after a system reboot. Possible values are Yes and No.
    
    InstallDirectory
        Local installation directory for the SAP HANA database. The installation script, local input file and all 
        installation logfiles will be stored here.
    
    LvmVolumeGroupName
        Name of the LVM volume group for the SAP HANA database installation.
    
    LvmVolumeNameHana
        Name of the LVM partition used for /hana directory.
    
    LvmVolumeNameSap
        Name of the LVM partition used for /usr/sap directory.
    
    LvmVolumeNameSwap
        Name of the LVM partition used for swap space.
    
    LvmVolumeSizeHana
        Size of the LVM partition required for /hana in GiB.
    
    LvmVolumeSizeSap
        Size of the LVM partition required for /usr/sap in GiB.
    
    LvmVolumeSizeSwap
        Size of the LVM partition required for swap space in GiB.
    
    ManagementNIC1
        NIC1 on the management network.
    
    ManagementNIC2
        NIC2 on the management network.
    
    NewRootPassword
        New password for the root user.
    
    SSH
        Defines if SSH shall be enabled on the deployed OS. Possible values are Enabled or Disabled.

---------------------------------------------			
How to use
---------------------------------------------
**Option 1: Import artifact bundle found in this repository**

    1. Import the artifact bundle into Image Streamer and extract.
    2. Create a new deployment plan by coping the supplied deployment plan 
       (named HPE-SLES12-SAP-HANA-DB-RA-yyyy-mm-dd).
    3. Adjust the custom attributes (see above) so that they match your environment. It is recommended to 
       make those attributes invisible which correspond to static values in your environment.
    4. Create a golden image and add it to the deployment plan.
    5. Create a server profile template in OneView using the deployment plan and provide values for 
       required attributes.
    6. Create a server profile using the server profile template.

**Option 2: Leverage plan scripts and customize them as per user need.**


Following are the plan scripts. Depending on the use case, modify the appropriate plan scripts.

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

-----------------------------------------------
Summary
-----------------------------------------------
These plan scripts have been tested for personalizing

    SLES for SAP Applications 12 SP2
