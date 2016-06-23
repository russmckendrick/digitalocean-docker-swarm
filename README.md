DigitalOcean Docker 1.12rc2
====================

This playbook launches a number of Ubuntu 16.04 droplets in [Digital Ocean][1], configures a firewall, installs Docker 1.12rc2 and then sets up a Swarm so you can test the new orchestration features.

## Setup

You will also need to ensure you have the following python module installed on your localhost;

```
sudo pip install 'dopy\>=0.3.5,\<=0.3.5'
```

## Varibles

Create a file called `do.yml` in the `group_vars` folder, this file should contain your DigitalOcean API token and also the name of the ssh key you want to use.

```
echo 'do\_api\_token: "sdnjkjdfgkjb345kjdgljknqwetkjwhgoih314rjkwergoiyu34rjkherglkhrg0"' \> group\_vars/do.yml
echo 'ssh\_key\_name: "Your Key Name"' \> group\_vars/do.yml
```

You can change the number of workers being launched in the `environment.yml` which is also in the `group_vars` folder.

### Notes on SSH keys

If the key matches one that you already have present in DigitalOcean then you must use the exact name associated with the key, if you don't you will receive an error stating that the key already exists.

If you don't have a key on the machine you are running Ansible on then one will be created and uploaded.

## Launching & Destroying the Droplets

To launch the droplets run;

```
ansible-playbook -i hosts launch.yml
```

Once you have finished and want to remove them run;

```
ansible-playbook -i hosts remove.yml
```