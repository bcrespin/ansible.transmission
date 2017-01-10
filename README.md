this role install et configure transmission ( see : https://transmissionbt.com/ ) 
currently, it's work on:
  - OpenBSD ( tested on 6.0/RELEASE)
  
Requirements
------------

no special requirement
but p2p port has to be set in pf, as this role don't change anything in pf.conf 

Role Variables
--------------

for now, few transmissions variables are configurable, feel free to edit defaults/main.yml & template/settings.json.j2
as I made this role quickly for my meet...

if transmission_block_list_enable is true, feed transmission_block_list_url with something...
this is to have a filter list of ip in the apps, some fellow guys provide that, example: http://john.bitsurge.net/public/biglist.p2p.gz
- transmission_block_list_enabled: 'false'
- transmission_block_list_url: ''

if you want to store incomplete download to a specific folder, change it to true and provide the path (it should be created be the role) 
- transmission_incomplete_download_enabled: 'false'
- transmission_incomplete_download_folder: '/var/transmission/Downloads'

where to store the stuff downloaded
- transmission_download_folder: '/var/transmission/Downloads'

this is a listening port, that should be open in the firewall & eventually redirected if the host where this role will be installed is behind a NAT... 
 - transmission_peer_port: 55413

if transmission_rpc_enabled is true, this is to allow web access to manage configuration/add torrent,
if transmission_rpc_white_list_enabled is true, transmission_rpc_white_list is a list of IP allowed to connect ( I would recommend to use a reverse proxy to more controle who can connect if it need to be reach from internet)
- transmission_rpc_enabled: 'true'
- transmission_rpc_white_list: '127.0.0.1'
- transmission_rpc_white_list_enabled: 'true'

this is the service name used to manage to service for the OS
it should be setup by role depending of OS/linux distrib 
- transmission_service_name

Dependencies
------------

no dependencies..

Example Playbook
----------------

    - hosts: my_p2p_seedbox
      roles:
         - { role: ansible.transmission }

License
-------

BSD

Author Information
------------------
me
