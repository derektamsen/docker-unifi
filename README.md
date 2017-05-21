# docker-unifi
Docker unifi container runs the Unifi Controller Software from
[Ubiquiti](https://www.ubnt.com) and Mongodb. This setup contains a several docker volumes
to store all of the mongodb data, unifi logs, and unifi data. These volumes will
be persistently stored on disk via docker volumes. This allows the containers to be
stopped, removed, and upgraded without losing any settings or files.

# Starting the unifi controller
- clone this repository to your docker host.
- `docker-compose up -d`

# Configure unifi
- Launch a browser to the unifi controller admin gui: `http://<your_docker_host:8080`
- Configure the controller as usual: (https://www.ubnt.com/download/unifi/default/default/unifi-controller-v5-user-guide)
- You may need to modify the `inform` url from the controller via dns or dhcp.
  This will allow your access points to find the management console.
  See: https://help.ubnt.com/hc/en-us/articles/204909754-UniFi-Layer-3-methods-for-UAP-adoption-and-management

# Notes
- The compose file uses a linked mongdb container to store the controller data and stats
  - The controller builds a custom `data/system.properties` file to include settings
    from https://community.ubnt.com/t5/UniFi-Wireless/External-MongoDB-Server/td-p/1305297.
- If you need assistance migrating from another installation of the controller
  see: https://help.ubnt.com/hc/en-us/articles/115002869188-UniFi-Migrating-Sites-with-Site-Export-Wizard
