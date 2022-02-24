# How To Get Started with HELM

## Understanding Helm’s Architecture
Helm’s mainly focuses on three things when you are managing applications in the cluster.

**Security**: Helm makes sure that the package comes from a trusted source and the security of the network it is pulled from, etc.

**Reusability**: We can install the same thing again and again into the cluster or namespace in a cluster. We can do it repeatedly and predictably.

**Configurability**: We can externalize the configuration and pass it while installing the repository into the cluster. Even though Helm is not a configuration management tool but still provides some configuration.

## Charts

A Chart in a Helm is nothing but a packaged version of your application. A chart is a set of files and directories that follows some specification for describing the resources to be installed into Kubernetes.
A chart contains Chart.yaml that provides the information about the chart version, name, description, etc. All the Kubernetes manifest files are under the templates folder. You can pass the configuration with the Values.yaml file. This file contains parameters that you can override during installation and upgrade.
Let’s create a chart with the following command and understand the structure.

                        helm create dummy-chart
                        
