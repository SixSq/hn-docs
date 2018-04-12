OneData management
==================

  .. figure:: ../../images/oneprovider-slide.png
     :alt: Oneprovider archictecture
     :width: 100%
     :align: center

Oneprovider implements drivers for storages such as NFS, Lustre, Ceph, Openstack SWIFT and S3.

In order to function properly, Oneprovider needs to communicate with the Onezone service,
        which requires a public IP address and specific ports opened to the world.

We have set a sample OneZone deployment at : https://onezone.rhea-hn.com

Once logged in, we will add a new space



- Setup a space (supported by S3 bucket should be sufficient)
- Attach a backend to a OneProvider instance

(TODO see https://onedata.org/#/home/documentation/doc/administering_onedata/provider_space_support.html)

