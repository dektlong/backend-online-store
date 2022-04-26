# Introduction
An Accelerator to create API-driven backend with Spring Boot.

The service should expose well defined API routes.

## Deploy the workload

```
tanzu apps workload create -f config/tap/workload.yaml -n YOUR_TAP_DEV_NS
```

## Track progess

```
tanzu apps cluster-supply-chain list

tanzu apps workload get mood-sensors -n YOUR_TAP_DEV_NS

kubectl tree workload mood-sensors -n YOUR_TAP_DEV_NS

kubectl describe imagescan.scanning.apps.tanzu.vmware.com/sensors -n YOUR_TAP_DEV_NS

tanzu apps workload tail mood-sensors --since 100m --timestamp  -n YOUR_TAP_DEV_NS

kc get ServiceBinding -n YOUR_TAP_DEV_NS
```

## Setup

- install TAP with ```full profile``` 
- Install the rabbitmq operator 
```
kapp -y deploy --app rmq-operator --file https://github.com/rabbitmq/cluster-operator/releases/download/v1.9.0/cluster-operator.yml
```

### Register workload entity in TAP GUI
```
config/tap/component.yaml
```
