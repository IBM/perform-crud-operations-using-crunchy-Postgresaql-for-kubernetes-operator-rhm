---
#Front matter (metadata).

authors:
 - name: "Rahul Reddy Ravipally"
   email: "raravi86@in.ibm.com"
 - name: "Manoj Jahgirdar"
   email: "manoj.jahgirdar@in.ibm.com"
 - name: "Srikanth Manne"
   email: "srikanth.manne@in.ibm.com"
 - name: "Manjula G. Hosurmath"
   email: "mhosurma@in.ibm.com"

completed_date: "2020-09-30"
last_updated:  "2020-09-30"

components:
- slug: "Crunchy PostgreSQL for Kubernetes"
  name: "Crunchy PostgreSQL for Kubernetes"
  url: "https://marketplace.redhat.com/en-us/products/crunchy-postgresql-for-kubernetes"
  type: "component"
- slug: "redhat-marketplace"
  name: "Red Hat Marketplace"
  url: "https://marketplace.redhat.com/"
  type: "component"

draft: true|false       # REQUIRED

excerpt:                # REQUIRED
abstract:               # REQUIRED
keywords:               # REQUIRED - comma separated list

primary_tag: databases

related_content:        # OPTIONAL - Note: zero or more related content
  - type: announcements|articles|blogs|patterns|series|tutorials|videos
    slug:

related_links:           # OPTIONAL - Note: zero or more related links
  - title: "Crunchy PostgreSQL for Kubernetes"
    url: "https://marketplace.redhat.com/en-us/products/crunchy-postgresql-for-kubernetes"
    # description:
  - title: "Red Hat Marketplace"
    url: ""
    # description: 

tags:
 - "databases"
 - "containers"

title: Perform CRUD operations using Crunchy PostgreSQL for Kubernetes
subtitle: Perform CRUD operations using Crunchy PostgreSQL for Kubernetes on Red Hat Marketplace
meta_title: Perform CRUD operations using Crunchy PostgreSQL for Kubernetes

---

# Perform CRUD operations using Crunchy PostgreSQL for Kubernetes Operator on Red Hat Marketplace

In this tutorial, we demonstrate how to install and get started using the Crunchy Postgres operator from RedHat Marketplace (RHM). Also, learn how to perform CRUD operations using the Crunchy PostgreSQL for Kubernetes operator hosted on Red Hat marketplace using a Python runtime and Jupyter notebook.

# About Crunchy PostgreSQL for Kubernetes Operator

Crunchy PostgreSQL for OpenShift Container Platform (OCP) includes Crunchy PostgreSQL Operator and Crunchy PostgreSQL Container Suite supporting hybrid cloud, open source PostgreSQL-as-a-Service. [Learn more](https://marketplace.redhat.com/en-us/products/crunchy-postgresql-for-kubernetes).

The PostgreSQL-operator is a controller that runs within a Kubernetes cluster that provides a means to deploy and manage PostgreSQL clusters.

Use the PostgreSQL operator to:
- deploy PostgreSQL containers including streaming replication clusters
- scale up PostgreSQL clusters with extra replicas
- add pgpool, pgbouncer, and metrics sidecars to PostgreSQL clusters
- apply SQL policies to PostgreSQL clusters
- assign metadata tags to PostgreSQL clusters
- maintain PostgreSQL users and passwords
- perform minor upgrades to PostgreSQL clusters
- load simple CSV and JSON files into PostgreSQL clusters
- perform database backups

# Learning objectives

When you have completed this tutorial, you will understand how to:

* Deploy a CrunchyDB Operator on OpenShift Cluster
* Create a CrunchyDB cluster and database
* Access the cluster on your localhost
* Perform Create, Read, Update and Delete Operations on CrunchyDB

# Estimated time

Completing this tutorial should take about 30 minutes.

# Prerequisites

To complete the steps in this tutorial, you will need:

1. A [Red Hat Marketplace Account](https://marketplace.redhat.com/en-us/registration/om)
2. A [Red Hat OpenShift Cluster](https://cloud.ibm.com/kubernetes/catalog/create?platformType=openshift). Operators from the Red Hat Marketplace, requore an OpenShift cluster version 4.3 or higher. [Set up a classic cluster](https://cloud.ibm.com/docs/openshift?topic=openshift-getting-started).
3. [OpenShift container & kubectl CLI](https://docs.openshift.com/container-platform/3.6/cli_reference/get_started_cli.html)
4. Access to a Jupyter Notebook. You can [install a Jupyter Notebook from python-pip](https://jupyter.org/install) or use a tool such as [Anaconda](https://www.anaconda.com/products/individual) to open the Jupyter Notebook

# Steps

### Step 1: Install the CrunchyDB Operator from Red Hat Marketplace on OpenShift Cluster

You need to complete the steps in this tutorial to deploy a CruchyDB Operator from Red Hat Marketplace on a OpenShift Cluster:
  - [Steps to Deploy CrunchyDB Operator](https://github.com/IBM/rhm-crunchydb-operator-install-steps)
  
### Step 2: Perform CRUD operations on CrunchyDB using Python

Once you have the CrunchyDB Operator up and running and you've created a user and database, you can now explore the CRUD operations on Crunchy PostgreSQL in a Python runtime using a Jupyter Notebook.

1. In your terminal, run the following command to port forward the `5432` port from the OpenShift cluster. This port is used in our Jupyter Notebook to establish a connection with the Crunchy PostgreSQL instance.

    ```bash
    $ kubectl port-forward -n pgo svc/hippo 5432:5432 
    ```

    ```
    Forwarding from 127.0.0.1:5432 -> 5432
    Forwarding from [::1]:5432 -> 5432
    ```

1. Download and open the Jupyter notebook [CrunchyDB CRUD Operations.ipynb](CrunchyDB%20CRUD%20Operations.ipynb) on your local machine.

1. Click on the **Cell** tab and select **Run All**.

    ![](doc/source/images/run.png)

    You can now follow the notebook instructions for more details on what is happening in each cell.

1. After you execute the Jupyter notebook, you can verify the table in the pgAdmin 4 console. To access pgAdmin 4, you can set up a `port-forward` to the service<!--EM: What service? And what is pgAdmin 4??-->, which follows the pattern `<clusterName>-pgadmin`, to port `5050`:

    ```bash
    $ kubectl port-forward -n pgo svc/hippo-pgadmin 5050:5050 
    ```
    
    ```
    Forwarding from 127.0.0.1:5050 -> 5050
    Forwarding from [::1]:5050 -> 5050
    ```

1. In the pgAdmin 4 console, expand the following attributes:
    
    * your `cluster` &mdash; for example, in our case ,`cpdemo`
    * `Databases`
    * `database_name`
    * `Schemas`
    * `username` (eg: in our case `hippo`)
    * `Tables` 
    
    Under Tables, you can now see the `accounts` table that we created from the notebook. Right click on the `accounts` table and select **View/Edit Data > All Rows**, and the table with all rows will be displayed.

    ![](doc/source/images/view.png)

    >NOTE: You can view this table after each CRUD operation performed in notebook in order to visualize the changes.

    ![](doc/source/images/results.png) 

# Summary

In this tutorial, you have learned the basics of how to use the Crunchy PostgreSQL for Kubernetes operator deployed on OpenShift Cluster and walked through a quick exercise of how to perform CRUD operations using the Crunchy PostgreSQL for Kubernetes operator in Python.

# Reference

The documentation for [Crunchy PostgreSQL Operator](https://access.crunchydata.com/) is available at,

  - https://access.crunchydata.com/documentation/postgres-operator/latest/

