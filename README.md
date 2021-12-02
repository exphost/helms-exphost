# exphost

v1.5.0
  ACTION REQUIRED:
    - need to add random key to password, so the template rendere could add ownerReference
      kubectl --context=exphost_dev-k8s-dev.exphost.pl-cluster get secret -l creator=password-generator  -A
      ex. patch:
      kubectl --context=exphost_dev-k8s-dev.exphost.pl-cluster -n tenant-exphost-services patch secret password-password-postfix-from-tenant-exphost-services --patch="{\"data\":{\"test\":\"YWE=\"}}" --type=merge
      or:
      for i in $(kubectl --context=exphost_dev-k8s-dev.exphost.pl-cluster -n tenant-exphost-services get secret -l creator=password-generator  -A -o name); do  kubectl --context=exphost_dev-k8s-dev.exphost.pl-cluster -n tenant-exphost-services patch $i --patch="{\"data\":{\"test\":\"YWE=\"}}" --type=merge; done

