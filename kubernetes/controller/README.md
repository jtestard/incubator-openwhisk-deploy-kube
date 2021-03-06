<!--
#
# Licensed to the Apache Software Foundation (ASF) under one or more
# contributor license agreements.  See the NOTICE file distributed with
# this work for additional information regarding copyright ownership.
# The ASF licenses this file to You under the Apache License, Version 2.0
# (the "License"); you may not use this file except in compliance with
# the License.  You may obtain a copy of the License at
#
#     http://www.apache.org/licenses/LICENSE-2.0
#
# Unless required by applicable law or agreed to in writing, software
# distributed under the License is distributed on an "AS IS" BASIS,
# WITHOUT WARRANTIES OR CONDITIONS OF ANY KIND, either express or implied.
# See the License for the specific language governing permissions and
# limitations under the License.
#
-->

Controller
----------

# Deploying

## Create config map

Edit controller.env as needed to set the appropriate values for your
deployment, then create the configmap controller.config:

```
kubectl -n openwhisk create cm controller.config --from-env-file=controller.env
```

## Deploy Controller

The Controller is deployed as a [StatefulSet][StatefulSet] because
each instance needs to know which index it is and we need stable pod
names to support Akka clustering. The Controller can be deployed with:

```
kubectl apply -f controller.yml
```

# Controller Deployment Changes
## Changing the Controller Count

By default, only a single controller is deployed (HA disabled).

Changing the number of controllers and/or enabling HA currently requires a complete
redeployment of the controller stateful set. You will need to update
the number of replicas
[here](https://github.com/apache/incubator-openwhisk-deploy-kube/tree/master/kubernetes/controller/controller.yml#L10)
and the values of the various variables for controller HA and Akka
clustering
[here](https://github.com/apache/incubator-openwhisk-deploy-kube/tree/master/kubernetes/controller/controller.yml#L30-L39)
and then redeploy.

[StatefulSet]: https://kubernetes.io/docs/concepts/workloads/controllers/statefulset/
