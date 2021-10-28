# operator-example-memcached
An example Kubernetes operator that creates a Memcached Deployment.  
The operator created with the `operator-sdk` tool.  
Based on [this guide](https://sdk.operatorframework.io/docs/building-operators/golang/tutorial/)

## Steps for creation
```
operator-sdk init --domain nati.com --repo github.com/example/memcached-operator
operator-sdk create api --group cache --version v1alpha1 --kind Memcached --resource --controller
```

Set the spec in the api/v1 types.go file and generate the CRD using `make` command:
```
make generate
make manifests
```

## Install the CRD
Install the CRD using `make` command:
```
make install
```

A sample file created in config/samples, you can use it to run your operator:
```
kubectl apply -f config/samples/cache_v1alpha1_memcached.yaml
```

## Check the CRD installed
You can get the installed CRDs using `kubectl` command:
```
kubectl get crd
```

## Running the operator
You can run the operator using `make` command:
```
make run
```

## Install the operator as a deployment
```
make deploy
```
