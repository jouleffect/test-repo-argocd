# Esempio Repository Git per ArgoCD

Questo è un esempio di repository Git contenente manifesti Kubernetes che possono essere distribuiti utilizzando ArgoCD.

## Struttura del Repository

- `manifests/`: Contiene i file YAML dei manifesti Kubernetes per l'applicazione.
  - `deployment.yaml`: Definisce il Deployment per l'applicazione (es. Nginx).
  - `service.yaml`: Definisce il Service per esporre l'applicazione.
  - `configmap.yaml`: Definisce un ConfigMap per configurazioni aggiuntive.

## Come utilizzare con ArgoCD

1. Clona questo repository in un repository Git accessibile da ArgoCD.
2. Crea un'Application ArgoCD che punti a questo repository e alla cartella `manifests/`.
3. ArgoCD sincronizzerà automaticamente i manifesti nel cluster Kubernetes.

Esempio di Application ArgoCD:

```yaml
apiVersion: argoproj.io/v1alpha1
kind: Application
metadata:
  name: esempio-app
  namespace: argocd
spec:
  project: default
  source:
    repoURL: https://github.com/tuo-username/esempio-repo-argocd
    targetRevision: HEAD
    path: manifests
  destination:
    server: https://kubernetes.default.svc
    namespace: default
  syncPolicy:
    automated:
      prune: true
      selfHeal: true
```

Questo repository rappresenta lo stato desiderato (Target State) che ArgoCD confronterà con lo stato live del cluster.</content>
<parameter name="filePath">c:\Users\gmaraventano\Desktop\Formazione\ArgoCD\esempio-repo-argocd\README.md