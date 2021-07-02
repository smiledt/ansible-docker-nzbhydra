Docker-NZBHydra
=========

A role to spin up a NZBHydra docker container. This role was heavily inspired by (and all credit goes to) Calvin Bui's roles. This is only being published for integration into my AWX instance. 

Requirements
------------

Docker needs to be installed and configured on the server. 

Role Variables
--------------

Required variables are listed here, along with default example values. See defaults/main.yml. Any of these defaults can be overwritten by using the vars role directory. 

    nzbhydra_name: nzbhydra

This is the name of the container. 

    nzbhydra_image: linuxserver/nzbhydra

The image container. By default this pulls from linuxserver.io.

    nzbhydra_ports:
     - 8989:8989
     - 9898:9898

These are the exported ports of the container.

    nzbhydra_config_directory: /opt/nzbhydra

This is the directory that config files will be stored. This is mapped to /config in the container. 

    nzbhydra_tv_directory: /tmp/tv

This is the directory that NZBHydra will move TV shows and managed files to. Usually we want this directory on some sort of media network storage. This is mapped to /tv inside the container.

    nzbhydra_download_directory: /tmp/downloads

This is where files will be placed for NZBHydra to managed, either via a download client or manually. This is mapped to /completed inside the container.

    nzbhydra_environment_variables:
      PUID: "1000"
      PGID: "1000"
      TZ: America/Chicago

This is a dictionary of extra environment variables for the container. 

    nzbhydra_docker_additional_options:
      restart_policy: unless-stopped

Another dictionary, this time of additional options for the container. By default, this sets the container to start on boot unless it was previously stopped. 

    nzbhydra_config:
      ApiKey: "abc123"
      UrlBase: "example.com"
      LaunchBrowser: "False"
      AnalyticsEnabled: "False"

This is not currently in use - the applicable code is commented out in the task. 

Dependencies
------------

None.

Example Playbook
----------------

    - name: Deploy the NZBHydra Container.
      hosts: rr
      become: true
      roles:
      - role: docker-nzbhydra

License
-------

BSD

Author Information
------------------

Derek Smiley - Aspiring System Administrator/Ansible Automation Engineer

Connect with me on LinkedIn - https://www.linkedin.com/in/derek-smiley/