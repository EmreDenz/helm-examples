To expose Harbor domain name to the address you want, you should edit vars.yaml in order to example below:
`harbor_domain_name: test.com`

To install Harbor registry and Keycloak, execute the command below:
`ansible-playbook helm.yaml`

> Harbor parameters in the helm.yaml file:
> expose.ingress.hosts.core={{ harbor_domain_name }} -> sets the URL to Harbor that you texted in the values.yaml file
> expose.ingress.hosts.notary={{ harbor_notary_domain_name }} -> sets the URL to Harbor Notary that you texted in the values.yaml file
> externalURL=http://{{ harbor_domain_name }} -> sets the URL to Harbor that you texted in the values.yaml file
> expose.tls.enabled=false -> this and the parameter below disables TLS.
> expose.ingress.annotations/ssl-redirect=false

To update domain name of Keycloak, execute the command below:

`ansible-playbook keycloak.yaml`

keycloak.yaml file consists of ingress definition about Keycloak.

To edit /etc/hosts file in order to access from local machine, execute the command below:

> Note: The command will ask your sudo password to edit /etc/hosts file.

`ansible-playbook add_hosts.yaml --ask-become-pass`
