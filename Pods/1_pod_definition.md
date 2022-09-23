# POD

## Définition

Un pod est le plus petit objet que l'on peut rencontrer dans l'écosystème K8S. Un pod encapsule une instance d'un conteneur. Typiquement dans le cas d'un monté en charge, on dupliquera le nombre de pods et donc le nombre d'instance de notre application.

Un pod entretient une relation de 1 à 1 avec un conteneur dans lequel une instance d'un application est servie. On ne dupliquera pas de nouveaux conteneurs à l'intérieur d'un même POD ! Mais on pourrait ajouter dans ce même pod des conteneurs utilitaires.

## Yaml

Lorsqu'il s'agit de définir un pod avec un fichier YAML, un fichier comprend 4 parties :

```yaml
apiVersion: v1
kind: Pod
metadata:
  name: my-app-pod
  labels:
    app: my-app
    type: front-end
spec:
  containers:
    - name: nginx-container
      image: nginx
```

Ces 4 parties sont les toujours situés à la racine du fichier et sont toujours requises.

- **apiVersion**: Désigne la version de l'api de Kubernetes avec laquelle le fichier va travailler.
- **kind**: Le type d'entité que l'on tente de créer, ici un pod.
- **metadata**: Renseigne des informations concernant l'objet que l'on tente de créer, ici un pod.
- **spec**: Renseigne les informations concernant le nom et l'image du conteneur.

Cette commande permet de lancer le fichier : `kubectl create -f pod-definition.yaml`
