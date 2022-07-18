### Install Pulumi
Pulumi is an open source infrastructure as code tool for creating, deploying, and managing cloud infrastructure. Pulumi works with traditional infrastructures like VMs, networks, and databases, in addition to modern architectures, including containers, Kubernetes clusters, and serverless functions.
```
$ curl -fsSL https://get.pulumi.com | sh
```

### Creating a Load Balanced ECS Service
To run a Docker container in ECS using default network and cluster settings, use the awsx.ecs.FargateService class. Since we need to access this container over port 80 using a stable address, we will use a load balancer.

Python code for creating ECS is in ecs/main.py. Give your details there:

```
cluster = aws.ecs.Cluster("<ecs_cluster_name>")

lb = awsx.lb.ApplicationLoadBalancer("<lb_name>")

service = awsx.ecs.FargateService("<service_name>",image="<image_name>")
```

### Running Pulumi
```
$ pulumi up
```
It will create all the resources that are needed.
