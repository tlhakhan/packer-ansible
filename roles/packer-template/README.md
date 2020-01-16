# README

- The private keys for packer to access the virtual machine upon build completion and the vsphere host access should be placed at the `playbook_dir`/ssh folder.
  - The private key file is currently expected to be called `packer.private`, this could be a symlink to the real file.
  - Ensure that the real private key file has a permission mode of `0600` otherwise `ssh` will complain about the permissions on the key.

- Take a look at the `default/main.yml` file for expected variables and its keys.
  - The variables here should be overidden by an `extra-vars` input.
