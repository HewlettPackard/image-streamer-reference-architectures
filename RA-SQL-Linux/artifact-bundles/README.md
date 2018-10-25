Artifact bundle contents
--------------------------------------------------------------------------------
--------------------------------------------------------------------------------
         File name: 7.4 Deploy Microsoft SQL Server instance.zip
         Name (in manifest): RHEL 7.4 Deploy Microsoft SQL Server instance
         Description: OS Build Plan and Plan Scripts to deploy SQL server instance on RHEL 7.4.
         Dated: 2018-10-16 (08:32:03)
--------------------------------------------------------------------------------

Build Plans:

	       Name: RHEL7.4 SQL Standalone (Type:deploy)
	Description: Deploy SQL Server instance on RHEL 7.4.


Plan Scripts:

	       Name: RHEL-mount-and-validate-2017-12-12 (general)
	   FullName: 9afd95ad-671c-470c-b5ca-75a9ee4c5815_planscript.json
	Description: mount the root partition of the server and validate image against invalid image captures


	       Name: RHEL Single NIC Teaming (deploy)
	   FullName: 971e9119-9ae8-4e2e-86dc-925b852bcdba_planscript.json
	Description: Configures management NIC teaming for host


	       Name: RHEL-configure-hostname-2017-12-12 (deploy)
	   FullName: 030942ac-91ee-412e-baee-47c8090eafaf_planscript.json
	Description: configure hostname


	       Name: SQLConfig (deploy)
	   FullName: 8b06a05e-56ed-4238-9017-69d73ebf0093_planscript.json
	Description: Configure SQL server setup using mssql-conf setup, enable SQL server agent and configure SQL configuration settings  


	       Name: RHEL-unmount-2017-12-12 (general)
	   FullName: 4a99779d-df8a-485f-8d7e-4788d0cd4d4a_planscript.json
	Description: cleans up the temporary directory created during mount and unmounts the root partition.

Artifact bundle contents
--------------------------------------------------------------------------------
--------------------------------------------------------------------------------
         File name: RHEL 7.4 Deploy Serviceguard cluster node with SQL server instance.zip
         Name (in manifest): RHEL 7.4 Deploy Serviceguard cluster node with SQL server instance
         Description: OS build plan and plan script to deploy Serviceguard cluster node with SQL server instance on RHEL 7.4.
         Dated: 2018-10-16 (08:44:31)
--------------------------------------------------------------------------------

Build Plans:

	       Name: RHEL7.4_SQL_Serviceguard cluster node build Plan (Type:deploy)
	Description: Deploy Serviceguard cluster node with SQL server instance


Plan Scripts:

	       Name: RHEL-mount-and-validate-2017-12-12 (general)
	   FullName: 9afd95ad-671c-470c-b5ca-75a9ee4c5815_planscript.json
	Description: mount the root partition of the server and validate image against invalid image captures


	       Name: NIC Teaming for HeartBeat and Stationary_IP for Serviceguard (deploy)
	   FullName: c8474665-2169-4383-81d6-76c4b5671190_planscript.json
	Description: Configures NIC teaming for Serviceguard cluster HeartBeat and Stationary_IP


	       Name: RHEL-configure-hostname-2017-12-12 (deploy)
	   FullName: 030942ac-91ee-412e-baee-47c8090eafaf_planscript.json
	Description: configure hostname


	       Name: SQLConfig (deploy)
	   FullName: 8b06a05e-56ed-4238-9017-69d73ebf0093_planscript.json
	Description: Configure SQL server setup using mssql-conf setup, enable SQL server agent and configure SQL configuration settings


	       Name: RHEL -Configure sshkey and deploy cluster (deploy)
	   FullName: 474f561f-bf8e-44fa-86d5-d51c35a7924d_planscript.json
	Description: Configure ssh keys for root account and configure the Serviceguard cluster


	       Name: RHEL-unmount-2017-12-12 (general)
	   FullName: 4a99779d-df8a-485f-8d7e-4788d0cd4d4a_planscript.json
	Description: cleans up the temporary directory created during mount and unmounts the root partition.
