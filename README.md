# OPA Test - TJ's test notes for OPA policy

## Task

 Styra Technical Exercise
Microservice Authorization with OPA and Envoy
Congratulations on reaching this stage in the Styra interview process! As a next step, we invite you to complete a technical exercise. This exercise has two goals:
1. Expose you to the Open Policy Agent and how it works with Envoy, to help you judge your own interest in this role and the technologies involved, and;
2. Help the Styra team understand how you approach problems, how you present solutions, and how you engage professionally.

Exercise

The Open Policy Agent website includes a tutorial on using OPA for microservices authorization with Envoy (link below). Please work through that tutorial, keeping detailed notes about what you did, what challenges you faced, and how you tried to solve them.
* https://www.openpolicyagent.org/docs/latest/envoy-tutorial-standalone-envoy/ 

Once you have completed the tutorial, please update the policy to enforce the following:
* Allow a user role associated with the “delete” permission the ability to delete a person
Please create Rego Tests for the policy as well.
Hints:
* Review the Go code for the sample application (linked from within the tutorial) to
understand the API endpoint that can be called to delete a person
* The “policy.rego” file in the tutorial contains an icon   to open the policy in the Rego
Playground.
* You should create a data structure (i.e. a Rego Object) to define a “role to permission” mapping that assigns the “delete” permission to a role. You can use the “admin” role for the specific “delete” permission assignment, however your assignment mapping should allow for multiple (or alternate) role definitions and multiple (or alternate) permissions to be associated. Your Rego policy rule will use the data from the Rego object in the rule expressions, therefore the rule behavior will be able to be modified by updating the data in the object, rather than the rule expressions.
      
Output

As output, please write up your process, results, and any other thoughts you consider relevant. Also, please be sure to include the policy code and tests for the additional policy.


## Process

Setup

* Docker installation
https://docs.docker.com/docker-for-mac/install/
* Install OPA 
```
curl -L -o opa \
https://openpolicyagent.org/downloads/latest/opa_darwin_amd64; \
chmod 755 ./opa
```
* Run OPA Playground policy
```
./opa run --server \
--log-format text \
--set decision_logs.console=true \
--set bundles.play.polling.min_delay_seconds=5 \
--set bundles.play.polling.max_delay_seconds=10 \
--set services.play.url=https://play.openpolicyagent.org \
--set bundles.play.resource=bundles/9WnO8Siyaw
```
* Error

pod error CrashLoopBackOff 




## Troubleshoot commands
```

kubectl get pods
kubectl describe pod 
kubectl get deployment
kubectl delete deployment ..........
kubectl get events
kubectl get nodes
kubectl cluster-info dump
k9s -c pod
```
## Notes

brew install k9s
brew install yamllint




```
test Deployment
kubectl apply -f test-deployment.yaml
test with kubectl port-forward svc/http-echo 8080:5678
 visit http://localhost:8080
```

```
	brew install kube-score/tap/kube-score
    kube-score score deployment.yaml
```
   
    result
```
    Container has the same readiness and liveness probe
            Using the same probe for liveness and readiness is very likely dangerous. Generally it's better to avoid the livenessProbe than re-using the readinessProbe.
            More information: https://github.com/zegl/kube-score/blob/master/README_PROBES.md
```

