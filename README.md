# Splunk Deploy
Ansible playbooks to automate the deployment of a distributed Splunk architecture. Variables are accepted to configure the `Artifact Replication Factor`, `Index Replication Factor`, `Search Factor`, and `Cluster Label`.

## Run
`ansible-playbook -i inventory main.yml`

## Droppings
Configuration and installation files to be copied to the remote hosts for the installation process. Please modify the .conf files before deployment.

- `user seed.conf`: Credentials to use when installing Splunk. This username and password will be used for all of the Splunk instances.
- `shcluster.conf`: Configuration file for the search head cluster.
- `splunk.deb`: Place the Splunk .deb package here to be used for installation

## Inventory
Fill out the inventory file with the hosts to be used for the Splunk install. Each line should be a single hostname or IP address. Each address should only be referenced once and under the proper group for the expected role in the cluster. Please see Splunk documentation for deployment best practices.

The host designated as Manager will server the role as Cluster Manager, SHC Deployer, Deployment Server, and License Manager.

## Post install
The Monitoring Console should be accessed on the deployed manager node to specify server roles and finalize the distributed deployment.