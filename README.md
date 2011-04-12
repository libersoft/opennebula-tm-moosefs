opennebula-tm-moosefs
=====================

OpenNebula is a fully open-source toolkit to build IaaS Private, Public and Hybrid Clouds.

MooseFS is a fault tolerant, network distributed file system. It spreads data over several physical servers which are visible to the user as one resource.

By combining these two components you can build an effective cloud with commodity hardware and cheap storage, ensuring high availability, replication and scalability.

Installation
------------

Requisites:
* a MooseFS storage mounted on every nebula host under the same folder (ex: /srv/vms);

oned.conf:
    VM_DIR=/srv/vms/deploy
    IMAGE_REPOSITORY_PATH = /srv/vms/images
    TM_MAD = [
        name       = "tm_moosefs",
        executable = "one_tm",
        arguments  = "tm_moosefs/tm_moosefs.conf" ]

Copy `tm_moosefs` in `/etc/one` or `$ONE-LOCATION/etc`
Copy `tm_commands/moosefs` in `/usr/lib/one/tm_commands`

Configure nebula host to use the new transfer manager:
    onehost create host01 im_kvm vmm_kvm tm_moosefs

Extra Hacks
-----------

If you mv your `/var/lib/one` inside moosefs (ex: `/srv/vms/one`) and symlink it back, you can easily achieve database replication with sqlite for easy frontend migration.

Contact 
-------

LiberSoft: http://www.libersoft.it
OpenNebula: http://opennebula.org
MooseFS: http://www.moosefs.org

License 
-------

Copyright 2011, LiberSoft (libersoft.it)

Licensed under the Apache License, Version 2.0 (the "License"); you may
not use this file except in compliance with the License. You may obtain
a copy of the License at http://www.apache.org/licenses/LICENSE-2.0

Unless required by applicable law or agreed to in writing, software
distributed under the License is distributed on an "AS IS" BASIS,
WITHOUT WARRANTIES OR CONDITIONS OF ANY KIND, either express or implied.
See the License for the specific language governing permissions and
limitations under the License.

