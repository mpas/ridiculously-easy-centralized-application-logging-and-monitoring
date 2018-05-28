# General

## Prerequisites

* Docker installed
* Docker Compose installed

### Build the required Docker images

* Execute `./build-docker-images.sh`

This will build the following images:
* **Fluentd Docker image**: with plugins that are used during the demo
* **Spring Boot Demo Docker image**: Small Spring Boot app that generates some logging information

### Configuration

* Please add your own Slack API webhook in `./steps/2-monitoring-using-prometheus-including-alerting/config.yml`

---

## Step 1: Logging
* Start Fluentd using docker-compose > dc up
* Show Fluent config > fluent.conf
* Show docker-compose.yml > including portmapping/log driver + springboot tag
* Navigate to [SpringBoot][springboot] and generate some load showing the log entry
* Navigate to [Kibana][kibana] and show the data that flows in
  * Filter on possibilities

## Step 2: Monitoring
* Start Prometheus using docker-compose > dc up
* Prometheus
  * Navigate to [Prometheus webinterface][prometheus-ui] > show prometheus webinterface
  * Show config and targets
  * Explain that scraping can be done by various ways (Consul, DNS, or dropping in new config file)
* Navigate to [Prometheus metrics][prometheus-metrics] > show the metrics that Prometheus itself is generating
* Navigate to [Node Exporter metrics][node-exporter-metrics] > show the metrics
* Navigate to [cAdvisor metrics][cadvisor-metrics] > show the metrics
* Grafana
  * Explain Grafana
  * Navigate to [Grafana][grafana]
  * Login using > admin/admin
  * Add Datasource
  * Load Dashboards
* Alerting
  * Introduce the Ping container
    * Stop/Start the Ping container -> `docker-compose stop ping`
  * View the results in:
    * Slack 
    * [Mailslurper][mailslurper]

# Demo Links

## Logging
* [Kibana][kibana]
* [SpringBoot][springboot]

## Monitoring
* [Prometheus webinterface][prometheus-ui]
* [Prometheus metrics][prometheus-metrics]
* [Node Exporter][node-exporter]
* [Node Exporter metrics][node-exporter-metrics]
* [AlertManager][alertmanager]
* [cAdvisor webinterface][cadvisor-ui]
* [cAdvisor metrics][cadvisor-metrics]
* [Grafana][grafana]
* [Mailslurper][mailslurper]

[kibana]: http://localhost:5601
[springboot]: http://localhost:8080
[prometheus-ui]: http://localhost:9090
[prometheus-metrics]: http://localhost:9090/metrics
[node-exporter]: http://localhost:9100
[node-exporter-metrics]: http://localhost:9100/metrics
[alertmanager]: http://localhost:9093
[cadvisor-ui]: http://localhost:8095
[cadvisor-metrics]: http://localhost:8095/metrics
[grafana]: http://localhost:3000
[alert-manager]: http://localhost:9093
[mailslurper]: http://localhost:9000