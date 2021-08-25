# 01- TODO deploy kafka using

kubectl apply -f metrics/strimzi-kafka-metrics.yaml

# 02- TODO port forward Kafka Exporter

kubectl port-forward my-cluster-kafka-exporter-848748f6c5-ffjq6 9404:9404

# 03- Kafka Exporter metrics will be available at

curl http://localhost:9404/metrics|grep kafka_
