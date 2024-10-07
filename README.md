Ansible role: Gvm
=========

Ansible Galaxy role for [gvm] on Debian / Ubuntu / RedHat / OSX.

Install it with the following command:

```sh
Coming soon!
```

Requirements
------------

None.

Role Variables
--------------

List of variables in ansible-role-gvm:

```sh
---
# defaults gvm source
gvm_env: 'user' # use 'user' for local user installation or 'system' for global installation 
gvm_repo_host: 'https://raw.githubusercontent.com' # use default gvm repository
gvm_repo_owner: 'moovweb' # default repo owner
gvm_repo_name: 'gvm' # default repo name
gvm_repo_branch: 'master' # default repo branch
gvm_script_installer: '{{ gvm_repo_host }}/{{ gvm_repo_owner }}/{{ gvm_repo_name }}/{{ gvm_repo_branch }}/binscripts/gvm-installer' # default manual installer script

# defaults gvm destination, use '$HOME' for local user installation or use custom global e.g: '/usr/local'
gvm_destination: '$HOME' # default use ansible user home
gvm_owner: '{{ ansible_facts.user_id }}' # default to use ansible fact user
gvm_owner_group: '{{ gvm_owner }}' # default to use ansible fact user

# use default config from gvm, refer to https://github.com/moovweb/gvm/blob/master/binscripts/gvm-installer#L110
gmv_no_update_profile: '' # if you set with any value, profile config will not auto update

# profile config if gmv_no_update_profile is true
gvm_manual_update_profile_file: '/etc/profile.d/gvm.sh' # create custom bash if `gmv_no_update_profile` not empty
gvm_manual_update_profile_content: '[[ -s "{{ gvm_destination }}/gvm/scripts/gvm" ]] && source "{{ gvm_destination }}/gvm/scripts/gvm"' # create custom content to `gvm_manual_update_profile_file`

# default golang version config
gvm_go_version: 'go1.22.8'
```

Dependencies
------------

None.

Example Playbook
----------------

Default installation:
```yaml
- hosts: servers
  roles:
  - role: ansible-role-gvm
    vars:
      gvm_env: 'user'
```

Global installation:
```yaml
- hosts: servers
  roles:
  - role: ansible-role-gvm
    vars:
      gvm_env: 'system'
      gvm_destination: '/usr/local'
      gmv_no_update_profile: 'true'
```

License
-------

Distributed under the terms of the [MIT] license,
_Ansible role Gvm_ is free and open source software.

Author Information
------------------

[Nedya Prakasa]. Build roles for [dPanel].

[dPanel]: https://cloud.terpusat.com/
[Nedya Prakasa]: https://github.com/prakasa1904
[mit]: https://opensource.org/licenses/MIT
[gvm]: https://github.com/moovweb/gvm
[devetek]: https://github.com/devetek