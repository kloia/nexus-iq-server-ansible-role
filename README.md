Ansible Role: Nexus IQ Server
=========

Installs and configures Nexus IQ Server as systemd service.

Requirements
------------

This role requires java on target environment. OS should be linux and systemd based one because role installs Nexus IQ Server as systemd service.

Role Variables
--------------
All the variables and their default values are: 

    # Default variables are like this:
    
    iqserver_license_path: ""
    iqserver_base_url: http://localhost:8070
    iqserver_create_sample_data: true
    iqserver_user: iqserver
    iqserver_base_dir: /opt/nexus-iq-server
    iqserver_base_log_level: ALL
    iqserver_use_nginx: false
    iqserver_enable_jira_integration: false
    iqserver_jira_server: ""
    iqserver_jira_username: ""
    iqserver_jira_api_token: ""
    iqserver_enable_rut: false
    iqserver_rut_username_header: ""
    iqserver_rut_logout_url: ""
    
- You should always provide `iqserver_license_path`. This path located in the machine that runs ansible playbook not target machine.
- You can set log level by `iqserver_base_log_level`. Can be OFF, ERROR, WARN, INFO, DEBUG, TRACE, or ALL.
- If you want to use nginx as a reverse proxy you should set `iqserver_use_nginx` to `true`. You should also set `iqserver_base_url` to URL that will be set for the IQ Server.
- If you are just trying out, you can set `iqserver_create_sample_data` to `true`. This option loads sample data to IQ Server.
- You can enable Jira integration by setting `iqserver_enable_jira_integration` to true and configure by these variables: [`iqserver_jira_server`, `iqserver_jira_username`, `iqserver_jira_api_token`].
- You can set up reverse proxy authentication by setting `iqserver_enable_rut` to and configure by these variables: [`iqserver_rut_username_header`, `iqserver_rut_logout_url`].

Dependencies
------------

None.

Example Playbook
----------------

The role needs root privileges.

    - hosts: servers
      roles:
        - role: kloia.nexus-iq-server
          become: true

License
-------

MIT/BSD

Author Information
------------------

This role was created in 2020 by [kloia](https://kloia.com/).