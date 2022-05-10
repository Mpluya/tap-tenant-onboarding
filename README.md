
## Acknowledgement: 

The [internal repo](https://gitlab.eng.vmware.com/rvanvoorhees/kapp-controller-tap-install/) provided by Robert Van Voorhees already paved the way for using kapp to install all of TAP. I used that as a spring board to prove out TAP tenant onboarding using TAP 1.1

## Deploy command:
```
kapp deploy --yes -a tap-tenants -f <(ytt -f .)
```