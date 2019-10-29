# Local Debugging Environment
First to export several key env variables
```
export ALIYUN_ACCESS_ID=xxx
export ALIYUN_ACCESS_SECRET=xxx
export ALIYUN_REGION=cn-hangzhou
```

And then use `helmfile` to apply,
```
helmfile apply
```

> Before to make this happen yor are asked for having `Docker for Mac` in place and also ensure you have already enabled the kubernetes..

# Grafana
Visit http://localhost/ to open Grafana, By default, the Grafana admin account is,
- `Username: admin`
- `Password: prom-operator`