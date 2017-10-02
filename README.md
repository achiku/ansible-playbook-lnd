# ansible-playbook-lnd
Ansible playbook to install and manage lnd configuration

### prepar venv

```
$ pip install -r requirements.txt
```

### spin up ec2 instance

- c4.large
- 250GB SSD
- Ubuntu 14.04 is used in this example

```
$ ansible-playbook create-ec2.yml -e group=security_group_name \
  -e key=your_key_pair_name -e role=iam_role_name \
  -e ami=ami_id -e region=region_name -e subnet=subnet_id
```

check if it's running.

```
$ ansible -i ec2.py tag_Name_btcnode -a 'uname -a' -u ubuntu
```

### provisioning

```
ansible-playbook server-provision.yml -i ./ec2.py
```

### config

```
ansible-playbook server-config.yml -i ./ec2.py
```

wait for a while to sync entire testnet blockchain.
