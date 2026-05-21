# Open WebUI pour YunoHost

[![Niveau d'intégration](https://dash.yunohost.org/integration/open-webui.svg)](https://dash.yunohost.org/appci/app/open-webui) ![Statut de fonctionnement](https://ci-apps.yunohost.org/ci/badges/open-webui.status.svg) ![Statut de maintenance](https://ci-apps.yunohost.org/ci/badges/open-webui.maintain.svg)<br>
[![Installer Open WebUI avec YunoHost](https://install-app.yunohost.org/install-with-yunohost.svg)](https://install-app.yunohost.org/?app=open-webui)

> *Ce package vous permet d'installer Open WebUI rapidement et simplement sur un serveur YunoHost.
> Si vous n'avez pas YunoHost, veuillez consulter [le guide](https://doc.yunohost.org/admin/get_started/install_on/) pour apprendre comment l'installer.*

## Aperçu

Open WebUI est une interface IA auto-hébergée et extensible avec support de l'API OpenAI et une interface similaire à ChatGPT pour une autonomie complète. Il fournit une interface web moderne pour interagir avec les modèles d'IA, supportant les backends de modèles locaux (Ollama) et distants (compatibles OpenAI).

### Fonctionnalités

- **Interface style ChatGPT**: Interface web moderne et intuitive pour les conversations IA
- **Authentification SSO/LDAP**: Intégrée au système d'authentification YunoHost
- **Support WebSocket**: Réponses en streaming en temps réel pour des interactions fluides
- **Support Multi-Modèles**: Connectez-vous à Ollama, OpenAI et d'autres API compatibles OpenAI
- **Gestion des Modèles**: Téléchargez et gérez les modèles IA directement depuis l'interface
- **Téléchargement de Fichiers**: Support des documents (PDF, TXT, DOCX, etc.)
- **Panneau d'Administration**: Contrôles admin complets pour la gestion des utilisateurs et des paramètres
- **Auto-hébergé**: Contrôle total sur votre infrastructure IA

**Version incluse:** 0.3.31~ynh1

**Démo:** https://sentencebook.com

## Captures d'écran

![Capture d'écran d'Open WebUI](./doc/screenshots/open-webui.png)

## Avertissements / Informations Importantes

### Authentification

- Open WebUI utilise SSOwat/LDAP de YunoHost pour l'authentification
- Les utilisateurs sont automatiquement connectés lors de l'accès via le portail YunoHost
- L'accès admin est accordé à l'utilisateur sélectionné pendant l'installation

### Configuration Requise

- **Espace Disque**: Minimum 2Go pour l'installation, plus pour les modèles IA
- **RAM**: Minimum 1Go d'exécution, plus recommandé pour l'inférence de modèle
- **Architecture**: Fonctionne sur toutes les architectures supportées par YunoHost (amd64, i386, armhf, arm64)

### Support WebSocket

- Les téléchargements de modèles et les flux de chat nécessitent le support WebSocket
- Ceci est automatiquement configuré par le package
- Les délais d'attente sont fixés à 24 heures pour les opérations IA longue durée

### Stockage des Modèles

- Les modèles sont stockés dans `/home/yunohost.app/open-webui/models`
- Les téléchargements peuvent utiliser un espace disque significatif
- Les fichiers téléversés sont stockés dans `/home/yunohost.app/open-webui/uploads` (limite de 10Go)

### Processus de Mise à Jour

- Les mises à jour exécutent les migrations avec un seul worker pour éviter la corruption de la base de données SQLite
- Le service est brièvement arrêté pendant les mises à jour (généralement moins de 2 minutes)
- Aucune perte de données car le répertoire de données est préservé

## Documentation et Ressources

* Site web officiel de l'application: <https://openwebui.com>
* Documentation utilisateur officielle: <https://docs.openwebui.com/>
* Documentation administrateur officielle: <https://docs.openwebui.com/>
* Dépôt de code upstream: <https://github.com/open-webui/open-webui>
* Documentation YunoHost pour cette application: <https://yunohost.org/app_open-webui>
* Signaler un bug: <https://github.com/YunoHost-Apps/open-webui_ynh/issues>

## Info Développeur

Veuillez envoyer vos pull requests vers la [branche testing](https://github.com/YunoHost-Apps/open-webui_ynh/tree/testing).

Pour essayer la branche testing, procédez comme ceci:

```bash
sudo yunohost app install https://github.com/YunoHost-Apps/open-webui_ynh/tree/testing --debug
```

ou

```bash
sudo yunohost app upgrade open-webui -u https://github.com/YunoHost-Apps/open-webui_ynh/tree/testing --debug
```

**Plus d'informations concernant le packaging d'application:** <https://doc.yunohost.org/dev/packaging/>

## Licence

Ce package est publié sous la licence MIT. Voir le fichier [LICENSE](./LICENSE) pour plus de détails.