# 3 virtual machines to use: 1 for internal services and 2 for the main application stack.

## Each application stack machine  have these services set up and running:

### HAProxy
### Keepalived
### Agama in the Docker container
### MySQL (master on one machine, replica on the another)
### Bind slave
### Prometheus exporters for HAProxy, Keepalived, MySQL and Bind slave

## Remaining machine should have these services set up and running:

### Bind master
### InfluxDB
### Telegraf
### Prometheus
### Grafana
### Nginx as frontend for Grafana and Prometheus
