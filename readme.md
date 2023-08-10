# What do i need? 
 - python3 
 - pip install --user -r ./requirements.txt
 - ansible-galaxy collection install ansible.utils
 - ssh keys https://docs.oracle.com/en/cloud/cloud-at-customer/occ-get-started/generate-ssh-key-pair.html
 - Ansible https://docs.ansible.com/ansible/latest/installation_guide/intro_installation.html
 - Vagrant https://developer.hashicorp.com/vagrant/downloads
 - VirtualBox https://www.virtualbox.org/wiki/Linux_Downloads


## Kubernetes overlay network 
Using Calico https://docs.tigera.io/calico/latest/about (config)[https://docs.tigera.io/calico/latest/manifests/calico.yaml]
https://github.com/projectcalico/calico


# 

https://docs.ansible.com/ansible/devel/reference_appendices/config.html#avoiding-security-risks-with-ansible-cfg-in-the-current-directory
ANSIBLE_CONFIG=$PWD/ansible.cfg

https://github.com/garutilorenzo/ansible-role-linux-kubernetes/blob/master/requirements.txt
https://kubernetes.io/docs/setup/production-environment/tools/kubespray/

role variables: https://stackoverflow.com/questions/33126156/is-it-possible-to-define-playbook-global-variables-in-ansible

https://medium.com/@joatmon08/playing-with-kubeadm-in-vagrant-machines-36598b5e8408
https://medium.com/@aleverycity/kubeadm-init-join-and-externalip-vs-internalip-519519ddff89

https://gist.github.com/rkaramandi/44c7cea91501e735ea99e356e9ae7883