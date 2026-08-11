# Finances publiques — notes visuelles

Site Quarto consacré aux notes personnelles de formation en finances publiques françaises.

> Comprendre les mécanismes derrière les chiffres.

🌐 **Site publié :** [https://MaryleneH.github.io/notes-finances-defense](https://MaryleneH.github.io/notes-finances-defense)

---

## Objectif

Ce site rassemble des notes pédagogiques et visuelles sur les finances publiques françaises : principes fondamentaux, architecture LOLF, programmation militaire, cadre budgétaire européen. Il est conçu pour progresser pas à pas, avec des schémas, des exemples et des sources institutionnelles.

---

## Architecture

```
.
├── _quarto.yml              # Configuration principale
├── index.qmd                # Page d'accueil
├── styles.scss              # Design system complet
├── about.qmd                # À propos
├── glossaire.qmd            # Glossaire des termes
├── sources.qmd              # Bibliographie institutionnelle
│
├── fondamentaux/
│   ├── index.qmd            # Vue d'ensemble de la section
│   ├── principes-budgetaires.qmd   # Annualité, unité, universalité, spécialité
│   └── architecture-lolf.qmd       # Missions, programmes, actions, AE/CP
│
├── defense/
│   ├── index.qmd            # Vue d'ensemble Défense & LPM
│   ├── lpm.qmd              # La LPM 2024-2030
│   ├── mission-defense.qmd  # Les 4 programmes (144, 146, 178, 212)
│   └── ae-cp.qmd            # AE et CP — l'exemple de la frégate
│
├── europe/
│   ├── index.qmd            # Vue d'ensemble Europe
│   └── depenses-nettes.qmd  # Les dépenses nettes (CGO 2024)
│
├── assets/
│   ├── diagrams/            # Schémas SVG style Excalidraw
│   ├── icons/               # Favicon, logo
│   └── images/              # Images éventuelles
│
└── .github/
    └── workflows/
        └── publish.yml      # Déploiement GitHub Pages
```

---

## Lancer localement

### Prérequis

Installer [Quarto](https://quarto.org/docs/get-started/).

### Prévisualiser

```bash
quarto preview
```

Le site est accessible à `http://localhost:4444` (port par défaut Quarto).

### Générer le site statique

```bash
quarto render
```

Les fichiers HTML sont générés dans le dossier `_site/`.

---

## Ajouter une nouvelle note

1. Créer un fichier `.qmd` dans la section appropriée :
   ```
   fondamentaux/ma-nouvelle-note.qmd
   ```

2. Ajouter l'en-tête YAML minimal :
   ```yaml
   ---
   title: "Titre de la note"
   description: "Description courte pour les métadonnées."
   toc: true
   ---
   ```

3. Ajouter le lien dans `_quarto.yml` si nécessaire (dans le menu de navigation).

4. Utiliser les composants CSS disponibles :
   - `.concept` — définition principale
   - `.remember` — bloc « À retenir »
   - `.example` — exemple concret
   - `.warning` — confusion fréquente
   - `.deep-dive` — pour aller plus loin
   - `.source-card` — source officielle
   - `.hand-note` — annotation manuscrite
   - `.question-card` — question pédagogique
   - `.local-nav` — navigation locale sticky
   - `.overview-grid` / `.overview-card` — cartes cliquables pour ouvrir un contenu
   - `.segmented-control` — boutons de bascule pour piloter un tabset Quarto
   - `::: {.panel-tabset}` — contenu principal en onglets

---

## Ajouter une nouvelle rubrique

1. Créer un nouveau dossier :
   ```bash
   mkdir ma-nouvelle-rubrique
   ```

2. Créer un `index.qmd` dans ce dossier.

3. Ajouter la rubrique dans le menu de navigation dans `_quarto.yml` :
   ```yaml
   navbar:
     left:
       - text: "Ma rubrique"
         href: ma-nouvelle-rubrique/index.qmd
   ```

---

## Ajouter un schéma

1. Créer le fichier SVG dans `assets/diagrams/mon-schema.svg`.
2. L'inclure dans une page `.qmd` :
   ```markdown
   ::: {.diagram-container}
   ![Description alt](../assets/diagrams/mon-schema.svg){width="100%" alt="Description détaillée"}
   :::
   ```

---

## Déploiement GitHub Pages

Le déploiement est **automatique** à chaque push sur la branche `main`.

Le workflow `.github/workflows/publish.yml` :
1. Installe Quarto
2. Rend le site (`quarto render`)
3. Déploie le dossier `_site/` sur GitHub Pages

**Prérequis GitHub :** activer GitHub Pages avec la source « GitHub Actions » dans les paramètres du dépôt (Settings → Pages → Source → GitHub Actions).

---

## Sources utilisées

Ce site s'appuie exclusivement sur des sources institutionnelles primaires :
Légifrance, Direction du Budget, Ministère des Armées, EUR-Lex, Commission européenne, Cour des comptes, Assemblée nationale, Sénat.
