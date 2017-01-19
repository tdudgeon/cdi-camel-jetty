# CDI Camel Jetty QuickStart

This example shows how to work with Camel in the Java Container using CDI to configure components,
endpoints and beans.

This quickstart is the server side which embeds a Jetty HTTP server in a Camel route that
exposes a HTTP service.

The `cdi-camel-http` is the client to this quickstart that can be started which will call this
Jetty HTTP server every 5 second.


### Building

The example can be built with

    mvn clean install


### Running the example locally

The example can be run locally using the following Maven goal:

    mvn clean install exec:java

And you can access the HTTP service using a web browser on url:

    http://localhost:8080/camel/hello


### Running the example in fabric8

It is assumed a running Kubernetes platform is already running. If not you can find details how to [get started](http://fabric8.io/guide/getStarted/index.html).

The example can be built and deployed using a single goal:

    mvn fabric8:run

When the example runs in fabric8, you can use the OpenShift client tool to inspect the status

To list all the running pods:

    kubectl get pods

Then find the name of the pod that runs this quickstart, and output the logs from the running pods with:

    kubectl logs <name of pod>

The example exposes a service over HTTP which you can find using

    kubectl get routes

This lists all the routes to the services, where you can find the actual HTTP url, which you can use from a web browser.

The Camel route is listening on context-path `camel/hello`, so the actual HTTP url should be prefixed with that.

You can also use the fabric8 [web console](http://fabric8.io/guide/console.html) to manage the
running pods, and view logs and much more.


#### Integration Testing

The example includes a [fabric8 arquillian](https://github.com/fabric8io/fabric8/tree/master/components/fabric8-arquillian) Kubernetes Integration Test. 
Once the container image has been built and deployed in Kubernetes, the integration test can be run with:

	mvn test -Dtest=*KT

The test is disabled by default and has to be enabled using `-Dtest`. [Integration Testing](https://fabric8.io/guide/testing.html) and [Fabric8 Arquillian Extension](https://fabric8.io/guide/arquillian.html) provide more information on writing full fledged black box integration tests for Kubernetes. 

### More details

You can find more details about running this [quickstart](http://fabric8.io/guide/quickstarts/running.html) on the website. This also includes instructions how to change the Docker image user and registry.

