# HPE Ezmeral

A product brand from [HPE](https://www.hpe.com/us/en/software.html)

The HPE Ezmeral software portfolio includes:

 * HPE Ezmeral Runtime Enterprise

    A unified container software platform built upon open source [kubernetes](./kubernetes.md)
    Designed for both cloud-native applications and non-cloud-native applications running on infrastructure either on-prem, or multiple public clouds, hybrid model or at the edge.

 * HPE Ezmeral Data Fabric

    Simplifies data management by unifying any data type from a wide variety of technologies into a single database.

 * HPE Ezmeral ML Ops

    Support to every stage of ML workflows: from sandbox experimentation with choice of ML/DL frameworks to model training on containerized distributed clusters, to deploying and tracking models in production.


For context it's worth mentioning other HPE products

**HPE GreenLake** a portfolio of cloud and as-a-service solutions. Delivers cloud experience wherever your apps and datav live - edge, data centre, colos and public clouds.

See HPE link above for other products and services.

## Finding Documentation

The HPE website is very hard to navigate to find what you want

Here's some links to what I think are the main documentation bits of relevance:

* HPE Ezmeral Container Platform 5.4 Documentation - [here](https://support.hpe.com/hpesc/public/docDisplay?docId=a00116774en_us&docLocale=en_US&page=reference/HPE_Ezmeral_Container_Platform.html). This is the landing page for docs. More sepcific useful links from there are:

  * [Universal concepts](https://support.hpe.com/hpesc/public/docDisplay?docId=a00116774en_us&page=reference/universal-concepts/Universal_Concepts_Overview.html)
  * [Navigating the GUI](https://support.hpe.com/hpesc/public/docDisplay?docId=a00116774en_us&page=reference/navigating-the-interface/Screen_Layout.html)

  * [DataTaps](https://support.hpe.com/hpesc/public/docDisplay?docId=a00116774en_us&page=reference/kubernetes/using-kubernetes/general-functionality/datataps/The_DataTaps_Screen.html)
  
   Note the types of DataTap a Tenant Admin can make available:
    
     * HDFS - Hadoop Distributed File System
    
     * MapR - was a business software in US, s/w provides access to variety of data sources, from a single compute cluster including big data workloads such as Apache Hadoop, Apache Spark, a distributed filesystem, a multi-model db management system and event stream processing. Used by AWS in their Elastic Map Reduce service.

     * NFS - option not available for K8s tenants

    GCS - Google Cloud Storage

  * [FSMounts](https://support.hpe.com/hpesc/public/docDisplay?docId=a00116774en_us&page=reference/kubernetes/using-kubernetes/general-functionality/fs-mounts/The_FS_Mounts_Screen.html) This may not be vailable within k8s cluster.

  * [Kubernetes Applications](https://support.hpe.com/hpesc/public/docDisplay?docId=a00116774en_us&page=reference/kubernetes-applications/general/The_Kubernetes_Applications_Screen.html) The main application window to select e.g. Jupyter Notebook

  * [Apache Spark](https://www.hpe.com/us/en/what-is/spark.html) See also [Spark](./spark.md)

  * [Livy](https://support.hpe.com/hpesc/public/docDisplay?docId=a00ecp54hen_us&page=reference/kubernetes-applications/spark/Livy_Overview.html) An HTTP server that allows you to:
   
      * Launch Spark applications

      * Submit code statements using the REST API 

   Under tho hood I think it's a wrap for [Apache Livy](https://livy.incubator.apache.org/). The main point being anyone can now interact with your Spark cluster without needing to have the Spark client installed.

  * [Magic Functions](https://support.hpe.com/hpesc/public/docDisplay?docId=a00ecp54hen_us&docLocale=en_US&page=reference/kubernetes/using-kubernetes/ai-ml-functionality/notebooks/Kubernetes_Notebook_Magic_Functions.html) - note the `%<magic-func>?` tells you about the magic-func and `%lsmagic` lists them.


---
## Miscellaneous Topics

  * See [KServe](./kubeflow.md#kubeflow-components) - serverless inferencing.