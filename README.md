# modern_app_jumpstart_workshop_infra
Supporting ArgoCD/Helm chart repo for the infrastructure components used in the [modern_app_jumpstart_workshop](https://github.com/f5devcentral/modern_app_jumpstart_workshop)


Requirements:

https://www.elastic.co/guide/en/cloud-on-k8s/current/k8s-deploy-eck.html

kubectl create -f https://download.elastic.co/downloads/eck/2.7.0/crds.yaml
kubectl apply -f https://download.elastic.co/downloads/eck/2.7.0/operator.yaml

#check latest version


Dashboard NAP:

https://github.com/f5devcentral/f5-waf-elk-dashboards




KIBANA_URL=https://XX.XX.XX.XX:5601

jq -s . kibana/overview-dashboard.ndjson | jq '{"objects": . }' | \
curl -k --location --request POST "$KIBANA_URL/api/kibana/dashboards/import" -u "elastic:xxxxxxxxx"\
    --header 'kbn-xsrf: true' \
    --header 'Content-Type: text/plain' -d @- \
    | jq


jq -s . kibana/false-positives-dashboards.ndjson | jq '{"objects": . }' | \
curl -k --location --request POST "$KIBANA_URL/api/kibana/dashboards/import" -u "elastic:xxxxxxxxx"\
    --header 'kbn-xsrf: true' \
    --header 'Content-Type: text/plain' -d @- \
    | jq

