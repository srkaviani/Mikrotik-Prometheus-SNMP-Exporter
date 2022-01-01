# Mikrotik-Prometheus-SNMP-Exporter
How To Monitor Mikrotik Devices (RouterOS) with Prometheus - SNMP Exporter and Grafana

Manual deploy
1.add into prometheus.yml


```

  - job_name: Mikrotik
    static_configs:
      - targets:
        - 192.168.88.1  # SNMP device IP.
    metrics_path: /snmp
    params:
      module: [mikrotik]
    relabel_configs:
      - source_labels: [__address__]
        target_label: __param_target
      - source_labels: [__param_target]
        target_label: instance
      - target_label: __address__
        replacement: localhost:9116  # The SNMP exporter's real hostname:port.
        
```


2.Configure Prometheus and run /snmp/snmp_exporter 

3.Add dashboard https://grafana.com/grafana/dashboards/15454
