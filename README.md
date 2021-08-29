# In the OpenStack cloud

* Generate an Application Credential in the project with `member` role, make note of the ID and Secret
* Create a Manila CephFS share you want to mount on clients: Type for the Arcus cloud is `ceph01_cephfs`, do not make globally public (for obvious reasons)
* Create a RW CephX access rule for the share; This will dynamically create the Ceph access key to mount the share on clients. "Access To" is the CephX user name, e.g. use `euclid_compute`, etc
* Edit `group_vars/{group_name}/{var,vault}` to use your own generated AppCred ID and Secret 

# Prerequisites

```
virtualenv ~/.venv --system-site-packages
source ~/.venv/bin/activate
pip install -r requirements.txt
ansible-galaxy install -r requirements.yml
```

# Mount share on clients

* Run playbook:

`ansible-playbook -i inventory  manila-test.yml --ask-vault-pass -v`
