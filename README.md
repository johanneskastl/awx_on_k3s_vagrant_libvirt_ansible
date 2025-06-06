# awx_on_k3s_vagrant_libvirt_ansible

Vagrant-libvirt setup that creates a VM with k3s.

On top of k3s Ansible installs [AWX](https://github.com/ansible/awx), the
web-based UI for running Ansible.

Default OS is openSUSE Leap 15.6, but that can be changed in the Vagrantfile.
Please be aware, that this might break the Ansible provisioning.

## Vagrant

1. You need `vagrant`, obviously. And `git`. And Ansible...
1. Fetch the box, per default this is `opensuse/Leap-15.6.x86_64`, using
   `vagrant box add opensuse/Leap-15.6.x86_64`.
1. Make sure the git submodules are fully working by issuing
   `git submodule init && git submodule update`
1. Run `vagrant up`
1. Wait until the Ansible provisioning has finished. At the end, it should
   output the AWX URL and the credentials.
1. Open the AWX URL in a private browser window and accept the self-signed
   certificate (after checking it, of course). And you should see your AWX
   instance...
1. Party!

## Cleaning up

The VMs can be torn down after playing around using `vagrant destroy`. This will
also remove the kubeconfig file `ansible/k3s-kubeconfig` as well as all
files related to the self-signed certificate (`ansible/awx.*`).

## License

BSD-3-Clause

## Author Information

I am Johannes Kastl, reachable via git@johannes-kastl.de
