### This module is to create and apply the appropriate resources to enable the log collector FluentBit to forward logs from all pods to the Cloudwatch for analytics.



*Create cloudwatch namespace*
> kubectl apply -f cloudwatch-namespace.yaml

*Create configurations for FluentBit*
> kubectl apply -f ConfigMap.yaml

*Download and deploy the Fluent Bit daemonset to the cluster*
> kubectl apply -f fluent-bit.yaml

*To run all at once, run from the root of the project into your selected/active cluster.*
> kubectl apply -k base/fluent-bit

## Resources Created
- A service account named **Fluent-Bit** in the amazon-cloudwatch namespace. This service account is used to run the FluentCancel changes Bit daemonSet.

- A cluster role named **Fluent-Bit-role** in the amazon-cloudwatch namespace. This cluster role grants get, list, and watch permissions on pod logs to the Fluent-Bit service account.

- A ConfigMap named **Fluent-Bit-config** in the amazon-cloudwatch namespace. This ConfigMap contains the configuration to be used by Fluent Bit.

____________________________________________________________________________________________________________
### You will also need to add an IAM role with the :
*CloudWatchLogsFullAccess* <br />
###permissions (devhub-stage-eks-node-group) to each node, so they have access to cloudwatch.
____________________________________________________________________________________________________________
