# prov_satellite_vm_pxe-less
Ansible playbook to provision a host via Satellite using PXE-less discovery

# Process

# Install the discovery image
yum install foreman-discovery-image rubygem-smart_proxy_discovery
foreman-maintain service restart

# In the Satellite server
In the Satellite web UI, navigate to Infrastructure > Subnets, select a
subnet, click the Capsules tab, and select the Discovery Proxy that you
want to use. Perform this for each appropriate subnet.

# Created a customized version of the discovery image
cd /usr/share/foreman-discovery-image/
discovery-remaster foreman-discovery-image-3.5.4-2.iso 'proxy.url=https://sat.example.com:9090 proxy.type=proxy fdi.pxauto=1' custom-auto-discovery-image.iso
