Role for change nginx configs. 
==============================

With this role you can change nginx config and roll it back
if something went wrong.

Requirements
------------

This role requires Ansible 2.5 or higher.

Role Variables
--------------

`nginx_config_src`
Path to your nginx config file. **Required option**.

`nginx_config_dest`
Path where config must be stored on server. (_default: /etc/nginx/conf.d/nginx.conf_).
`nginx_command_to_check_config`
Command to check nginx configuration. (_default: nginx -t_)

`nginx_command_to_reload`
Command to reload server. (_default: service nginx reload_)

Add role to project:
----------------
Add role into your requirements(_requirements.yml_ for example):
```yaml
- src: lexa-uw.nginx-configuration
  version: v1.0.0
  name: nginx-configuration
```

Install role: `ansible-galaxy install -r ./requirements.yml --roles-path ./roles/`

Playbook example:
----------------

```yaml
- hosts: all
  vars_files:
    - vars/main.yml
  roles:
    - { role: nginx-configuration }
```

Inside `vars/main.yml`
```yaml
nginx_config_src: templates/example.conf
nginx_config_dest: /etc/nginx/conf.d/example.conf
nginx_command_to_reload: /etc/init.d/nginx reload
```