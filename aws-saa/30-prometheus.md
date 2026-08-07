## amazon managed service for prometheus
1. serverless prometheus-compatible svc for monitoring container metrics.
2. let aws manage auto scaling.
3. PromQL query lang
4. data is stored in workspace for 150 days.

## aws managed grafana
1. fully managed grafana aws svc.
2. data visualization for instantly querying, correlating, visualizing metrics, logs, traces from diff sources.
3. workspaces (logical grafana servers) allow for separation of data viz and querying.
4. integrates with cw, aws prometheus, aws opensearch svc
5. use cases
   1. eks
   2. ecs
   3. kubernetes
   4. iot - monitoring iot and edge device data
   5. troubleshooting - centralize dashboards