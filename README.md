# OpenShift Data Foundation - Multi Cloud Gateway (Noobaa) Only

A full installation of OpenShift Data Foundation deploys a full Ceph cluster as well as Noobaa.  This provides Block, File and Object storage.

However, sometimes all you need is object storage!  ODF has the option to only install the "Multi Cloud Gateway" component in this situation.  This is a lot of lighter on CPU and Memory as well.

First, install the ODF operator:

```
oc apply -k https://github.com/redhat-cop/gitops-catalog/openshift-data-foundation-operator/operator/overlays/stable-4.12
```

Once the operator has been installed, create the `StorageSystem` and `StorageCluster`:

```
oc apply -k instance/aws-gp3
```

Once Multi Cloud Gateway (Noobaa) has been deployed, you can try making a new `ObjectBucketClaim`.  There's an example in the `bucket-example` directory.