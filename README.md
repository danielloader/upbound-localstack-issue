# Upbound Bucket Endpoint Reproduction

## Install Steps

These steps rely on your kubectl being set to the right context, in a disposable cluster, and the fluxcd CLI installed and available in the $PATH.

1. `flux install --namespace=flux-system --network-policy=false --components=source-controller,helm-controller`
1. `kubectl apply -f packages.yaml`
1. `kubectl apply -f credentials.yaml`
1. `kubectl apply -f providers.yaml`
1. `kubectl apply -f upbound/`
1. `kubectl apply -f community/`

## Post Install Checks

1. Events log for both bucket types (upbound and community).
1. Exec into localstack pod and run `awslocal s3 ls` to list buckets.

