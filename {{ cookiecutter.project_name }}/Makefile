ENV_FILE=.env
REQUIREMENTS=requirements.txt
VENV=venv

PROJECT_NAME={{ cookiecutter.project_name }}

.PHONY: help
help:
	@echo "Usage: make [target]"
	@echo ""
	@echo "Targets:"
	@echo "  install        - Crée un environnement virtuel et installe les dépendances."
	@echo "  tests       - Exécute les tests avec génération de rapports de couverture."
	@echo "  run            - Lance l'application principale."
	@echo "  sonar          - Exécute SonarQube pour analyser le code (si configuré)."
	@echo "  format         - Formate le code avec black."
	@echo "  lint           - Vérifie le code avec flake8."
	@echo "  clean          - Supprime l'environnement virtuel et les fichiers temporaires."

.PHONY: install
install: $(VENV)/bin/activate

$(VENV)/bin/activate: $(REQUIREMENTS)
	python3.9 -m venv $(VENV)
	$(VENV)/bin/pip install --upgrade pip
	$(VENV)/bin/pip install -r $(REQUIREMENTS)

.PHONY: tests
tests: $(VENV)/bin/activate
	$(VENV)/bin/pytest --cov=src --cov-report=term-missing --cov-report=html tests/ --junitxml=results/pytest-results.xml

.PHONY: run
run: $(VENV)/bin/activate
	$(VENV)/bin/python src/{{ cookiecutter.project_slug }}/main.py

{% if cookiecutter.use_sonarqube == "yes" %}
.PHONY: sonar
sonar: $(VENV)/bin/activate
	sonar-scanner \
		-Dsonar.projectKey={{ cookiecutter.sonarqube_project_key }} \
		-Dsonar.sources=. \
		-Dsonar.host.url={{ cookiecutter.sonarqube_server_url }} \
		-Dsonar.login={{ cookiecutter.sonarqube_token }}
{% else %}
.PHONY: sonar
sonar:
	@echo "SonarQube n'est pas configuré pour ce projet."
{% endif %}

.PHONY: format
format: $(VENV)/bin/activate
	$(VENV)/bin/black .

.PHONY: lint
lint: $(VENV)/bin/activate
	$(VENV)/bin/flake8 src/ tests/ > results/flake8-report.txt

.PHONY: clean
clean:
	rm -rf $(VENV)
	find . -type d -name "__pycache__" -exec rm -rf {} +
	find . -type f -name "*.pyc" -exec rm -f {} +
	find . -type f -name "*.pyo" -exec rm -f {} +
