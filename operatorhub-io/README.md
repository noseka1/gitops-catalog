# OperatorHub.io

This makes the operators hosted at https://operatorhub.io/ available for installation via OLM. Why do we need this? Not all operators hosted on OperatorHub.io are available through the built-in OperatorHub in OpenShift. This kustomization makes all of the operators from OperatHub.io available along with the built-in OperatorHub operators.

## Usage

Deploy the OperatorHub.io catalog source:

```
$ oc apply -k operatorhub-io
```

After a while, operators hosted on OperatorHub.io will be available for installation using OLM:

```
$ oc get packagemanifest | grep OperatorHub.io
```

You can than install these operators easily, for example:

```
apiVersion: operators.coreos.com/v1alpha1
kind: Subscription
metadata:
  name: topolvm-operator
  namespace: openshift-operators
spec:
  source: operatorhub-io
  sourceNamespace: openshift-marketplace
  name: topolvm-operator
  channel: alpha
  installPlanApproval: Automatic
```
