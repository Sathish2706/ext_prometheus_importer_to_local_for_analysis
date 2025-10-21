1) Use promtool to usedump prometheus metrics

promtool tsdb dump-openmetrics \
            --min-time=$MIN_MS \
            --max-time=$MAX_MS \
            '/var/lib/prometheus' > /tmp/export.om"


2) Import to new PVC using prometheus import pod
2a) Ensure to run as root user
2b) Copy the export.om manually if needed #for issues in copy by importer pod

3) Create destination prometheus statefulset referencing imported prometheus PVC along with prometheus configmap

4) Create Grafana with this newly created destination prometheus URL as source
