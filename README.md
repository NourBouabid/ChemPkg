# chempkg — Package Python pour la modélisation chimique

**Programmation orientée objet · Packaging Python · Tests unitaires · Calcul scientifique**

## Présentation

`chempkg` est un package Python développé dans le cadre d'un projet de M1. Il propose des objets et des fonctions pour représenter des atomes et des molécules, examiner l'équilibrage de réactions chimiques et simuler une cinétique de décomposition simple.

L'objectif du projet est aussi **logiciel** : organiser des fonctionnalités dans plusieurs modules, définir une interface Python, préparer un package installable et tester ses composants.

# Architecture

Ce repertoire est organisé de la maniere suivante:
```
├── README.md
├── chempkg
│   ├── atom.py
│   ├── mol.py
│   └── reaction_utils.py
├── pyproject.toml
└── tests
    ├── test_atom.py
    ├── test_molecule.py
    └── test_reactions_utils.py
```
`chempkg` est un package pour de la chime. Il contient trois modules: `atom`, `mol` et `reaction_utils`.

## Module atom
Ce module permet de représenter des atomes avec nombre d'électrons, masse atomique et configuration électronique approchée selon l'ordre de remplissage de Klechkowski

### Classe Atom  

```python
Atom(name: str, num_electron: int, weight: float)
```

Attributs :
- `name` : symbole chimique de l’atome
- `num_electron` : nombre d’électrons
- `weight` : masse atomique


### Atomes prédéfinis :

`O`, `C`, `H`, `N`, `Ca`, `P`, `K`, `S`, `Na`, `Cl`, `Fe`, `I`, `F`, `Co`, `Mo` 

### Méthode :
- `elec_config()` : renvoie la configuration électronique de l’atome selon la règle de Klechkowski


## Module mol

Ce module permet de manipuler des molécules à partir de leur formule chimique: lecture de formules chimiques simples, composition atomique et calcul de masse molaire. 

### Classe Molecule  
```python
Molecule(formule: str)
```

### Méthodes :
- `atoms()` : renvoie un dictionnaire associant chaque atome de la molécule à sa quantité
- `weight()` : calcule et renvoie la masse molaire de la molécule

## Module reaction_utils

Ce module fournit des outils liés aux réactions chimiques et à la cinétique, en particulier la vérification de l'équilibrage d'une réaction et la simulation d'une décomposition d'ordre 1. 

### Fonctions :
```python
valid_reaction(reactifs: list[tuple[Molecule, int]], produits: list[tuple[Molecule, int]]) -> bool
```
Vérifie si une réaction chimique est équilibrée.

```python
kinetic_decomp(A0: float, k: float, T: float, steps: int = 10, figure_path: str | None = None)  
```
Calcule l’évolution temporelle de la concentration d’une molécule lors d’une réaction de décomposition cinétique.  
Une figure peut être sauvegardée si figure_path est fourni

## Installation

Cloner le dépôt puis installer le package en mode développement :

`pip install -e .` 
