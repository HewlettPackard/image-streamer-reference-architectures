# HPE Reference Architecture for SAP HANA lifecycle activity with HPE Synergy Image Streamer

## About

This repository contains HPE Image Streamer plan scripts and artifact bundles to personalize and deploy 
*Red Hat Enterprise Linux for SAP Applications 7.x* or *SUSE Linux Enterprise Server for SAP Applications 12* 
golden images and install SAP HANA on HPE Synergy compute modules. 

After the deployment, lifecycle activities like updating the operating system, the SAP HANA version or revision 
and switching workload to another compute module can be executed in a standardized way for one or several servers.

**Contents of the repository are:**
	
- [artifact-bundles](artifact-bundles/): Contains artifact bundles in zip format which can be imported into HPE Synergy Image Streamer.
- [docs](docs/): Documentation how to prepare the systems and use the artifact bundles.

## Pre-requisites

- HPE Synergy platform
- HPE Synergy Composer configured with OS deployment server 'HPE Synergy Image Streamer'
- HPE 3PAR StoreServ as SAN storage
- Operating Systems
  - Red Hat Enterprise Linux for SAP Applications 7.x or
  - SUSE Linux Enterprise Server for SAP Applications 12
- Access to SAP support webpages
- Access to SAP software downloads

## Custom Attributes

When you create a server profile in the Synergy Composer GUI, you can attach the deployment plan shipped 
in the artifact bundle found in this repository. This example deployment plan only exposes a subset of the 
parameters (known as "custom attributes") supported by the underlying OS build plan. It is your decision to 
make a custom attribute visible or not in the deployment plan. Keep in mind that the less input is required 
for a deployment, the better the user experience.


    DepotCifsPassword
        Password for the CIFS software share. For NFS, either delete this attribute in plan script
        "HPE - RHEL7.x – SAP HANA DB - create local input file" or 
        "HPE - SLES12 – SAP HANA DB - create local input file" or enter a dummy value.

    DepotCifsUsername
        Username for the CIFS software share. For NFS, either delete this attribute in plan script 
        "HPE - RHEL7.x – SAP HANA DB - create local input file" or 
        "HPE - SLES12 – SAP HANA DB - create local input file" or enter a dummy value.

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
        Domain name of the host.

    HanaInstanceNumber
        The two-digit SAP HANA database Instance Number. Rules for SAP Instance Number apply.

    HanaMasterPassword
        The master password of the SAP HANA database that will be used for all SAP HANA users.

    HanaSID
        The SAP System Identification of the SAP HANA database host. Rules for SAP System ID definition apply.

    HanaStartAfterReboot
        Sets the autostart option for HANA after a system reboot. Possible values are Yes and No.

    HanaUpdate
        Defines if the SAP HANA database shall be updated. Possible values are true and false.

    HostName
        The hostname of the system.

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
        Defines if SSH will be enabled on the deployed OS. Possible values are Enabled or Disabled


## How to use

### 1. Import artifact bundle found in this repository

1. Import the artifact bundle into Image Streamer and extract.
2. Create a new deployment plan by copying a supplied deployment plan.
3. Adjust the custom attributes (see above) so that they match your environment. It is recommended to make those attributes invisible which correspond to static values in your environment.
4. Create a golden image and add it to the deployment plan.
5. Create a server profile template in OneView using the deployment plan and provide values for required attributes.
6. Create a server profile using the server profile template.

### 2. Leverage plan scripts and customize them as per user need

Following are the plan scripts. Depending on the use case, modify the appropriate plan scripts.

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


## Operating Systems

These plan scripts have been tested with the following Operating Systems:

- Red Hat Enterprise Linux for SAP Applications 7.4
- SUSE Linux Enterprise Server for SAP Applications 12 SP2
- SUSE Linux Enterprise Server for SAP Applications 12 SP3
