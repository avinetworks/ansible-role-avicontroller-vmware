# avinetworks.avicontroller-vmware

Using this module you are able to install the Avi Vantage Controlller, to Vmware cloud.

Requirements
------------
 - python >= 2.6
 - avisdk
 - pyVmomi
 - pyVim
 - ovftool

Role Variables
--------------

| Variable | Required | Default | Comments |
|----------|----------|---------|----------|
|ovftool_path|Yes||Path for VMWare ovftool|
|vcenter_host|Yes||VMWare host IP|
|vcenter_user|Yes||VMWare user name|
|vcenter_password|Yes||VMWare password|
|datacenter|No|Picked first from the list|Name of VMWare datacenter|
|cluster|No|Picked from the first in the list of given datacenters clusters|Name of a cluster in the datacenter|
|datastore|No|Picked up the datastore having max free space|Name of datastore on which VM to be deployed|
|mgmt_network|Yes||Management network name|
|disk_mode|No|thin|Deployment disk mode|
|controller_ova_path|Yes||Path to controller OVA file|
|vm_name|Yes||Name of a controller VM on VMWare|
|power_on|No|True|VM to be powered on after provisioning|
|vcenter_folder|No|Datacenter root|Folder path to deploy VM|
|ssl_verify|No|False|ovftool sslverify option|
|state|No|present|Option to specify create or destroy the infra|

Dependencies
------------

A list of other roles hosted on Galaxy should go here, plus any details in regards to parameters that may need to be set for other roles, or variables that are used from other roles.

Example Playbook
----------------

Including an example of how to use your role:

```
- hosts: localhost
  connection: local
  roles:
    - { role: avinetworks.avicontroller-vmware }
  tasks:
    - name: Deploy Avi Controller
      deploy_controller:
        ovftool_path: /usr/lib/vmware-ovftool
        vcenter_host: '{{ vcenter_host }}'
        vcenter_user: '{{ vcenter_user }}'
        vcenter_password: '{{ vcenter_password }}'
        datacenter: 10GTest
        cluster: Arista
        mgmt_network: Mgmt_Ntwk_3
        controller_ova_path: ./controller.ova
        vm_name: ansible-test-controller
        power_on: true
        vcenter_folder: network/avi
```

License
-------

Apache 2.0

Author Information
------------------

contact: Avi Networks [avi-sdk@avinetworks.com]


