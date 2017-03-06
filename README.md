Nagios check script for elasticsearch
=====================================

This is a simple script to check the status of an elasticsearch cluster.
It now supports elasticsearch 5.0 with or without x-pack authentication. 

Usage:

    ./check_elasticsearch -H es1.mysite.com -P 9200 -o /tmp [ -a ] [ -u <username> -p <password> ] 

This will output the standard Nagios format:

    OK - elasticsearch (elasticsearch) is running. status: green; timed_out: false; number_of_nodes: 1; number_of_data_nodes: 1; active_primary_shards: 2; active_shards: 2; relocating_shards: 0; initializing_shards: 0; unassigned_shards: 0  | 'active_primary'=2 'active'=2 'relocating'=0 'init'=0

`OK` / `WARNING` / `CRITICAL` correspond to the status being "green", "yellow", or "red" respectively.

If you have a Graphite server you can send data to it via:

    ./check_elasticsearch -H es1.mysite.com -P 9200 -c graphite.foo.com -C 2003
    
This will output data to the following metric prefix:

    system.$cluster_name.cluster.app.elasticsearch.cluster

Removed reference to Chef cookbook since this fork won't support it. 


Script is a modified version of check\_phpfpm by [MAB](https://github.com/mabitt/mab-nagios-plugins).

Enjoy.

# License

MIT.

