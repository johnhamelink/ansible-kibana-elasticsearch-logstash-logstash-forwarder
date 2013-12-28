kibana, elasticsearch, logstash, logstash-forwarder ansible roles
=================================================================

Setup
-----

Start up two clean ubuntu 13.10 x64 servers. One will be for logstash, elastic search and kibana, the other will be for logstash-forwarder.

Generate SSL keys by running:

    openssl req -x509 -batch -nodes -newkey rsa:2048 -keyout logstash-forwarder.key -out logstash-forwarder.crt

Copy the resultant .key and .crt files to `roles/logstash/files/certs` and `roles/logstash-forwarder/files/certs`.

Copy `vars/global_vars.yml.sample` and customise it to suit your setup - it should be fairly self explanatory.

Generate a htpasswd file (You can use an online tool if you don't have apache installed - [this one is known to work](http://www.htpasswdgenerator.net/)) and put it in `roles/kibana/files/htpasswd`.

Add `elastic_search`, `kibana`, `logstash`, and `logstash-forwarder` groups to your ansible hosts file

Installation
------------

### Elastic Search:

`ansible-playbook elastic_search.yml`

### Kibana:

`ansible-playbook kibana.yml`

### Logstash:

`ansible-playbook logstash.yml`

### Logstash-forwarder:

`ansible-playbook logstash-forwarder.yml`

