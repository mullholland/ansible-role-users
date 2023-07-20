# [users](#users)

Manages users and groups

|GitHub|GitLab|Quality|Downloads|Version|
|------|------|-------|---------|-------|
|[![github](https://github.com/mullholland/ansible-role-users/workflows/Ansible%20Molecule/badge.svg)](https://github.com/mullholland/ansible-role-users/actions)|[![gitlab](https://gitlab.com/opensourceunicorn/ansible-role-users/badges/master/pipeline.svg)](https://gitlab.com/opensourceunicorn/ansible-role-users)|[![quality](https://img.shields.io/ansible/quality/57640)](https://galaxy.ansible.com/mullholland/users)|[![downloads](https://img.shields.io/ansible/role/d/57640)](https://galaxy.ansible.com/mullholland/users)|[![Version](https://img.shields.io/github/release/mullholland/ansible-role-users.svg)](https://github.com/mullholland/ansible-role-users/releases/)|

## [Example Playbook](#example-playbook)

This example is taken from [`molecule/default/converge.yml`](https://github.com/mullholland/ansible-role-users/blob/master/molecule/default/converge.yml) and is tested on each push, pull request and release.

```yaml
---
- name: Converge
  hosts: all
  become: true
  gather_facts: true
  vars:
    users_groups:
      - name: "mullholland"  # required
      # gid: "4711"  # optional
      # state: ""  # optional
      # system: ""  # optional [bool]
      - name: "full_opts"  # required
        gid: "4711"  # optional
        state: "present"  # optional
        system: "true"  # optional [bool]
      - name: "group_absent"  # required
        state: "absent"  # optional

    users:
      - name: "mullholland"
      # state: ""  # optional (defaults to present)
      # uid: ""  # optional
      # system: ""  # optional (bool)
      # `group` and `groups` must exist.
      # the user's primary group
      # group: "mullholland"
      # List of groups user will be added to.
      # When set to an empty string '', the user is
      # removed from all groups except the primary group.
      # groups: "users"
      # create_home: ""  # optional [bool] (defaults to true)
      # home: ""  # optional
      # shell: ""  # optional
      # comment: ""  # optional
      # Optionally set the user's password to this crypted value.
      # To create a disabled account on Linux systems, set this to '!' or '*'.
      # password: ""  # optional
      # update_password: ""  # optional [always/on_create] (defaults to on_create)
      # An expiry time for the user in epoch, it will be ignored on platforms that do not support this.
      # expires: ""  # optional
      # ssh_key: "ssh-rsa yyyxxccvvbb"  # optional
      # ssh_key_exclusive: ""  # optional [bool]
      # ssh_key_manage_dir: ""  # optional [bool]
      - name: "full_user"
        state: "present"
        uid: "4711"
        system: "true"
        group: "mullholland"
        groups: "users"
        create_home: "true"
        home: "/home/full_user"
        shell: "/bin/sh"
        comment: "managed by ansible"
        password: "!"
        # update_password: "always"  # not idempotent
        # expires: "1422403387"  # not idempotent
        ssh_key: |
          ssh-rsa yyyxxccvvbb
          ssh-rsa yyyxxccvvbbb
        ssh_key_exclusive: "true"
        ssh_key_manage_dir: "true"
      - name: "user_absent"
        state: "absent"

  roles:
    - role: "mullholland.users"
```


## [Role Variables](#role-variables)

The default values for the variables are set in [`defaults/main.yml`](https://github.com/mullholland/ansible-role-users/blob/master/defaults/main.yml):

```yaml
---
users_groups: []
# - name: "mullholland"  # required
#   gid: "4711"  # optional
#   state: ""  # optional
#   system: ""  # optional [bool]

users: []
# - name: "mullholland"
#   state: ""  # optional (defaults to present)
#   uid: ""  # optional
#   system: ""  # optional (bool)
#   `group` and `groups` must exist.
#   the user's primary group
#   group: "mullholland"
#   List of groups user will be added to.
#   When set to an empty string '', the user is
#   removed from all groups except the primary group.
#   groups: "users"
#   create_home: ""  # optional [bool] (defaults to true)
#   home: ""  # optional
#   shell: ""  # optional
#   comment: ""  # optional
#   Optionally set the user's password to this crypted value.
#   To create a disabled account on Linux systems, set this to '!' or '*'.
#   password: ""  # optional
#   update_password: ""  # optional [always/on_create] (defaults to on_create)
#   An expiry time for the user in epoch, it will be ignored on platforms that do not support this.
#   expires: ""  # optional
#   ssh_key: "ssh-rsa yyyxxccvvbb"  # optional
#   ssh_key_exclusive: ""  # optional [bool]
#   ssh_key_manage_dir: ""  # optional [bool]
```

## [Requirements](#requirements)

- pip packages listed in [requirements.txt](https://github.com/mullholland/ansible-role-users/blob/master/requirements.txt).


## [Context](#context)

This role is a part of many compatible roles. Have a look at [the documentation of these roles](https://mullholland.net) for further information.

Here is an overview of related roles:
![dependencies](https://raw.githubusercontent.com/mullholland/ansible-role-users/png/requirements.png "Dependencies")

## [Compatibility](#compatibility)

This role has been tested on these [container images](https://hub.docker.com/u/mullholland):

|container|tags|
|---------|----|
|[EL](https://hub.docker.com/repository/docker/mullholland/docker-centos-systemd/general)|all|
|[Amazon](https://hub.docker.com/repository/docker/mullholland/docker-amazonlinux-systemd/general)|Candidate|
|[Fedora](https://hub.docker.com/repository/docker/mullholland/docker-fedora-systemd/general)|all|
|[Ubuntu](https://hub.docker.com/repository/docker/mullholland/docker-ubuntu-systemd/general)|all|
|[Debian](https://hub.docker.com/repository/docker/mullholland/docker-debian-systemd/general)|all|

The minimum version of Ansible required is 2.10, tests have been done to:

- The previous version.
- The current version.
- The development version.

If you find issues, please register them in [GitHub](https://github.com/mullholland/ansible-role-users/issues)

## [License](#license)

[MIT](https://github.com/mullholland/ansible-role-users/blob/master/LICENSE).

## [Author Information](#author-information)

[Mullholland](https://mullholland.net)

Please consider [sponsoring me](https://github.com/sponsors/mullholland).
