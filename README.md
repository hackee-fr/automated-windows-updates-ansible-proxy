# Ansible Playbook pour la mise à jour de Windows avec Proxy

Ce dépôt contient deux fichiers essentiels pour l'automatisation de la mise à jour des systèmes Windows à l'aide d'Ansible. Le playbook configure un proxy temporaire pour accéder à Internet, effectue les mises à jour critiques et de sécurité de Windows, puis désactive le proxy une fois la mise à jour terminée.

## Fichiers

### 1. ***`inventory.ini`***
Le fichier `inventory.ini` est utilisé pour définir les hôtes Windows que vous souhaitez cibler avec Ansible. Il contient les informations nécessaires pour établir une connexion via WinRM (Windows Remote Management), notamment l'adresse IP de l'hôte, le nom d'utilisateur, le mot de passe et les paramètres de connexion pour WinRM.

### 2. ***`update_windows.yaml`***
Le fichier `update_windows.yaml` est un playbook Ansible qui automatise le processus de mise à jour des systèmes Windows en trois étapes principales :
- **Activation du Proxy** : Il configure un proxy temporaire pour permettre à Windows d'accéder à Internet et télécharger les mises à jour nécessaires.
- **Mise à jour de Windows** : Il recherche et installe les mises à jour critiques et de sécurité disponibles pour le système.
- **Désactivation du Proxy** : Une fois les mises à jour installées, il désactive et supprime la configuration du proxy.

## Prérequis

- **Ansible** : Vous devez avoir Ansible installé sur votre machine de contrôle.
- **Windows Hosts** : Les hôtes Windows doivent être configurés pour accepter les connexions WinRM. Les informations de connexion sont définies dans le fichier `inventory.ini`.
- **Permissions administratives** : Vous devez disposer des droits nécessaires pour effectuer des mises à jour et modifier les paramètres système sur les hôtes Windows.

## Exécution du Playbook

Pour exécuter ce playbook, vous devez avoir configuré Ansible et les hôtes Windows comme décrit dans le fichier `inventory.ini`. Vous pouvez ensuite lancer le playbook en utilisant la commande suivante :

```bash
ansible-playbook -i inventory.ini update_windows.yaml
```

Cette commande démarrera le processus de mise à jour sur les hôtes définis dans le fichier d'inventaire, appliquant les mises à jour et gérant la configuration du proxy.

## Conclusion

Ce dépôt offre une solution simple et automatisée pour maintenir vos systèmes Windows à jour, en passant par un proxy temporaire pour le téléchargement des mises à jour. Vous pouvez adapter et étendre ce playbook pour répondre à vos besoins spécifiques en matière de gestion des mises à jour Windows.
