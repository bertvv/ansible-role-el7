# Ansible role `el7`

A role for basic setup of an EL7-based machine. This role contains general tasks for basic configuration. Specifically, the responsibilities of this role are to:

* Install external repositories like EPEL (we assume through RPM packages)
* Install packages not in the default minimal installation,
* Turn specified services on or off,
* Create users and groups,
* Set up an administrator account with an SSH key,
* Apply basic security settings, like turning on SELinux and the firewall

## Roadmap

See https://huboard.com/bertvv/ansible-role-el7

## Requirements

No specific requirements

## Role Variables

None of the role variables are required, no default values are set. If the variable is not set, the corresponding setting is not applied.

| Variable               | Required | Type              | Comments                                                                                                    |
| :---                   | :---     | :---              | :---                                                                                                        |
| `el7_admin_ssh_pubkey` | no       | scalar            | The public SSH key for the admin user that allows her to log in without a password. The user should exist.  |
| `el7_admin_user`       | no       | scalar            | The name of the user that will manage this machine.                                                         |
| `el7_install_packages` | no       | sequence          | Sequence of packages that should be installed.                                                              |
| `el7_remove_packages`  | no       | sequence          | Sequence of packages that should **not** be installed                                                       |
| `el7_repositories`     | no       | sequence          | Sequence of URLs to RPM packages to install external repositories (e.g. EPEL)                               |
| `el7_start_services`   | no       | sequence          | Sequence of services that should be running and enabled.                                                    |
| `el7_stop_services`    | no       | sequence          | Sequence of services that should **not** be running                                                         |
| `el7_user_groups`      | no       | sequence          | Sequence of user groups that should be present.                                                             |
| `el7_users`            | no       | sequence of dicts | Sequence of dicts specifying users that should be present. |

Users are specified by dicts like this:

```Yaml
el7_users:
  - name: johndoe
    comment: 'John Doe'
    groups:
      - users
      - devs
    password: '$6$WIFkXf07Kn3kALDp$fHbqRKztuufS895easdT [...]'
```

Optionally, you can specify the `shell`, which defaults to `/bin/bash`.

## Dependencies

No dependencies.

## Example Playbook

See the [test playbook](https://github.com/bertvv/ansible-role-el7/blob/master/tests/test_full.yml)

## Testing

The `tests` directory contains acceptance tests for this role in the form of two playbooks and a Vagrant environment. The directory `tests/roles/el7` is a symbolic link that should point to the root of this project in order to work. You may want to change the base box into one that you like. The current one is based on Box-Cutter's [CentOS Packer template](https://github.com/box-cutter/centos-vm).

- The playbook [`test.yml`](tests/test.yml) is minimal. It applies the role to a VM, but doesn't set any variables
- The playbook [`test-full.yml`](tests/test_full.yml) sets all role variables.

For testing the installation of an SSH key, a key pair is provided in `tests/sshkey`. It goes without saying that you should never use this key pair in a production machine! You should be able to log in with:

```
ssh -i tests/sshkey/admin_key -p 2222 admin@127.0.0.1
```

Vagrant uses port forwarding on the NAT interface (that is always present in a VM). The first VM under control of Vagrant is assigned port 2222, following ones 2200, 2201, etc. Data sent to this port on your host system is forwarded to port 22 (ssh) on the VM.

## License

BSD

## Author Information

Bert Van Vreckem (bert.vanvreckem@hogent.be)

