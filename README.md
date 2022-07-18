
## Acknowledgement: 

The [internal repo](https://gitlab.eng.vmware.com/rvanvoorhees/kapp-controller-tap-install/) provided by Robert Van Voorhees already paved the way for using kapp to install all of TAP, including tenants. It was used as a spring board to prove out TAP tenant onboarding with version 1.1.

## Deploy command:
```
kapp deploy -n tap-install --yes -a tap-tenants -c \
-f <(ytt --ignore-unknown-comments -f app-onboarding.yml -f values.yml -f ./app-onboarding-secrets.yml)
```