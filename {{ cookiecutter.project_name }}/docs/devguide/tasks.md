# Guide d'Automatisation des Tâches

## Tâches

De nombreuses tâches, en particulier celles liées à la configuration, sont automatisées en utilisant `make`. Ces tâches sont définies dans le `Makefile`. Vous trouverez ci-dessous les principales tâches disponibles.

L'environnement virtuel par défaut est appelé `{{ cookiecutter.project_name }}_env`. Cet environnement est activé en tant que partie intégrante de ces tâches.

| Tâche                      | Commande                | Description                                                                                     |
|----------------------------|-------------------------|-------------------------------------------------------------------------------------------------|
| Créer l'environnement virtuel | `make install`           | Crée un environnement virtuel et installe les dépendances définies dans `requirements.txt`.      |
| Supprimer l'environnement virtuel | `make clean`            | Supprime l'environnement virtuel et les fichiers temporaires générés.                            |
| Réinitialiser l'environnement virtuel | `make reinstall`       | Supprime et recrée l'environnement virtuel, réinstalle toutes les dépendances.                    |
| Mettre à jour les dépendances | `make update`           | Met à jour les dépendances à partir de `requirements.txt`.                                       |
| Lancer JupyterLab           | `make jupyterlab`       | Démarre JupyterLab par défaut pour l'exploration des données et le développement interactif.     |
| Exécuter les tests unitaires | `make tests`            | Exécute les tests unitaires avec `pytest` et génère un rapport XML pour Jenkins.                 |
| Exécuter les tests avec couverture | `make coverage`         | Exécute les tests unitaires avec `pytest` tout en générant un rapport de couverture de code.     |
| Formater le code            | `make format`           | Formate le code Python en utilisant `black`.                                                    |
| Vérifier le code avec Flake8| `make lint`             | Exécute `flake8` pour vérifier le respect des conventions de codage.                             |
| Analyser le code avec SonarQube | `make sonar`            | Exécute une analyse de code avec SonarQube (si configuré).                                       |

### Détails des Commandes Make

1. **Créer l'environnement virtuel (`make install`)** :
   - Crée un environnement virtuel dans le dossier `venv` et installe les dépendances définies dans `requirements.txt`.

2. **Supprimer l'environnement virtuel (`make clean`)** :
   - Supprime l'environnement virtuel et nettoie les fichiers temporaires et les caches pour assurer un environnement propre.

3. **Réinitialiser l'environnement virtuel (`make reinstall`)** :
   - Supprime l'environnement virtuel existant et le recrée, réinstallant toutes les dépendances définies dans `requirements.txt`.

4. **Mettre à jour les dépendances (`make update`)** :
   - Met à jour toutes les dépendances à partir de `requirements.txt` en utilisant l'environnement virtuel actuel.

5. **Lancer JupyterLab (`make jupyterlab`)** :
   - Démarre un serveur JupyterLab, qui peut être utilisé pour le développement interactif et l'exploration des données.

6. **Exécuter les tests unitaires (`make tests`)** :
   - Exécute les tests définis dans le répertoire `tests/` avec `pytest` et génère un rapport XML, idéal pour une intégration avec des outils CI comme Jenkins.

7. **Exécuter les tests avec couverture (`make coverage`)** :
   - Exécute les tests tout en générant un rapport de couverture de code, stocké au format HTML et XML.

8. **Formater le code (`make format`)** :
   - Utilise `black` pour formater automatiquement le code Python selon les standards définis.

9. **Vérifier le code avec Flake8 (`make lint`)** :
   - Exécute `flake8` pour vérifier la conformité du code aux normes de style Python, avec les résultats enregistrés dans `results/flake8-report.txt`.

10. **Analyser le code avec SonarQube (`make sonar`)** :
    - Exécute une analyse de code avec SonarQube pour évaluer la qualité du code et détecter les vulnérabilités potentielles.

### Recommandations

- **Configuration initiale** : Exécutez `make install` dès la création du projet pour configurer l'environnement de développement.
- **Tests réguliers** : Utilisez `make tests` et `make coverage` régulièrement pour vérifier que votre code fonctionne comme prévu et que la couverture des tests est adéquate.
- **Maintenance du code** : Avant chaque commit, il est conseillé d'exécuter `make lint` et `make format` pour garantir la qualité et la conformité du code.

Ce guide vous aidera à automatiser les tâches courantes et à maintenir un environnement de développement efficace et cohérent pour votre projet {{ cookiecutter.project_name }}.
