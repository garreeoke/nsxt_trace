# NSX-T Trace #
Use for tracing between containers in a PKS/K8s environment

* This is my personal tool, not supported by VMware.

### Run on a linux box ###

* Download the latest nsxt-trace binary from [github release page](https://github.com/garreeoke/nsxt_trace/releases)
* chmod +x nsxt-trace
* mv nsxt-trace /usr/local/bin (or somewhere in PATH)

### Arguments ###

_Required_
* --nsx
    * ip/fqdn of NSX Manager
    * Can set NSX_MANAGER env variable as an alternative
* --nsx-pass
    * password for NSX user
    * Set NSX_PASS env variable as an alternative
* --pks-uid
    * uid of the k8s cluster in PKS
    * get this info by running pks clusters or within NSX by looking at pks-### where ### is uid from PKS.
* --namespace
    * kubernetes namespace where pods live
* --src-pod
    * name of the source pod
* --src-port
    * port of the source pod
* --dst-pod
    * name of the destination pod
* --dst-port
    * port of the destination pod
    
_Optional_
* --nsx-user
    * user for nsx manager, admin is default
    * Set NSX_USER env variable as an alternative
* --dst-namespace
    * specify a different namespace for the destination
* --payload
    * send a text payload
    
### Examples ###

* nsxt_trace --nsx-ip=10.173.61.44 --nsx-user=admin --nsx-pass=VMware1! --pks-uid=7976bc34-53e2-4031-aad3-cdfe99c6f3be --namespace=acme-air --src-pod=acme-web-c6bbf95d5-wlrwf --src-port=8080 --dst-pod=mongodb-0 --dst-port=27017
* nsxt_trace --nsx-ip=10.173.61.44 --nsx-user=admin --nsx-pass=VMware1! --pks-uid=7976bc34-53e2-4031-aad3-cdfe99c6f3be --namespace=acme-air --src-pod=acme-web-c6bbf95d5-wlrwf --src-port=8080 --dst-pod=mongodb-0 --dst-port=27017 --dst-namespace=acme-air2