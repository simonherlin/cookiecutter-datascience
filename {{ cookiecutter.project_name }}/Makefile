# Nom du fichier de configuration de l'environnement
ENV_FILE=.env
# Nom du fichier requirements
REQUIREMENTS=requirements.txt
# Dossier de l'environnement virtuel
VENV=venv

# Nom du projet
PROJECT_NAME={{ cookiecutter.project_name }}

# Cible par défaut
.PHONY: help
help:
	@echo "Usage: make [target]"
	@echo ""
	@echo "Targets:"
	@echo "  install        - Crée un environnement virtuel et installe les dépendances."
	@echo "  tests          - Exécute les tests unitaires avec pytest."
	@echo "  coverage       - Exécute les tests avec génération de rapports de couverture."
	@echo "  run            - Lance l'application principale."
	@echo "  sonar          - Exécute SonarQube pour analyser le code (si configuré)."
	@echo "  format         - Formate le code avec black."
	@echo "  lint           - Vérifie le code avec flake8."
	@echo "  clean          - Supprime l'environnement virtuel et les fichiers temporaires."

# Crée un environnement virtuel et installe les dépendances
.PHONY: install
install: $(VENV)/bin/activate

$(VENV)/bin/activate: $(REQUIREMENTS)
	python3 -m venv $(VENV)
	$(VENV)/bin/pip install -r $(REQUIREMENTS)
	touch $(VENV)/bin/activate

# Exécute les tests unitaires
.PHONY: tests
tests: $(VENV)/bin/activate
	$(VENV)/bin/pytest tests/

# Exécute les tests avec génération de rapports de couverture
.PHONY: coverage
coverage: $(VENV)/bin/activate
	$(VENV)/bin/pytest --cov=src --cov-report=term-missing --cov-report=html tests/

# Lance l'application principale
.PHONY: run
run: $(VENV)/bin/activate
	$(VENV)/bin/python src/{{ cookiecutter.project_slug }}/main.py

# Exécute SonarQube
.PHONY: sonar
sonar: $(VENV)/bin/activate
{% raw %}
{% if cookiecutter.use_sonarqube == "yes" -%}
	$(VENV)/bin/sonar-scanner \
		-Dsonar.projectKey={{ cookiecutter.sonarqube_project_key }} \
		-Dsonar.sources=. \
		-Dsonar.host.url={{ cookiecutter.sonarqube_server_url }} \
		-Dsonar.login={{ cookiecutter.sonarqube_token }}
{% else -%}
	@echo "SonarQube n'est pas configuré pour ce projet."
{% endif -%}
{% endraw %}

# Formate le code avec black
.PHONY: format
format: $(VENV)/bin/activate
	$(VENV)/bin/black .

# Vérifie le code avec flake8
.PHONY: lint
lint: $(VENV)/bin/activate
	$(VENV)/bin/flake8 src/ tests/

# Nettoie l'environnement virtuel et les fichiers temporaires
.PHONY: clean
clean:
	rm -rf $(VENV)
	find . -type d -name "__pycache__" -exec rm -rf {} +
	find . -type f -name "*.pyc" -exec rm -f {} +
	find . -type f -name "*.pyo" -exec rm -f {} +
