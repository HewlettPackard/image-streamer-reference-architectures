# HPE Reference Architecture for SAP Application and SAP HANA lifecycle activity with HPE Synergy Image Streamer

## About

This repository contains HPE Image Streamer plan scripts and artifact bundles to personalize and deploy 
*Red Hat Enterprise Linux for SAP Applications 7.x* or *SUSE Linux Enterprise Server for SAP Applications 12* 
golden images and install SAP HANA and/or SAP application like SAP S/4HANA on HPE Synergy compute modules. 

After the deployment, lifecycle activities like updating the operating system, the SAP HANA version or revision 
and switching workload to another compute module can be executed in a standardized way for one or several servers.

**Contents of the repository are:**
	
- [artifact-bundles](artifact-bundles/): Contains artifact bundles in zip format which can be imported into HPE Synergy Image Streamer.
- [docs](docs/): Documentation how to prepare the systems and use the artifact bundles.

## Pre-requisites

- HPE Synergy platform
- HPE Synergy Composer configured with OS deployment server 'HPE Synergy Image Streamer'
- Storage 
  - HPE 3PAR StoreServ or
  - HPE Synergy D3940 Storage Module
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
        "HPE - RHEL7.x - SAP - create local input file" or 
        "HPE - SLES12 - SAP - create local input file" or enter a dummy value.

    DepotCifsUsername
        Username for the CIFS software share. For NFS, either delete this attribute in plan script 
        "HPE - RHEL7.x – SAP - create local input file" or 
        "HPE - SLES12 – SAP - create local input file" or enter a dummy value.

    DepotHost
        IP-Address of the software share.

    DepotLocalMountpoint
        Local mountpoint on the deployed host for the software share. 
        The directory will be created during deployment.

    DepotMountType
        Network protocol for the software share. Either 'CIFS' or 'NFS' is supported.

    DepotSapDirectory
        Directory on the software share that contains the SAP installation media.

    DepotShareName
        Name of the software share.

    HanaHostName
       FQDN hostname of the SAP HANA server.

    HanaInstanceNumber
        The two-digit SAP HANA database Instance Number. Rules for SAP Instance Number apply.

    HanaMasterPassword
        The master password of the SAP HANA database that will be used for all SAP HANA users.

    HanaSID
        The SAP System Identification of the SAP HANA database host. Rules for SAP System ID definition apply.

    HanaUpdate
        Defines if the SAP HANA database shall be updated. Possible values are 'True' and 'False'.

    HostFunction
        Defines which SAP function shall be installed.
        Possible values:
        'standard' for SAP Primary Application Server
        'db' for SAP HANA only installation
        'aas' for additional SAP Application Server

    InstallDirectory
        Local directory for the SAP installation. The installation script, local input file and all 
        installation logfiles will be stored here.

    LvmVolumeGroupName
        Name of the LVM volume group for the SAP installation.

    LvmVolumeNameHana
        Name of the LVM partition used for /hana directory.
        In case of SAP application only installation, the volume will not be created.

    LvmVolumeNameSap
        Name of the LVM partition used for /usr/sap directory.

    LvmVolumeNameSapmnt
        Name of the LVM partition used for /sapmnt directory.
        In case of SAP HANA only installation, the volume will not be created.

    LvmVolumeNameSwap
        Name of the LVM partition used for swap space.

    LvmVolumeSizeHana
        Size of the LVM partition required for /hana in GiB.
        In case of SAP application only installation, the volume will not be created.

    LvmVolumeSizeSap
        Size of the LVM partition required for /usr/sap in GiB.

    LvmVolumeSapmnt
        Size of the LVM partition required for /sapmnt in GiB.
        In case of HANA only installation, the volume will not be created.

    LvmVolumeSizeSwap
        Size of the LVM partition required for swap space in GiB.

    NewRootPassword
        New password for the root user.

    NIC1
        NIC1 on the management network.

    NIC2
        NIC2 on the management network.

    NIC3
        NIC3 on the management network for external connection, e.g. to an HPE Superdome Flex server with SAP HANA.

    NIC4
        NIC3 on the management network for external connection, e.g. to an HPE Superdome Flex server with SAP HANA.

    SapGlobalHost
        FQDN hostname of the SAP global host.
        In case of HANA DB only installation, the attribute value can be set to 'none'.

    SapHostName
        FQDN hostname for the SAP Application Server.
        In case of HANA DB only installation, the attribute value can be set to 'none'.

    SapInstanceNumber
        The two-digit SAP Instance Number. 
        In case of HANA DB only installation, the attribute value can be set to any value.

    SapMasterPassword
        Master Password for the SAP Application.
        In case of HANA DB only installation, the attribute value can be set to any value.

    SapSID
        The SAP System Identification of the SAP Application.
        In case of HANA DB only installation, the attribute value can be set to any value.

    SapStack
        Defines if the ABAP or JAVA Stack of a release shall be installed.
        Possible values are 'ABAP' or 'JAVA'.

    SapTestRun
        Defines if the SAP installation shall be started in a test run.
        Possible Values:
        'false' Complete installation is executed.
        'host_preparation' host is prepared, but SAP installer not started.
        'sap_summary' SAP installer is stopped after the summary phase.

    SapVersion
        Defines which SAP Version shall be installed.
        Possible Values are 'S4HANA1809' or 'BW4HANA10SR1'. 

    SSH
        Defines if SSH will be enabled on the deployed OS. Possible values are 'Enabled' or 'Disabled'.

    StartInstanceAfterReboot
        Sets the autostart option for SAP Instances after a system reboot.
        Possible values are 'yes' and 'no'.

    Storage
        Defines which storage to use. Possible values are 'HPE 3PAR StoreServ' or 'HPE Synergy D3940'.

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
    Description: Creates the input file required for the SAP HANA and SAP application installation.

           Name: HPE - Linux - SAP - create install script
           Type: Deploy
    Description: Creates the installation script install_SAP.sh. 
                 The script will configure SAP specific OS settings, using 'saptune' for SLES12 or 'tuned' for RHEL7.x,
                 mount the software depot, create the SAP HANA config file and/or SAP application inifile, 
                 detect if SAP HANA and/or a SAP application shall be installed, start the 
                 installation or database update and create backup services for SAP specific OS 
                 settings. The script will be executed after the first boot of the OS.

           Name: HPE - RHEL7.x - SAP – unmount
                 HPE - SLES12 - SAP – unmount
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


## Operating Systems

These plan scripts are compatible with all Red Hat Enterprise Linux for SAP Applications 7.x and 
SUSE Linux Enterprise Server for SAP Applications 12 releases.

We have tested the following Operating Systems:

- Red Hat Enterprise Linux for SAP Applications 7.6
- Red Hat Enterprise Linux for SAP Applications 7.4
- SUSE Linux Enterprise Server for SAP Applications 12 SP4
- SUSE Linux Enterprise Server for SAP Applications 12 SP3
- SUSE Linux Enterprise Server for SAP Applications 12 SP2

## SAP Software

We have tested the following SAP HANA versions:
- SAP HANA 2.0 SPS04
- SAP HANA 2.0 SPS03

We have tested the following SAP applications:
- SAP S/4HANA 1809
- SAP BW/4HANA 1.0 SR1
