
## Acknowledgement: 

The [internal repo](https://gitlab.eng.vmware.com/rvanvoorhees/kapp-controller-tap-install/) provided by Robert Van Voorhees already paved the way for using kapp to install all of TAP, including tenants. It was used as a spring board to prove out TAP tenant onboarding with version 1.2.

## Deploy command:
```
kapp deploy -n tap-install --yes -a tap-tenants -c \
-f <(ytt --ignore-unknown-comments -f app-onboarding.yml -f values.yml -f ./app-onboarding-secrets-sealed.yml)
```

Note: app-onboarding-secrets-sealed.yml is a result of running the command below. Automatic decryption happens in the intended cluster, where kubeseal controller is running:
```
k create secret generic app-onboarding-secrets -n tap-install --from-file=app-onboarding-secret-values.yaml=secrets.yml --dry-run=client -oyaml | kubeseal --cert **path-to-pem=file**/kubeseal-cert.pem > app-onboarding-secrets-sealed.yml
```