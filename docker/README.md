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

This directory contains the Dockerfiles and other artifacts to
build specialized docker images for deploying OpenWhisk to Kubernetes.

These images are built automatically and published
to DockerHub under the openwhisk userid.  Docker images are
published on all successful Travis CI builds of the master branch.
The built images are:
  * couchdb - creates and initializes a CouchDB instance for
    dev/testing of OpenWhisk.  This image is not intended for
    production usage.
  * docker-pull - performs a 'docker pull' for action runtimes
    specified in runtimesManifest format -- used to prefetch
    action runtime images for invoker nodes
  * invoker-agent - worker node invoker agent -- used to implement
    suspend/resume and log consolidation ops for a remote invoker
  * openwhisk-catalog - installs the catalog from the project
    incubator-openwhisk-calalog to the system namespace of the
    OpenWhisk deployment.
  * routemgmt - installs OpenWhisk's route management package
    in the system namespace of the OpenWhisk deployment.
