# Provision On demand environments

This repo contains set of Github actions workflows to provision Hello world environments on GCP GKE clusters based on developers sprints 

## create_env.yml

It contains three main jobs:

- checkup: which make sure that the naming convention of namespace is valid and doesn't contains special characters or already created before.

- setup: this job does a set of actions as below:
    - Auth to GCP project.
    - Auth Docker registry.
    - Auth to GKE cluster.
    - Setup helm and all neeed plugins (helm-gcs, sops, helm-secrets)
    - Create the namespace.
    - Deploy your version of hello world to the namespace.

- slack: it notifies the slack channel with the creation event

## remove_env.yml

This job deletes the hello world provided namespace and all the corresponding components.

## scale_env.yml

This job scales up/down the corresponding enviornment provided by namespace name.