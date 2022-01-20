# [users](#users)

|GitHub|GitLab|
|------|------|
|[![github](https://github.com/mullholland/ansible-role-users/workflows/Ansible%20Molecule/badge.svg)](https://github.com/mullholland/ansible-role-users/actions)|[![gitlab](https://gitlab.com/mullholland/ansible-role-users/badges/master/pipeline.svg)](https://gitlab.com/mullholland/ansible-role-users)|[![quality](https://img.shields.io/ansible/quality/unset)](https://galaxy.ansible.com/mullholland/users)|

Manages users and groups

## [Role Variables](#role-variables)

These variables are set in `defaults/main.yml`:
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
#   ssh_keys: "ssh-rsa yyyxxccvvbb"  # optional
#   ssh_key_exclusive: ""  # optional [bool]
#   ssh_key_manage_dir: ""  # optional [bool]
```


## [Example Playbook](#example-playbook)

This example is taken from `molecule/default/converge.yml` and is tested on each push, pull request and release.
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





## [Compatibility](#compatibility)

This role has been tested on these [container images](https://hub.docker.com/u/mullholland):

-   [debian9](https://hub.docker.com/r/mullholland/docker-molecule-debian9)
-   [debian10](https://hub.docker.com/r/mullholland/docker-molecule-debian10)
-   [debian11](https://hub.docker.com/r/mullholland/docker-molecule-debian11)
-   [ubuntu1804](https://hub.docker.com/r/mullholland/docker-molecule-ubuntu1804)
-   [ubuntu2004](https://hub.docker.com/r/mullholland/docker-molecule-ubuntu2004)
-   [centos7](https://hub.docker.com/r/mullholland/docker-molecule-centos7)
-   [centos-stream8](https://hub.docker.com/r/mullholland/docker-molecule-centos-stream8)
-   [centos-stream9](https://hub.docker.com/r/mullholland/docker-molecule-centos-stream9)
-   [ubi8](https://hub.docker.com/r/mullholland/docker-molecule-ubi8)
-   [fedora34](https://hub.docker.com/r/mullholland/docker-molecule-fedora34)
-   [fedora35](https://hub.docker.com/r/mullholland/docker-molecule-fedora35)
-   [amazonlinux](https://hub.docker.com/r/mullholland/docker-molecule-amazonlinux)
-   [rockylinux8](https://hub.docker.com/r/mullholland/docker-molecule-rockylinux8)
-   [almalinux8](https://hub.docker.com/r/mullholland/docker-molecule-almalinux8)

The minimum version of Ansible required is 2.10, tests have been done to:

-   The last 2 versions.
-   The current version.





If you find issues, please register them in [GitHub](https://github.com/mullholland/ansible-role-users/issues)

## [License](#license)

MIT


## [Author Information](#author-information)

[Mullholland](https://github.com/mullholland)

## [Special Thanks](#special-thanks)

Template inspired by [Robert de Bock](https://github.com/robertdebock)
