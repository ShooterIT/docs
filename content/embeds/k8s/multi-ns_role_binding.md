```yaml
kind: RoleBinding
apiVersion: rbac.authorization.k8s.io/v1
metadata:
  name: redb-role
  labels:
    app: redis-enterprise
subjects:
- kind: ServiceAccount
  name: redis-enterprise-operator
  namespace: NAMESPACE_OF_SERVICE_ACCOUNT
- kind: ServiceAccount
  name: NAME_OF_REC_SERVICE_ACCOUNT  # service account of the REC, usually the same as the name of the custom resource
  namespace: NAMESPACE_OF_SERVICE_ACCOUNT
roleRef:
  kind: Role
  name: redb-role
  apiGroup: rbac.authorization.k8s.io
```
