# Ansible role `el7`

A role for basic setup of an EL7-based machine. This role contains general tasks that are common to all managed machines. Specifically, the responsibilities of this role are to:

* Install external repositories like EPEL (we assume through RPM packages)
* Install packages not in the default minimal installation,
* Turn specified services on or off,
* Create users and groups,
* Set up an administrator account with an SSH key,
* Apply basic security settings, like turning on SELinux and the firewall

## Requirements



## Role Variables

| Variable               | Required | Default | Choices | Comments                                                                                 |
| :---                   | :---     | :---    | :---    | :---                                                                                     |
| `el7_admin_ssh_pubkey` | no       | -       | -       | The public SSH key for the admin user that allows her to log in without a password       |
| `el7_admin_user`       | no       | -       | -       | The name of the user that will manage this machine.                                      |
| `el7_install_packages` | no       | -       | -       | Packages that should be installed.                                                       |
| `el7_remove_packages`  | no       | -       | -       | Packages that should **not** be installed                                                |
| `el7_repositories`     | no       | -       | -       | External repositories that should be added (e.g. EPEL). Specify the URL to RPM packages. |
| `el7_start_services`   | no       | -       | -       | Services that should be running and enabled.                                             |
| `el7_stop_services`    | no       | -       | -       | Services that should **not** be running                                                  |
| `el7_user_groups`      | no       | -       | -       | User groups that should be present.                                                      |
| `el7_users`            | no       | -       | -       | Users that should be present.                                                            |

## Dependencies

No dependencies.

## Example Playbook

TODO: Including an example of how to use your role (for instance, with variables passed in as parameters) is always nice for users too:

## License

BSD

## Author Information

Bert Van Vreckem (bert.vanvreckem@hogent.be)

