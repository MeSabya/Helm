# How To Get Started with HELM

## Understanding Helm’s Architecture
Helm’s mainly focuses on three things when you are managing applications in the cluster.

**Security**: Helm makes sure that the package comes from a trusted source and the security of the network it is pulled from, etc.

**Reusability**: We can install the same thing again and again into the cluster or namespace in a cluster. We can do it repeatedly and predictably.

**Configurability**: We can externalize the configuration and pass it while installing the repository into the cluster. Even though Helm is not a configuration management tool but still provides some configuration.

## Helm concepts
**Chart**: is a package in Helm. It has a name, and contains a set of Kubernetes resource definitions that are used to deploy your application.

**Repository**: is an online collection of charts. It has a URL. You can search, download and install charts from a repository.

**Release**: is an instance or a deployment of a chart. When you perform a helm install command, you are creating a new release of that chart on your Kubernetes cluster.

### Charts

A Chart in a Helm is nothing but a packaged version of your application. A chart is a set of files and directories that follows some specification for describing the resources to be installed into Kubernetes.
A chart contains Chart.yaml that provides the information about the chart version, name, description, etc. All the Kubernetes manifest files are under the templates folder. You can pass the configuration with the Values.yaml file. This file contains parameters that you can override during installation and upgrade.
Let’s create a chart with the following command and understand the structure.

                        helm create dummy-chart
                        
![image](https://user-images.githubusercontent.com/33947539/155517153-21706f6d-3571-44bc-8556-11a1eedaf0b7.png)

It created the tests as well where you can test the deployments. You can see different manifest files such as deployment, hpa, ingress, etc under the templates folder.
👉 Let’s see what happens when the Helm chart is installed into Kubernetes.

- Helm reads the chart
- It reads the configuration values from the Values.yml and generates the manifest files with these values.
- Helm sends these generated manifests to the Kubernetes API server
- Kubernetes takes these manifest files and creates desired resources in the cluster.

## Working with Kubernetes Cluster
Helm interacts with the Kubernetes API server to deploy objects. But, before that, we need Helm to connect to Kubernetes Cluster. If you have a Kubectl installed already on your machine and the Helm uses the same configuration used by Kubectl automatically unless you specifically mention otherwise.
You can view the Kube config file with the following command

          cat /users/bhargavbachina/.kube/config

You can view all the clusters and get the current context with the following commands.

          // view all clusters
          kubectl config get-clusters
          // get the current context
          kubectl config current-context
          
As you can see above, Helm uses the same configuration by default that kubectl uses and you can change it by exposing the environment variable either $KUBECONFIG or HELM_KUBECONTEXT.

We can create a package using helm , then we can install it.

        helm package dummy-chart/
        helm install release1 dummy-chart-0.1.0.tgz

## References:
https://www.tutorialworks.com/helm-cheatsheet/

https://medium.com/bb-tutorials-and-thoughts/how-to-get-started-with-helm-b3babb30611f
