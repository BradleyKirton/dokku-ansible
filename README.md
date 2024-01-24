# Ansible playbooks for setting up dokku

This repository contains some playbooks and scripts for automating the setup of a virutal machine running dokku.

## Setup

The project assumes you are using [mise-en-place](https://mise.jdx.dev/) for managing your python runtimes and loading the `.env` variables.

To setup the project run the following:

```console
./scripts/install
```

If you require `vaults` create a file `.vault.key` in the project root (This file is in the .gitignore by default). Once you have created the .vault.key you can create the vaults by running:

```console
./scripts/createvaults
```

To edit a vault run:

```console
./scripts/editvault -v {production,staging}
```

To print a vault run:

```console
./scripts/printvault -v {production,staging}
```

To rekey a vault run:

```console
./scripts/rekeyvault -v {production,staging}
```

## Provisioning a VM

Once you have a VM running in the cloud you can provision it by:

- Populating the `hosts` within the relevant inventory i.e. staging or production
- Running the provision playbook

```console
./scripts/runplay -i {production,staging} -p provision
```

## Installing dokku

Once you have provisioned your VM you can install dokku by:

- Populating the dokku_domain variable within the playbook group_vars
- Running the dokku playbook

```console
./scripts/runplay -i {production,staging} -p dokku
```