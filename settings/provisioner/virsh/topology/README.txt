This is a placeholder for the new provisioner to hold the topology files
in the form of:

provisioner:
    nodes:
        # Dict of nodes
        example:
            name: controller
            cpu: !lookup provisioner.image.cpu
            memory: 8192
            os: &os
                type: linux
                variant: !lookup provisioner.image.os.variant
            disk: &disk
                size: !lookup provisioner.image.disk.size
                path: /var/lib/libvirt/images
            network: &network_params
                interfaces: &interfaces
                    management: &mgmt_interface
                        label: eth0
                    data: &data_interface
                        label: eth1
                    external: &external_interface
                        label: eth2
            groups:
                - controller
                - openstack_nodes


