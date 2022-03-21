# v1.9 Pending Release Notes

## Breaking Changes

* The mds liveness and startup probes are now configured by the filesystem CR instead of the cluster CR. To apply the mds probes, they need to be specified in the filesystem CR. See the [filesystem CR doc](Documentation/ceph-filesystem-crd.md#metadata-server-settings) for more details. See #9550

## Features

* The number of mgr daemons for example clusters is increased to 2 from 1, resulting in a standby mgr daemon.
  If the active mgr goes down, Ceph will update the passive mgr to be active, and rook will update all the services
  with the label app=rook-ceph-mgr to direct traffic to the new active mgr.
* Network encryption is configurable with settings in the CephCluster CR. Requires the 5.11 kernel or newer.
* Network compression is configurable with settings in the CephCluster CR. Requires Ceph Quincy (v17) or newer.
* Add support for custom ceph.conf for csi pods. See #9567
