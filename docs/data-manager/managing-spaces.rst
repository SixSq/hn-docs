
Managing Spaces
===============

Space can be seen as a virtual directory, which contents are stored on
distributed storage resources provisioned by storage providers. Each
space must have at least one provider supporting it with a non-zero
storage space (quota). The effective quota available to a single space
is the sum of storage quotas dedicated to this space by all storage
providers supporting it.

Creating spaces
---------------

Spaces in Onedata can be seen as virtual volumes or buckets, where an arbitrary
directory and file hierarchy can be created.

To create a new data space follow these steps:

- In the Onezone Web Interface unfold Data space management tab
  located on the left menubar

.. image:: images/spacestabhome.png
   :scale: 50 %

- Click Create new space button

- Provide new space name in the text edit field and confirm

New space will appear in the list of spaces designated with a unique ID.

Supporting spaces with Oneprovider instances
--------------------------------------------

By default new space has no storage resources associated with it. In
order to add storage quota to a space, generate a space support token
by clicking on `Get support` option under space name, copy the
presented token and send the token to the administrator of the
Oneprovider instance whose the storage resources should be assigned to
this space.

