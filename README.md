# Oracle APEX

This repository covers my personal [Oracle APEX](https://apex.oracle.com/) instance. Please consider this as a **test environment** which is not ready for production usage, there are unprotected passwords in some files!

The following chapters cover setup, upgrade and backup. I publish it because it might help anybody to setup a similar solution.

# Requirements

* Ansible 2.7 or higher
* Docker runtime environment with docker compose
* A Linux user which is used by Docker to run the container

# Setup

First of all, please instantiate Ansible var samples:

```
cd /YOUR/REPO/CHECKOUT/PATH/ansible
cp roles/install-oracle/vars/main-sample.yml roles/install-oracle/vars/main.yml
```

Open `roles/install-oracle/vars/main.yml` in your prefered editor and adapt settings.

Open `roles/install-oracle/tasks/main.yml` in your prefered editor and uncomment `Copy conn_string.txt` to make sure the initial conn_string.txt gets copied to the target server. Make sure to add comments to this again afterwards.

To execute this Ansible playbook, you can use following command:

```
ansible-playbook -i /PATH/TO/INVENTORY /YOUR/REPO/CHECKOUT/PATH/ansible/ansible_playbook.yml
```

Open `roles/install-oracle/tasks/main.yml` in your prefered editor and add comment for `Copy conn_string.txt` again.

## Start

After setup, all containers needs to get started executing

```
docker compose up -d
```

in setup directory.

You can verify successfull startup by connecting to sqlplus client using [sqlplus_connect.sh](/ansible/roles/install-oracle/templates/sqlplus_connect.sh.j2).
