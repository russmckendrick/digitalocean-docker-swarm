DigitalOcean Docker 1.12rc2
====================

This [Ansible](https://www.ansible.com) Playbook launches three Ubuntu 16.04 droplets in [Digital Ocean](https://m.do.co/c/52ec4dc3647e), configures a firewall, installs Docker 1.12rc2 and then sets up a Swarm so you can test the new orchestration features.

## Setup

Create a file called `do.yml` in the `group_vars` folder, this file should contain your DigitalOcean API token and also the name of the ssh key you want to use.

```
echo 'do_api_token: "sdnjkjdfgkjb345kjdgljknqwetkjwhgoih314rjkwergoiyu34rjkherglkhrg0"' > group_vars/do.yml
echo 'ssh_key_name: "Your Key Name"' > group_vars/do.yml
```

You will also need to ensure you have the following python module installed on your localhost;

```
sudo pip install 'dopy>=0.3.5,<=0.3.5'
```

### Notes on SSH keys

If the key matches one that you already have present in DigitalOcean then you must use the exact name associated with the key, if you don't you will receive an error stating that the key already exists.

If you don't have a key on the machine you are running Ansible on then one will be created and uploaded.

## Running Ansible

To run Ansible run;

```
ansible-playbook -i hosts site.yml
```
