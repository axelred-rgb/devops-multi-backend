# DevOps Multi-Backend Platform (Docker Swarm + Monitoring)

## Présentation

Cette infrastructure DevOps simule un environnement distribué à l’aide de Vagrant et Docker Swarm. Elle intègre une architecture complète avec plusieurs nœuds, chacun ayant un rôle précis : une API Python Flask en backend, une interface utilisateur React en frontend, une base de données MySQL, et des outils de supervision modernes (Grafana, Prometheus, cAdvisor).

## Architecture

* **manager1** : nœud principal Swarm et déploiement centralisé, héberge aussi certains services de monitoring
* **worker1** : exécute l’API backend en Python Flask
* **worker3** : dédié au monitoring (Grafana, Prometheus, cAdvisor)
* **worker4** : héberge l’application frontend React

## Technologies

* Vagrant + VirtualBox
* Docker & Docker Swarm
* Flask (Python)
* React
* MySQL
* Grafana, Prometheus, cAdvisor

## Démarrage

```bash
git clone https://github.com/axelred-rgb/nom-du-repo.git
cd nom-du-repo
vagrant up
```

## Accès aux services

| Service     | URL                                                                |
| ----------- | ------------------------------------------------------------------ |
| Backend API | [http://localhost:5010/api/hello](http://localhost:5010/api/hello) |
| Frontend    | [http://localhost:3005](http://localhost:3005)                     |
| Grafana     | [http://localhost:3006](http://localhost:3006)                     |
| Prometheus  | [http://localhost:9090](http://localhost:9090)                     |
| cAdvisor    | [http://localhost:8080](http://localhost:8080)                     |

## Déploiement des stacks

```bash
# Depuis manager1
docker stack deploy -c stack.yml monapp
docker stack deploy -c stack-monitoring.yml monitoring
```

## Retour d’expérience

Ce projet a été une véritable immersion dans le déploiement d’une plateforme distribuée moderne. Il m’a permis de :

* Comprendre la logique de création et d’orchestration de services multi-conteneurs avec Docker Swarm
* Maîtriser l’intégration de plusieurs composants applicatifs dans un environnement distribué
* Déployer des outils de supervision et visualisation (Grafana, Prometheus) sur des nœuds dédiés
* Utiliser Vagrant pour provisionner rapidement un cluster local reproductible
* Résoudre de manière pratique des problèmes courants liés aux ports, à la persistance des données et à la mise en réseau entre services

Ce type d’exercice concret m’a beaucoup appris sur l’aspect opérationnel du DevOps et m’a donné envie d’aller plus loin avec Kubernetes, CI/CD, et l’automatisation complète via Terraform et Ansible.

