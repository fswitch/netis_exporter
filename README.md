# Netis statistics exporter

Prometheus exporter for Netis home routers.  
Netis routers can send port statistics via web.  
This exporter gets statistics data and makes it suitable for Prometheus TSDB.

---

## Config (netis_exporter.yml):

```yml
# IP address for local server
source_ip_address: 127.0.0.1

# IP port for local server
source_ip_port: 9960

# Time in seconds betbeen certificate queries
query_time: 10

# Timeout for netis info
http_timeout: 7

# Show http logs (0/1)
http_log_show: 0

# Routers configuration
equipment:
  192.168.1.1:
    instance: 192.168.1.1
    url: http://192.168.1.1/cgi-bin-igd/netcore_get.cgi
    login: Admin
    password:
  192.168.11.1:
    instance: 192.168.11.1
    url: http://192.168.11.1/cgi-bin-igd/netcore_get.cgi
    login: admin
    password:
```

### Prometheus scraping

```
scrape_configs:
  - job_name: "netis"
    scrape_interval: 5s
    static_configs:
      - targets: ["127.0.0.1:9960"]
```

### Grafana example

![Netis Grafana](https://raw.githubusercontent.com/fswitch/netis_exporter/main/netis_grafana.png)
