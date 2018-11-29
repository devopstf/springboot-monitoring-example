# Springboot demo application for Monitoring demo using Prometheus and Grafana

This simple demo has been forked from [ConSol Labs](https://labs.consol.de/development/2018/01/19/openshift_application_monitoring.html).
It has been deployed using OKD docker-based cluster launched via ``oc cluster up``

The only step that is not explicitly documented within the former linked blog post is the one for binding the ``system:auth-delegator`` with the ``prometheus`` service account. It has to be accomplished doing the following:

* ``oc login -u system:admin``
* ``oc adm policy add-cluster-role-to-user system:auth-delegator system:serviceaccount:prometheus:prometheus``

## Usage

If we summarize the demo steps you have to follow:

* Deploy the demo application.
* Deploy Prometheus within a separate project.
* Deploy Grafana within a separate project.
* Give Grafana service account view privileges for the ``prometheus``project.
* Set up Prometheus data source within Grafana.
* Update Prometheus' configuration file (via ConfigMap) for scraping our demo application.
* Update our demo application's Deployment Config for allowing Prometheus scraping.
* Import a sample dashboard to Grafana
* Enjoy!
