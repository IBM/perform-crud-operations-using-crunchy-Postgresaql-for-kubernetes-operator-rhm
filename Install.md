# How to install & get started using the Crunchy Postgres operator on RedHat OpenShift cluster

In this tutorial, we demonstrate how to install and get started using the Crunchy Postgres operator operator from RedHat Marketplace (RHM). The advantages of using RHM operators are per below.  

* `Software for any cloud` :- Enterprise software for container-based environments in public clouds and on-prem

* `Automated deployment` :- Fast, integrated experience with instant availability on Red Hat® OpenShift® clusters

* `Fully supported` :- Free, continuous support for products purchased through Red Hat Marketplace

## A short brief about Crunchy Postgres operator operator

The postgres-operator is a controller that runs within a Kubernetes cluster that provides a means to deploy and manage PostgreSQL clusters.
Use the postgres-operator to:
- deploy PostgreSQL containers including streaming replication clusters
- scale up PostgreSQL clusters with extra replicas
- add pgpool, pgbouncer, and metrics sidecars to PostgreSQL clusters
- apply SQL policies to PostgreSQL clusters
- assign metadata tags to PostgreSQL clusters
- maintain PostgreSQL users and passwords
- perform minor upgrades to PostgreSQL clusters
- load simple CSV and JSON files into PostgreSQL clusters
- perform database backups


## Prerequisites

For all operators being installed from RHM, OpenShift cluster version 4.3 or higher is mandatory. Please set up Classic cluster using the instructions from below URL.

[Setting up OpenShift Cluster](https://cloud.ibm.com/docs/openshift?topic=openshift-getting-started)

## Next Step - Access the RedHat OpenShift Container Platform (Web Console)

Follow the steps below to launch the cluster console which is also called RedHat OpenShift Container Platform.

Login to IBM Cloud Account and navigate to Dashboard

![](doc/source/images/dashboard.png)

Click on Clusters and select the cluster which you have created under prerequisites. In our case, cluster name is cp-rhm-poc.

![](doc/source/images/cluster.png)

After you launch the cluster, click on OpenShift web console on the top right hand side.

![](doc/source/images/web-console.png)

We can see the RedHat OpenShift Container Platform (Web Console). Click on question mark ikon on the top right hand side and select Command Line Tools. 

![](doc/source/images/cmd-line-tools.png)

Navigate to the section `oc - OpenShift Command Line Interface (CLI)` and download the respective oc binary onto your local system. This is needed to manage OpenShift projects from a terminal and is further extended to natively support OpenShift Container Platform features.

![](doc/source/images/oc-binary.png)

We are all set to proceed to next step which is to register the OpenShift cluster on RedHat Marketplace platform. This is mandatory to install any operators from RedHat Marketplace platform using the OpenShift cluster.

## Register the cluster on RedHat Marketplace

Sign up and login to RHM portal at [Link](https://marketplace.redhat.com/en-us) and click on workspace and then click on cluster. We need to add our new OpenShift cluster and register it on RHM platform.

![](doc/source/images/add-cluster.png)

Update the cluster name, generate the pull secret as per the instructions and save it. 

![](doc/source/images/cluster-details.png)

Copy the curl command which starts with `curl -sL https` and append the pull secret towards the end. The entire script should be handy to be used in next step.

We need to start the cluster first to register it. Open a command prompt and type oc login, update the username and password which are used for accessing the cluster and hit enter. 

![](doc/source/images/start-cluster.png)

The cluster is up and running at this point. We need to run the entire script which is from previous step and hit enter. It will take a couple of mins and we can see that we have successfully registered the cluster on RHM portal.

![](doc/source/images/register-cluster.png)

## Create a project in web console

We need to create a project to be used and managed from command line. Click on Create Project and give a name as `crunchy-project`.

![](doc/source/images/create-project.png)

## Install the operator

Navigate to OpenShift web console which was launched during previous step. Select operatorhub under Operators and type 'Crunchy' in the search bar and hit 

![](doc/source/images/install-operator1.png)

Click on Crunchy Postgres Operator (non custom) and hit install.

![](doc/source/images/install.png)

Create Operator Subscription by choosing All namespaces or specific namespace (select default project crunchy-project) and hit subscribe.

![](doc/source/images/subscribe1.png)

After a couple of minutes, the operator gets installed on the cluster. We can verify by clicking on Installed Operators under `Operators` and see that the operator is successfully installed with status showing as Succeeded.

![](doc/source/images/installed-operator.png)


### This concludes, how to install and get started using the Crunchy Postgres operator on RedHat OpenShift cluster
