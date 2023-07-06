# This github repo goes over an example on how to use ansible to populate device models and metavariables mappings to FortiManager Cloud

## Script example on how to use ansible to populate Fortimanager cloud device model and device mappings

### Instruction
Create an IAM API user, you are going to support.fortinet.com/iam and creating an IAM API user to use in your script
![image](https://github.com/MikeWissa/ansible-script-add-device-to-fortimanager-cloud/assets/6186228/81e7c6f7-a32f-42bc-83a9-c782f1fdef3a)
![image](https://github.com/MikeWissa/ansible-script-add-device-to-fortimanager-cloud/assets/6186228/032c50be-5709-4796-99b9-e3933370cc35)
![image](https://github.com/MikeWissa/ansible-script-add-device-to-fortimanager-cloud/assets/6186228/26c22f86-35ce-4d75-8136-12f2958546f3)
![image](https://github.com/MikeWissa/ansible-script-add-device-to-fortimanager-cloud/assets/6186228/70607d7e-1a45-4b7c-bc37-a22f87030014)
![image](https://github.com/MikeWissa/ansible-script-add-device-to-fortimanager-cloud/assets/6186228/eaf31e8a-ec81-465b-ac0f-1403ce350b1c)

## Download credentials file
It asks for a password to download credential file, download and unzip the file.

## Login to Fortimanager and Get the URL for your fortimanager instance

## Install ansible on your favorite platform

## Install the ansible collection
ansible-galaxy collection install --upgrade fortinet.fortimanager

## Create a hosts inventory file to use in your ansible script 
This is used to connect to fortimanager cloud
### hosts file example
[fortimanagers]

fortimanager01 ansible_host=your-fortimanager-url-region.fortimanager.forticloud.com FORTICLOUD_APIID='API user'  FORTICLOUD_PASSWD='yourapi_password'

[fortimanagers:vars]

ansible_network_os=fortinet.fortimanager.fortimanager

## Update device-list.csv
You will need to have pre-created a device blueprint.
You will also need to specify your device serial number.
Other information can be provided like group, which is not in that script.

## Update metavariables
metavars.csv contains the variable ansible will be parse to create the dynamic mapping
The metavariables would need to be precreated

## Run the ansible playbook
ansible-playbook -i hosts fmgrcloud.yml
