# Système Multi-Agents pour bâtiment intelligent

Ce projet est une implémentation d'une architecture multi-agents sémantique pour la gestion énergétique et de confort d'un bâtiment, réalisé dans le cadre d'un projet de fin d'études. Le système utilise une approche hybride, combinant une logique déterministe pour les tâches simples et des Grands Modèles de Langage (LLM) pour le raisonnement complexe.

## Architecture

Le système est fondé sur trois piliers principaux :
1.  **Pilier sémantique** : Une ontologie (`SMA4SB.ttl`) définit tous les concepts, relations et règles du domaine (bâtiment, équipements, agents, intentions, etc.).
2.  **Pilier de communication** : Un **Tableau blanc sémantique** (un graphe RDF) sert de mémoire partagée et de seul canal de communication entre les agents.
3.  **Pilier décisionnel** : Un écosystème d'agents logiciels spécialisés (`AgentConfort`, `AgentEcoEnergie`, `AgentStratege`, etc.) qui collaborent de manière asynchrone pour atteindre les objectifs du système.

## Mise en route

Suivez ces étapes pour lancer une simulation.

### 1. Prérequis

* Python **3.8+**
* Git 
* Un environnement virtuel (recommandé)

### 2. Installation

Clonez ce dépôt sur votre machine locale :
```bash
git clone [https://github.com/ton-nom-utilisateur/ton-projet.git](https://github.com/ton-nom-utilisateur/ton-projet.git)
cd ton-projet
```
Créez et activez un environnement virtuel :
#### Sur macOS/Linux
```bash
python3 -m venv env
source env/bin/activate
```
#### Sur Windows
```bash
python -m venv env
env\Scripts\activate
```
Installez les dépendances Python nécessaires :
```bash
pip install rdflib openai python-dotenv jupyterlab
```
## Configuration
Le système a besoin de clés API pour interroger les modèles de langage (LLM).

### Obtenir les clés :

   1. Groq : Allez sur `console.groq.com/keys`, créez une clé et copiez-la.

   2. OpenRouter : Allez sur `openrouter.ai/keys`, créez une clé et copiez-la.
### Créer le fichier `.env` :

1. Créez un fichier nommé .env à la racine du projet.
2. Ouvrez ce fichier et insérez vos propres clés API sur le modèle suivant :
```bash
OPENROUTER_API_KEY="sk-or-v1-xxxxxxxxxxxxxxxxxxxx"
GROQ_API_KEY="gsk_xxxxxxxxxxxxxxxxxxxx"
```
## Lancement
La manière la plus simple de lancer et d'interagir avec les scénarios est via le notebook Jupyter.

1. Lancez JupyterLab depuis votre terminal :
```bash
jupyter lab
```
2. Dans l'interface de Jupyter qui s'ouvre dans votre navigateur, ouvrez le fichier SMA4SB.ipynb.

3. Exécutez les cellules une par une en utilisant Maj + Entrée pour voir le déroulement des scénarios de test.

## Scénarios de test
Le notebook contient plusieurs scénarios préconfigurés pour tester les différentes compétences du système :

1.  **Gestion de conflit :**  Simule un conflit entre une action de confort et un objectif d'économie d'énergie, testant la capacité d'arbitrage de `l'AgentMediateur`.

2.  **Détection de synergie :** Met en scène des besoins multiples afin d’évaluer la capacité de `l’AgentStratege` à proposer la solution la plus efficace (mutualisée).

3.  **Planification proactive :** Anticipe un besoin futur (événement de calendrier) pour valider la chaîne `AgentCalendrier -> AgentPlanificateur`.
