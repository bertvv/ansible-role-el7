# Ansible role `el7`

A role for basic setup of an EL7-based machine. This role contains general tasks for basic configuration. Specifically, the responsibilities of this role are to:

* Install external repositories like EPEL (we assume through RPM packages)
* Install packages not in the default minimal installation,
* Turn specified services on or off,
* Create users and groups,
* Set up an administrator account with an SSH key,
* Apply basic security settings, like turning on SELinux and the firewall

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

## License

BSD

## Author Information

Bert Van Vreckem (bert.vanvreckem@hogent.be)

