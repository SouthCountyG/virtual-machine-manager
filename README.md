Ansible Code for Managing Local VMs


File Notes:
vars.yml - input needed before running
- image path
- password
- vm_name
- vm_domain
You can also change the VM size and a couple other options

templates/user-data-custom - account info for new VM
- username
- ssh_authorized_keys ## if you want to have an SSH KEY added

custom-vm.yml - I am adding roles that will build apps/services on the new VM (see end of file)


Roles:
reg_n_packs - Auto register VM to RHN/Satellite/Whatever and install some base packages

reg_n_packs/vars/main.yml
- registration_password ## I used an Ansible Vault password for security.. do as you please

reg_n_packs/tasks/main.yml
- username ## Username used for registration_password
- pool_ids ## subscription number if using RHN


ansible_tower - Auto build Ansible Tower on newly provisioned VM

ansible_tower/vars/main.yml
- admin_password ## Ansible Tower Admin password
- pg_password ## Ansible Tower Postg password
- rabbitmq_password ## Ansible Tower, you guessed it, Rabbitmq password
