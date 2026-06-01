# elastic
## Stack montado
Squid Server → UDP :5000 → Logstash (grok SQUID3) → Elasticsearch → Kibana

## Archivos del proyecto
- docker-compose.yml	ELK stack (ES, Kibana, Logstash) con user: root y UDP 5000
- .env	Credenciales (elastic/elastic123, kibana_system/kibana123)
- elasticsearch.yml	Config ES + watermarks de disco para desarrollo
- logstash-squid.conf	Pipeline: input UDP 5000 → filter SQUID3 + geoip → output ES
- patterns/squid	Patrón SQUID3 para parsear logs nativos de Squid
- send_squid_to_elk.sh	Script en servidor Squid que lee access.log y envía por UDP
