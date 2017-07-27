# Artifact bundle contents

--------------------------------------------------------------------------------

                    File name: HPE-RHEL-7.3-Docker-Worker-With-Aqua-Security-2017-06-16.zip
                Name (in manifest): HPE-RHEL-7.3-Docker-Worker-With-Aqua-Security-2017-06-16
                       Description: Artifacts to deploy a Docker EE Worker node, add it to an existing UCP swarm, deploy the Aqua Agent and register it with the Aqua Management Console.
                             Dated: 2017-07-21 (16:59:16)

--------------------------------------------------------------------------------

Deployment Plans:

                Name: RHEL-7.3-Docker-Worker-With-AquaSec-2017-06-16 (Type:OEDeploymentPlan)
         Description: Deploy Docker EE Worker node, add it to an existing UCP swarm and register it with the Aqua Console



Build Plans:

               Name: RHEL-7.3-Docker-Worker-With-AquaSec-2017-06-16 (Type:deploy)
        Description: Deploy Docker worker node with Aqua Security Agent


Plan Scripts:

               Name: 030-RHEL-7.3-configure-multiple-NIC-teaming (deploy)
           FullName: 02c5a2cd-f2de-4a37-85e5-bd5fe1c96572_planscript.json
        Description: configure NIC teaming


               Name: 080-RHEL-7.3-erase-drive (deploy)
           FullName: 0801e3bd-057b-479c-b476-eaa77c69c8f6_planscript.json
        Description: 080-RHEL-7.3-erase-drive


               Name: 020-RHEL-7.3-change-root-password (deploy)
           FullName: 0923da9a-867c-43ae-8332-265430bd0747_planscript.json
        Description: 020-RHEL-7.3-change-root-password


               Name: 150-RHEL-7.3-config-firewalld-for-Docker (deploy)
           FullName: 23a1f1f2-9f32-4f8e-a43e-b5364b7b9569_planscript.json
        Description: 150-RHEL-7.3-config-firewalld-for-Docker


               Name: 160-Aqua-agent-configure (deploy)
           FullName: 3fee7668-0fa5-4077-8866-d5309ee7e80a_planscript.json
        Description: Loads the Aqua Security Agent


               Name: 070-Docker-configure-proxy (deploy)
           FullName: 4b9c1a44-70bf-482b-bc59-488628660786_planscript.json
        Description: 070-Docker-configure-proxy


               Name: 999-RHEL-7.3-unmount (general)
           FullName: 5ca01201-8cc2-49c7-88ed-85d025ce570e_planscript.json
        Description: It removes the temporary directory created during mount and unmounts from the root partition.


               Name: 120-upload-bash-helpers (deploy)
           FullName: 67059839-b5b9-45f4-ad29-e8d0ce3806e6_planscript.json
        Description: 120-upload-bash-helpers


               Name: 140-Docker-UCP-worker-configure (deploy)
           FullName: 69042882-3e25-4eea-9416-adcb29290dd9_planscript.json
        Description: 140-Docker-UCP-worker-configure


               Name: 130-RHEL-7.3-Docker-preconfig (deploy)
           FullName: 6c8db592-87e1-4ba2-b516-deb2600369f0_planscript.json
        Description: 130-RHEL-7.3-Docker-preconfig


               Name: 110-Docker-remove-key.json (deploy)
           FullName: 80d4102c-155b-4aca-8a12-4b4e78de9685_planscript.json
        Description: 110-Docker-remove-key.json


               Name: 090-RHEL-7.3-Docker-configure-devicemapper (deploy)
           FullName: 8b65441f-a4cc-42df-89b6-a51b2a0fdfb7_planscript.json
        Description: 090-RHEL-7.3-Docker-configure-devicemapper


               Name: 100-RHEL-7.3-Docker-Bootstrap (deploy)
           FullName: 931e55db-c745-4601-87ec-81153f58a2aa_planscript.json
        Description: 100-RHEL-7.3-Docker-Bootstrap


               Name: 040-RHEL-7.3-Docker-configure-ntp (deploy)
           FullName: 95f7cb71-3977-4872-9a31-163ae7371747_planscript.json
        Description: 040-RHEL-7.3-Docker-configure-ntp


               Name: 010-RHEL-7.3-set-iscsi-initiatorname (deploy)
           FullName: ac1172e8-efc3-4042-9f9a-25dd7671b6d4_planscript.json
        Description: 010-RHEL-7.3-set-iscsi-initiatorname


               Name: 000-RHEL-7.3-mount-and-validate (general)
           FullName: df273ca2-72b3-4fe9-bf52-72aa51e5a2e2_planscript.json
        Description: mount RHEL partition and validate its contents


               Name: 050-RHEL-7.3-configure-hostname (deploy)
           FullName: e4d7f92b-f37c-4d56-905e-c846539c8e7f_planscript.json
        Description: 050-RHEL-7.3-configure-hostname


               Name: 060-RHEL-7.3-manage-security-services (deploy)
           FullName: eb567ac5-4f25-49df-b202-9725f1d3bef9_planscript.json
        Description: 060-RHEL-7.3-manage-security-services
