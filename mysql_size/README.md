mysql_{data,index}_size
=========

graph mysql filesystem size totals.

installation
------------
```
$ sudo cp mysql_{data,index}_size /usr/share/munin/plugins/
$ sudo cp sudoers.d-munin-node /etc/sudoers.d/munin-node
$ sudo chmod 440 /etc/sudoers.d/munin-node
$ cd /etc/munin/plugins/
$ sudo ln -fs /usr/share/munin/plugins/mysql_data_size .
$ sudo ln -fs /usr/share/munin/plugins/mysql_index_size .
```

screenshots
-----------

![mysql data size - year](https://raw.github.com/dsobon/munin-plugins/master/mysql_size/img/mysql_data_size-year.png)
![mysql index size - year](https://raw.github.com/dsobon/munin-plugins/master/mysql_size/img/mysql_index_size-year.png)
