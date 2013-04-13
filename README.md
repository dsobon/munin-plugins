munin-plugins
=============

useful munin plugins that I modified or I wrote over the years

apache_response_*
=================

create graphs based on apache's access.log

Graphs such as: (over a 5 minute period)
- total response time to service requests.
- maximum response time.
- total requests count.
- response times to service static file requests, represented in percentiles.
- response times to service dynamic requests, represented in percentiles.
- http status codes.

requirements
------------
apache logging format modified to:
```
LogFormat "%v %{X-Real-IP}i %l %u %t \"%r\" %>s %b %D \"%{Referer}i\" \"%{User-Agent}i\"" vhost_combined
```

installation
------------
```
$ sudo cp apache_response /usr/share/munin/plugins/
$ cd /etc/munin/plugins/
$ sudo ln -fs /usr/share/munin/plugins/apache_response apache_response_count
$ sudo ln -fs /usr/share/munin/plugins/apache_response apache_response_http_status
$ sudo ln -fs /usr/share/munin/plugins/apache_response apache_response_time_max
$ sudo ln -fs /usr/share/munin/plugins/apache_response apache_response_time_percentile_dynamic
$ sudo ln -fs /usr/share/munin/plugins/apache_response apache_response_time_percentile_static
$ sudo ln -fs /usr/share/munin/plugins/apache_response apache_response_time_total
```

limitations
-----------
* tested with apache, on Debian stable ("squeeze" 6.0)
* does not handle logrotate properly, so one 5 minute interval will be missed.
* does not yet support munin-node "autoconf" or "suggest"
* access.log filename is hardcoded.
* presumes locale (for 3-character month strings) is English.
* definition (based on file extension) of "static" is hardcoded.
* "dynamic" is defined as mutually exclusive of "static"
