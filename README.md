opennebula-tm-moosefs
=====================

OpenNebula is a fully open-source toolkit to build IaaS Private, Public and Hybrid Clouds.

MooseFS is a fault tolerant, network distributed file system. It spreads data over several physical servers which are visible to the user as one resource.

By combining these two components you can build an effective cloud with commodity hardware and cheap storage, ensuring high availability, replication and scalability.

Article on the official OpenNebula blog by [Giovanni Toraldo](http://gionn.net/about-me): http://blog.opennebula.org/?p=1512

Installation
------------

Requires a MooseFS filesystem mounted on every OpenNebula host under the same folder (e.g.: /srv/vms);

Configure your oned.conf accordingly:

    VM_DIR=/srv/vms/deploy
    IMAGE_REPOSITORY_PATH = /srv/vms/images
    TM_MAD = [
        name       = "tm_moosefs",
        executable = "one_tm",
        arguments  = "tm_moosefs/tm_moosefs.conf" ]

Copy the `tm_moosefs` folder into `/etc/one` or `$ONE-LOCATION/etc`

Copy the `tm_commands/moosefs` into `/usr/lib/one/tm_commands`

Configure OpenNebula hosts to use the new transfer manager with:

    $ onehost create host01 im_kvm vmm_kvm tm_moosefs dummy

Goodies
-----------

When using SQLite database, if you move your `/var/lib/one` (and symlink it back)
or you do a self-contained installation into the MooseFS volume (e.g.: `/srv/vms/one`),
you can easily achieve database replication and a simple fail-over of the frontend on another machine.

Links 
-------

OpenNebula: http://opennebula.org

MooseFS: http://www.moosefs.org

LiberSoft: http://www.libersoft.it


License 
-------

Copyright 2011-2012, LiberSoft (info@libersoft.it)

Licensed under the Apache License, Version 2.0 (the "License"); you may
not use this file except in compliance with the License. You may obtain
a copy of the License at http://www.apache.org/licenses/LICENSE-2.0

Unless required by applicable law or agreed to in writing, software
distributed under the License is distributed on an "AS IS" BASIS,
WITHOUT WARRANTIES OR CONDITIONS OF ANY KIND, either express or implied.
See the License for the specific language governing permissions and
limitations under the License.
