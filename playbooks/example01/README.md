### Start the VM
- With a Vagrant file, include running an initial Ansible playbook from the  
Vagrant file.  
ex:  
```  
config.vm.provision "ansible" do |ansible|
    ansible.playbook = "main.yml"
  end
```  
- Start the VM  
```vagrant up```  
This will setup an inventory file for you to run individual Ansible playbooks.  


- When you want to run a playbook on a running Vagrant VM, point to the  
inventory file in the ansible-playbook command  
```ansible-playbook -i .vagrant/provisioners/ansible/inventory/vagrant_ansible_inventory vim.yml```  



