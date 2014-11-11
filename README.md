# Name

munin-koha

# Description

A collection of short scripts that can be used to collect data for Munin from
instances of Koha installed using the Debian packages. 

* http://munin-monitoring.org/
* http://koha-community.org/

# Get the code

```
git clone https://github.com/Libriotech/munin-koha.git
```

# Setup

(This assumes you are on Debian or a Debian-based distro. It also assumes you
cloned the Git repo into /home/me/munin-koha.)

In general, what you do is create symlinks from the Git repo to 
/etc/munin/plugins. How you create the links varies a bit from script to script:

Some scripts take arguments in the form of additions to the script name. For
example, to tell the koha_ script to keep track of the *items* table for the 
instance called *mylibrary*, you would do:

```
ln -s /home/me/munin-koha/koha_ /etc/munin/plugins/koha_items_mylibrary 
```

In the following examples, the foloowing conventions will be used:

* [table] = the name of a table in the Koha database
* [instance] = the name of a Koha instance on the server, as reported by koha-list

## koha

Purpose: Show the total number of instances and the number of Zebra processes on
the server.

Setup:

```
ln -s /home/me/munin-koha/koha /etc/munin/plugins/koha
```

This script does not take any arguments.

## koha_

Purpose. Keeps track of one table for one instance. 

Setup:
```
ln -s /home/me/munin-koha/koha_ /etc/munin/plugins/koha_[table]_[instance] 
```
Example:
```
ln -s /home/me/munin-koha/koha_ /etc/munin/plugins/koha_items_mylibrary 
```

## kohaall_

Purpose: Keep track of one table for all instances on the server.

Setup:
```
ln -s /home/me/munin-koha/kohaall_ /etc/munin/plugins/kohaall_[table]
```
Example:
```
ln -s /home/me/munin-koha/kohaall_ /etc/munin/plugins/kohaall_items
```

## kohacirc_

Purpose: Keeps track of circulation-related data for one instance. Specifically:

* Issues
* Returns
* Holds

The stats will begin counting from zero every day. 

Setup:
```
ln -s /home/me/munin-koha/kohacirc_ /etc/munin/plugins/kohacirc_[instance]
```
Example:
```
ln -s /home/me/munin-koha/kohacirc_ /etc/munin/plugins/kohacirc_mylibrary
```

## kohapending_

Purpose: Keeps track of pending messages (in the message_queue table) for one
instance. Specifically:

* Issues
* Returns
* Holds

Can be used to check that messages are being sent and are not piling up in the 
database.

Setup:
```
ln -s /home/me/munin-koha/kohapending_ /etc/munin/plugins/kohapending_[instance]
```
Example:
```
ln -s /home/me/munin-koha/kohapending_ /etc/munin/plugins/kohapending_mylibrary
```

# Author

Magnus Enger, Libriotech

# Bug reports, patches, pull requests

...are all very welcome!

https://github.com/Libriotech/munin-koha

# License

This is free software; you can redistribute it and/or modify
it under the terms of the GNU General Public License as published by
the Free Software Foundation; either version 3 of the License, or
(at your option) any later version.

This file is distributed in the hope that it will be useful,
but WITHOUT ANY WARRANTY; without even the implied warranty of
MERCHANTABILITY or FITNESS FOR A PARTICULAR PURPOSE. See the
GNU General Public License for more details.

You should have received a copy of the GNU General Public License
along with this file; if not, write to the Free Software
Foundation, Inc., 51 Franklin St, Fifth Floor, Boston, MA 02110-1301 USA













