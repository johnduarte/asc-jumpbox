# Deploy a jumpbox on the ASC Phobos instance
This set of playbooks creates a small dedicated instance on Phobos for you to
use as a jumpbox.  The primary intent of this instance is to allow you to run
an MNAIO snapshot deploy from a remote box without worrying about remaining
connected to the Phobos network while the deploy is being conducted.

To create your Phobos jumpbox, run the following command from within the root
directory of this repository.  You will be prompted for any additional
information that the playbooks require.

```
ansible-playbook playbooks/main.yml
```

## Prerequisites
The playbooks make the following assumptions.  These conditions should be
satisfied prior to running the playbook.

1. You are currently connected to the Phobos network.
2. Your Phobos credentials have been sourced in the current shell session
   (e.g. `source $HOME/openrc`).

## What does this do?
This set of playbooks perform the following:
* Creates Ubuntu jumpbox server in you server domain with your given key.
* Creates an unprivileged user with your Phobos username.
* Copies your private key to the user account.
* Configures SSH and openrc for Phobos connection.
* Clones the
  [rpco-test-deploy-images](https://github.com/rcbops/rpco-test-deploy-images)
  repository to the root of the user's home directory.
