# Point Isoelectrique -- Calculateur interactif

Application web interactive pour apprendre a calculer le point isoelectrique (pI) des peptides en biochimie.

## Fonctionnalites

- **Generation aleatoire de peptides** : choix du nombre d'acides amines ionisables (2 a 10) avec indicateur de difficulte
- **Visualisation du peptide** : representation graphique coloree de la sequence peptidique, avec groupements terminaux (NH3+, COO-) et valeurs de pKa
- **Tableau de charges interactif** : saisie des etats de charge (+, -, 0) pour chaque residu a chaque intervalle de pH, avec suivi de progression en temps reel
- **Panneau theorique contextuel** : echelle de pH visuelle, legende des charges, rappels sur la relation pH/pKa et indicateurs dynamiques des pKa
- **Validation intelligente** : correction automatique avec score, temps ecoule, barres de performance et conseils pedagogiques personnalises
- **Animations fluides** : transitions et micro-interactions sur l'ensemble de l'interface (Framer Motion)
- **Design responsive** : interface adaptee aux ecrans de bureau et mobiles

## Technologies

| Categorie       | Outil                          |
|-----------------|--------------------------------|
| Framework       | React 19 + TypeScript          |
| Bundler         | Vite 7                         |
| Styles          | Tailwind CSS 4, PostCSS        |
| Composants UI   | Radix UI (Slider, Separator, Tooltip, Progress) |
| Animations      | Framer Motion                  |
| Icones          | Lucide React                   |
| Utilitaires CSS | clsx, tailwind-merge           |
| Polices         | Inter, JetBrains Mono          |

## Installation

**Prerequis :** Node.js (version 18 ou superieure recommandee)

```bash
# Cloner le depot
git clone <url-du-depot>
cd isoelectric-calculator

# Installer les dependances
npm install

# Lancer le serveur de developpement
npm run dev
```

L'application sera accessible par defaut sur `http://localhost:5173`.

### Autres commandes

```bash
# Compiler pour la production
npm run build

# Previsualiser le build de production
npm run preview

# Lancer le linter
npm run lint
```

## Utilisation

L'application guide l'utilisateur a travers 4 etapes successives :

### Etape 1 -- Configuration

Choisir le nombre d'acides amines ionisables a l'aide du curseur (de 2 a 10). L'interface affiche un indicateur de difficulte et le nombre de cellules a remplir. Cliquer sur "Generer un Nouveau Peptide" pour demarrer.

### Etape 2 -- Resolution

Le peptide genere s'affiche avec sa sequence et ses valeurs de pKa. Un panneau lateral presente l'echelle de pH, la legende des charges et les rappels theoriques. Remplir le tableau en cliquant sur chaque cellule pour basculer entre les etats de charge (+, -, 0) selon la relation entre le pH de l'intervalle et le pKa du residu.

### Etape 3 -- Verification

Une fois le tableau entierement rempli, cliquer sur "Verifier mes reponses" pour lancer la correction. Le bouton est desactive tant que toutes les cellules ne sont pas renseignees.

### Etape 4 -- Resultats

L'application affiche le score (pourcentage de reponses correctes), le detail des reponses justes et fausses, le temps total, un indicateur de rapidite et des conseils personnalises en fonction des erreurs commises. Un bouton permet de recommencer avec un nouveau peptide.

## Structure du projet

```
isoelectric-calculator/
├── index.html
├── package.json
├── vite.config.ts
├── tsconfig.json
├── tsconfig.app.json
├── tsconfig.node.json
├── tailwind.config.js
├── postcss.config.js
├── eslint.config.js
├── public/
└── src/
    ├── main.tsx                          # Point d'entree
    ├── App.tsx                           # Composant racine, gestion des etapes
    ├── App.css
    ├── index.css
    ├── vite-env.d.ts
    ├── data/
    │   └── aminoAcids.ts                 # Donnees des acides amines, pKa, types
    ├── utils/
    │   ├── peptideGenerator.ts           # Generation aleatoire, calcul des pKa
    │   └── chargeCalculator.ts           # Calcul des charges correctes
    ├── lib/
    │   └── utils.ts                      # Utilitaires (cn, couleurs pH, conseils)
    ├── components/
    │   ├── PeptideGenerator.tsx           # Generateur de peptide (version simple)
    │   ├── ChargeTable.tsx                # Tableau de charges (version simple)
    │   ├── ValidationPanel.tsx            # Panneau de validation (version simple)
    │   └── ui/
    │       ├── StepperNavigation.tsx      # Barre de navigation par etapes
    │       ├── PeptideConfigurator.tsx    # Configuration du peptide avec slider
    │       ├── PeptideVisualizer.tsx      # Visualisation graphique du peptide
    │       ├── InteractiveChargeTable.tsx # Tableau de charges interactif
    │       ├── TheoreticalPanel.tsx       # Panneau lateral theorique
    │       └── ValidationSystem.tsx       # Systeme de validation et resultats
    └── assets/
        └── react.svg
```

## Licence

Projet a usage educatif.
