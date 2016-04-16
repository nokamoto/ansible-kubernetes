# ansible-kubernetes

[![Build Status](https://travis-ci.org/nokamoto/ansible-kubernetes.svg?branch=master)](https://travis-ci.org/nokamoto/ansible-kubernetes)

## vagrant
```
vagrant up
ssh -i keys/local admin@192.168.33.11
```

| node | ip |
| --- | --- |
| node1 | 192.168.33.11 |
| node2 | 192.168.33.12 |
| node3 | 192.168.33.13 |


### RabbitMQ Cluster
```
ssh -i keys/local admin@192.168.33.11
kubectl exec rabbitmq-two -- rabbitmqctl stop_app
kubectl exec rabbitmq-two -- rabbitmqctl join_cluster rabbit@rabbitmq-svc
kubectl exec rabbitmq-two -- rabbitmqctl start_app
```
