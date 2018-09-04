
The artifact bundle "RHEL7 Deploy RAC Node" includes an OS build plan and associated plan scripts that may be used to deploy a two-node 
Oracle RAC 12c cluster on RHEL.  

**OS Build Plan:**

**Name:** RHEL 7 Deploy RAC Node Rev2 </br>
**Description:** Deploy an Oracle RAC node

**Plan Scripts:**

The OS build plan "RHEL 7 Deploy RAC Node Rev2" uses the following plan scripts:

**Name:** RHEL7 – RAC mount </br>
**Description:** mount the root partition of the server

**Name:** RHEL7 - RAC hostname configuration Rev2 </br>
**Description:** Configure all RAC hostnames and IP addresses

**Name:** RHEL7 - RAC update resolv.conf </br>
**Description:** set domain for DNS search

**Name:** RHEL7 - RAC public and private network configuration Rev2 </br>
**Description:** Configure network devices for public network and RAC private network

**Name:** RHEL7 - RAC update kernel params </br>
**Description:** update kernel parameters in sysctl.conf

**Name:** RHEL7 - RAC update limits </br>
**Description:** Update oracle-limits.conf

**Name:** RHEL7 - RAC create udev rules and multipath.conf </br>
**Description:** Create udev rules and multipath.conf for Oracle RAC volumes

**Name:** RHEL7 - RAC create firstboot service </br>
**Description:** Create service to run only at first boot

**Name:** RHEL7 - RAC create firstboot.sh script </br>
**Description:** Create first boot script for Oracle RAC install

**Name:** RHEL7 - RAC create sshkeydist.sh </br>
**Description:** Create script to copy SSH keys across RAC nodes

**Name:** RHEL7 - RAC create install_RAC.sh </br>
**Description:** Create script to install Oracle RAC

**Name:** RHEL7 - RAC unmount </br>
**Description:** Cleanup temp directory and unmounts root partition

**Name:** HPE - Foundation 1.0 - attempt or fail deployment </br>
**Description:** This plan script may be used to test failure of OS deployment
