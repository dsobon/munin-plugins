mongodb_*
=========

graph mongodb status ( http://HOST:PORT/_status )

installation
------------
```
$ chmod 755 mongodb_
$ sudo cp mongodb_ /usr/share/munin/plugins/
$ cd /etc/munin/plugins/
$ for F in btree memory command connections flush_time commits_writelock lock_time {locking,locked}_{read,write}; do \
    sudo ln -fs /usr/share/munin/plugins/mongodb_ $F \
  done
```

requirements
-------------
```
$ sudo apt-get install libjson-perl
```

limitations
-----------
* does not yet support munin-node "autoconf" or "suggest"
* database filtering is not supported.
* splitting graphs into multiple graphs (based on inclusive filter) is not supported.
