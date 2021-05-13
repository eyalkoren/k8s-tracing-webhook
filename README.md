# k8s-tracing-webhook
This webhook project is based on https://github.com/stackrox/admission-controller-webhook-demo

An implementation of k8s [admission control webhook](https://kubernetes.io/docs/reference/access-authn-authz/extensible-admission-controllers/#admission-webhooks), that enables atuomatic attachement of the Elastic APM Java agent to application pods. 
The registered MutatingAdmissionWebhook intercepts requests to the Kubernetes API server and executes the mutating admission control webhook prior to persistence of the object, but after the request is authenticated and authorized. This allows the mutation of the originally submitted request. 

![Screen Shot 2021-05-13 at 14 20 35](https://user-images.githubusercontent.com/41850454/118119053-71f2db00-b3f6-11eb-9d9e-bf3b26bd4dd5.png)

The mutation is done by applying [JSON patches](https://datatracker.ietf.org/doc/html/rfc6902).
