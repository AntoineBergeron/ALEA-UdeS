# Capsules d'atelier sur R

Présentateur: Antoine Bergeron

---
title: "Séance 1: Introduction à la programmation scientifique"
author: "Dominique Gravel"
date: "Hiver 2020"
output:
  xaringan::moon_reader:
    css: [default, ../bio109.css, "hygge"]
    lib_dir: assets
    seal: false
    nature:
      highlightStyle: monokai
      highlightLines: true
      countIncrementalSlides: false
      beforeInit: "../macros.js"
---

class: title-slide, middle

<style type="text/css">
  .title-slide {
    background-image: url('assets/img/bg.jpg');
    background-color: #23373B;
    background-size: contain;
    border: 0px;
    background-position: 600px 0;
    line-height: 1;
  }
</style>

# Séance 1

<hr width="65%" align="left" size="0.3" color="orange"></hr>

## Introduction à la programmation scientifique

<hr width="65%" align="left" size="0.3" color="orange" style="margin-bottom:40px;" alt="@Martin Sanchez"></hr>

.instructors[
  **BIO109** - Dominique Gravel
]

<img src="assets/img/logo.png" width="8%" style="margin-top:20px;"></img>


---

# Introduction

<div style='text-align:center;'>
<img src="assets/img/intro/bioclim.png" height="500px"></img>
</div>

---

# Introduction

<div style='text-align:center;'>
<img src="assets/img/intro/mont_vertes.png" height="500px"></img>
</div>

---

# Introduction

<div style='text-align:center;'>
<img src="assets/img/intro/megantic.jpg" height="500px"></img>
</div>

---

# Introduction

<div style='text-align:center;'>
<img src="assets/img/intro/ours.jpg" height="500px"></img>
</div>

---

# Introduction

<div style='text-align:center;'>
<img src="assets/img/intro/orignal.jpg" height="400px"></img>
</div>

---

# Introduction

<div style='text-align:center;'>
<img src="assets/img/intro/salamandre.jpg" height="400px"></img>
</div>

---

# Introduction

<div style='text-align:center;'>
<img src="assets/img/intro/cypripedium.jpg" height="400px"></img>
</div>

---

# Introduction

<div style='text-align:center;'>
<img src="assets/img/intro/grille.jpg" height="250px"></img>
</div>

---

# Projet de session

## Question de recherche

À quelle vitesse se réalisera la migration de l'érable à sucre, et des espèces associées, au sein de la sapinière de montagne du massif des Montagnes vertes ?

---

# Le type de données

```{r}
arbres <- read.table(file = './donnees/arbres.txt', header = TRUE, sep=";")
head(arbres)
```

---

# Exercice 1

Ouvrir le fichier [arbres](./donnees/arbres.xlsx) avec Excel et calculer le nombre d'individus de chaque espèce pour le quadrat 1.

---

# Exercice 1: solution sur R

```{r}
arbres <- read.table(file = './donnees/arbres.txt', header = TRUE, sep=";")
quadrats <- table(arbres$id_bor,arbres$esp)
head(quadrats)
```

```{r, echo=FALSE}
write.table(quadrats, file="./donnees/quadrats.txt",sep=";",quote=TRUE)
```
---

# Exercice 2

Ouvrir le fichier [quadrats](./donnees/quadrats.xlsx) avec Excel et calculer la corrélation entre toutes les paires d'espèces.

Petit truc: sur Excel, la fonction pour calculer une corrélation est:

```bash
=COEFFICIENT.CORRELATION(données_1; données_2)
```

---

# Exercice 2: solution sur R

```{r,eval=FALSE}
quadrats <- read.table(file = './donnees/quadrats.txt', header = TRUE, sep= ";")
cor(quadrats)
```

```{r,eval=TRUE,echo=FALSE}
quadrats <- read.table(file = './donnees/quadrats.txt', header = TRUE, sep= ";")
round(cor(quadrats),6)
```

---

# Exercice 2: visualisation sur R

```{r,  fig.width= 6, fig.height= 6, fig.align='center'}
plot(quadrats)
```

---

# Objectif général

Au terme de ce cours, l'étudiant sera en mesure de conceptualiser un problème qui requiert de la programmation scientifique et de réaliser des tâches courantes de programmation.

---

# Objectifs spécifiques

1. Charger des données et exporter des résultats d'analyses au moyen du
    logiciel R;
2. Conceptualiser un problème au moyen de pseudo-code;
3. Manipuler des données;
4. Rédiger des fonctions;
5. Programmer des algorithmes afin de réaliser des tâches complexes,
    incluant des boucles et des énoncés conditionnels;
6. Réaliser des simulations de Monte Carlo;

---
# Contenu

1. Introduction et bonnes pratiques de programmation
2. Interagir avec R
3. Les fonctions
4. Algorithmique I: boucles et conditions
5. Alogithmique II: simulations de Monte Carlo

---

# Ce que le cours n'est pas ...

1. Des recettes
2. Un catalogue de fonctions R
3. Un cours de statistiques

---

# Approche

Les connaissances requises pour la programmation scientifique sont
minimales, l'apprentissage porte davantage sur l'acquisition de
compétences et le développement de capacités à la résolution de problèmes.


Les séances seront constituées de courtes leçons magistrales sur des
notions de bases de programmation, entre-coupées d'exercices spécifiques
destinés à pratiquer les éléments enseignés. Les séances se conclueront
sur la réalisation d'un exercice intégrateur à compléter à la maison.

L'ensemble du matériel du cours sera disponible sur un dépôt Git à l'adresse :
https://github.com/EcoNumUdS/BIO109.git

---

# Évaluation

L'évaluation porte sur la participation (20%) et sur un
travail de session (80%). Un exercice simple sera présenté à la fin des
séances 1-4 et <b>chaque étudiant</b> devra remettre la solution de l'exercice sous
forme de script <i>avant le début</i> de la séance suivante. Les exercices
peuvent être réalisés en groupe, mais <b>chaque étudiant</b> devra remettre sa
propre copie, personnalisée. <b>Les points sont attribués pour la
participation.</b>

L'évaluation finale portera sur la réalisation d'un projet de
programmation <b>en équipe de 4</b> à remettre deux semaines après la fin du
dernier cours, soit au plus tard le <b>18 février 2020 à 23:59</b>. La
pénalité sera de 10% par jour de retard. Le rapport final sera évalué à
partir de

   1. le pseudo-code pour le projet de programmation,
   2. le respect des bonnes pratiques de programmation
   3. la réussite de l'exercice demandé.

Les étudiants devront remettre le script nécessaire à la
réalisation du projet.

---
class: inverse, center, middle

# La place de la programmation en écologie
<hr width="65%" size="0.3" color="orange" style="margin-top:-20px;"></hr>


---

# Hier

La dynamique d'une population:

$$
\frac{dN}{dt} = rN(1-\frac{N}{K})
$$

Qui donne pour solution à l'équilibre:

$$
N^* = K
$$

$N =$ Taille d'une population

$t =$ temps

$r =$ taux de croissance

$K =$ capacité de support de l'environnement

---

# Aujourd'hui

.pull-left[
  <div style='text-align:center;'>
  <img src="assets/img/intro/modele_vissault.png" width="100%"></img>
  </div>
]

.pull-right[
- R: Regénération
- T: Forêts tempérées
- M: Forêts mixes
- B: Forêts boréale
]



---

# Aujourd'hui

<div style='text-align:center;'>
<img src="assets/img/intro/map_vissault.png" height="550px"></img>
</div>

---

# Et demain, la modélisation de la biosphère?
<div style='text-align:center;'>
<img src="assets/img/intro/PurvesNature.jpg" height="400px"></img>
</div>

---

# Progression de la puissance de calcul

<div style='text-align:center;'>
  <img src="assets/img/intro/moores.png" height="525px"></img>
</div>

<!-- Ces questions sont rendu possible en partie grâce à l'augmentation de la puissance de nos ordinateurs et l'accessibilité aux données -->

---

# Utilisation en science au quotidien

La programmation est outil indispensable au biologiste 2.0, elle permet:

- Tâches répétitives et/ou complexes (p.ex. Nettoyage des données, Simulations stochastiques)
- Visualisation et exploration des données
- Analyses statistiques avancées (p. ex. tests par permutations, statistiques bayésiennes)

---

# La programmation en science

.pull-left[
## Avantages

- Gain de temps
- Limiter les erreurs
- Formaliser les opérations
- Archiver, reproduire et partager
- Tâches intensives (e.g. en génomique)
]


.pull-right[
## Augmentation du volume de données génomiques
<img src="assets/img/intro/data_increase.jpg" width="100%"></img>
<span style="font-size:small;text-transform:uppercase;text-align:right;">
[Nature 2013](http://www.nature.com/nature/journal/v498/n7453/full/498255a.html)
</span>
]

---

# La programmation en science

<img src="assets/img/intro/geek_mode.jpg" align="center" width="80%"></img>

---

# La programmation en science

.pull-left[
## Inconvénients

- L'erreur est avant tout humaine, avant d'être informatique
- La courbe apprentissage peut être difficile
]

.pull-right[
<img src="assets/img/intro/FunctionalResp.svg" width="100%"></img>
]


---
class: inverse, center, middle

# Les langages de programmation
<hr width="65%" size="0.3" color="orange" style="margin-top:-20px;"></hr>


---

# Deux grandes familles de langages

1. Les langages compilés
2. Les langages interprétés

---

# 1. Les langages compilés

<div style='text-align:center;'>
  <img src="assets/img/intro/compile.png"  width="900px"></img>
</div>

---

# 2. Les langages interprétés

<div style='text-align:center;'>
  <img src="assets/img/intro/interprete.png" width="900px"></img>
</div>

---

# La performance: un critère pour le choix d'un langage

<div style='text-align:center;'>
  <img src="assets/img/intro/performance.png" width="900px"></img>
</div>

---

# Un autre critère est le 'débugging'

<div style='text-align:center;'>
  <img src="assets/img/intro/bug.jpg" width="600px"></img>
</div>

---
class: inverse, center, middle

# Et en écologie?
<hr width="65%" size="0.3" color="orange" style="margin-top:-20px;"></hr>


---
class: inverse, middle, center

# Le Pseudo-Code
<hr width="65%" size="0.3" color="orange" style="margin-top:-20px;"></hr>

---

# Le `Pseudo-Code` et ses **algorithmes**


## Définitions

- *En programmation, le `pseudo-code` est une façon de formuler un <b>algorithme</b> sans référence à un langage de programmation en particulier.*

> - *Un <b>algorithme</b> est une suite d'actions qui sont réalisées dans un ordre précis par l'ordinateur. C'est une séquence d'étapes dans la résolution d'un problème.*

---

# Le `Pseudo-Code`

## Exemple

```
PROGRAM DEMO
  FOR t IN 1:100
    n_t = n_t * lambda
    PRINT n_t
    IF n_t < 1
      BREAK
    ELSE
      CONTINUE
    END IF
  END FOR
```

Le programme `DEMO` fait croitre une population à un taux $\lambda$ et affiche à l'utilisateur si la population est éteinte ($n_t<1$) ou vivante ($n_t>1$).

---

# Le `Pseudo-Code`

## Exemple

```
PROGRAM DEMO
  FOR t IN 1:100 <------------- Opération itérative
    n_t = n_t * lambda
    PRINT n_t <---------------- Le programme affiche la valeur à l'écran
    IF n_t < 1 <--------------- Opération décisionnelle
      BREAK <------------------ Le programme arrête son éxécution
    ELSE
      CONTINUE <--------------- Le programme continue son éxécution
    END IF
  END FOR
```

Le programme `DEMO` fait croitre une population à un taux $\lambda$ et affiche à l'utilisateur si la population est éteinte ($n_t<1$) ou vivante ($n_t>1$).


---

# Les structures de base d'un algorithme

On retrouve 3 familles d'opérations:

1. Les opérations séquentielles
2. Les opérations itératives (`FOR`, `WHILE`)
3. Les opérations décisionnelles (`IF`, `IFELSE`)

---

# Avant-propos

Avant de décrire chacune des opérations d'un algorithme, certaines instructions sont communes:

- `READ`: Le programme lit un fichier
- `WRITE`: Le programme écrit un fichier
- `PRINT`: Le programme écrit un message à l'écran pour l'utilisateur
- `BREAK`: Le programme stop son éxécution
- `CONTINUE`: Le programme continue son éxécution

---

# 1. Les opérations séquentielles

## Exemple: Calculer l'aire d'un rectangle

```
PROGRAM REC_AIRE
  READ hauteur
  READ largeur
  WRITE hauteur * largeur
```

Chaque opération est effectuée l'une après l'autre dans un ordre déterminé.

---

# 2. Les opérations itératives

## Exemple avec `FOR`: Croissance exponentielle

```
PROGRAM DEMO
  FOR t IN 1:100
    n_t = n_t * lambda
  END FOR
```

La population va croître pendant 100 pas de temps.

---

# 2. Les opérations itératives

## Exemple avec `WHILE`: Croissance avec capacité de support (K)

```
PROGRAM DEMO
  WHILE n_t < K
    n_t = n_t * lambda
  END WHILE
```

---

# 3. Les opérations décisionnelles

## Exemple avec `IF`: quelques tests sur $\lambda$

```
PROGRAM DEMO
  IF lambda > 0
    PRINT "La population est croissante"
  ELSE lambda < 0
    PRINT "La population est décroissante"
  ENDIF
```

> - Et si le taux de croissance est nul?
---

# 3. Les opérations décisionnelles

```
PROGRAM DEMO
  IF lambda > 0
    PRINT "La population est croissante"
  IF ELSE lambda < 0
    PRINT "La population est décroissante"
  ELSE
    PRINT "Absence de croissance"
  ENDIF
```

Avec la clause `ELSE`, la croissance est nulle

---

# Les types d'objets

Les objets en programmation sont définis en fonction de leur dimensionalité.

## Dimensionalité

- **Dimension 0** : Valeur unique
- **Dimension 1** : Vecteur
- **Dimension 2** : Matrice
- **Dimension 3** : ...

Bien qu'il n'y ai pas de limite à la dimension d'un objet en programmation,
pour le cours nous nous limiterons à des objets en deux dimensions
(c.à.d Matrice)

---

# Dimension 0

Ces objets ne contiennent qu'une seule information

## Exemple

```
bobo = "toi"
coco = 2
dodo = -3
fofo = 456457.678
```

---

# Dimension 1

Ces objets contiennent un série d'information. Chaque valeur
a une position dans le vecteur, laquelle peut être accédée.

## Exemple

```
lettre = ["A" "R" "C" "D" "A"]
lettre[3]
# "C"
```

---

# Dimension 2

Ayant deux dimensions, ces objets présentent les données sous forme de matrices et ont des lignes et des colonnes. Pour accéder à une valeur dans une matrice il faut donner la position de la <b>ligne</b> en premier suivit de la position de la <b>colonne</b>.

## Exemple

```
lettreTab = ["A" "R" "C"
             "D" "A" "T"
             "R" "A" "Q"]
lettreTab[2, 1]
# "D"
```

---

# Les règles du `pseudo-code`

## A garder en mémoire

1. N'écrivez qu'une seule instruction par ligne de pseudo-code.
2. Écrivez en lettres majuscules le verbe de chaque opération principale.
3. Soyez explicite en nommant les opérations et les variables.
4. Soyez le plus détaillé possible (c.à.d les plus petites étapes possibles)
5. Utilisez des structures de langages de programmation connues (c.à.d `WHILE`, `FOR`, `IF` etc.)
6. Délimitez les étapes en formant des blocs d'instructions par l'utilisation de l'indentation.

<b> Ces règles sont générales, peu importe le langage de programmation utilisé. </b>

---
class: inverse, middle, center

# Les bonnes pratiques en programmation scientifique
<hr width="65%" size="0.3" color="orange" style="margin-top:-20px;"></hr>


---

# Les 10 commandements de la programmation

> <b>1.</b> Tu commenteras ton code pour que d'autres puissent le lire, le comprendre et le partager
---

# Les 10 commandements de la programmation

> <b>2.</b> Il faut prendre soin de l'environnement et nettoyer ses déchets
---

# Les 10 commandements de la programmation

> <b>3.</b> Ton script sera dur à avaler. Mieux vaut le découper
---

# Les 10 commandements de la programmation

> <b>4.</b> Plusieurs chiens s'appellent Fido, le tiens tu sauras le nommer
---

# Les 10 commandements de la programmation

> <b>5.</b> Des pas de bébés permettent aussi d'avancer
---

# Les 10 commandements de la programmation

> <b>6.</b> Un bon programmeur est paresseux. Les opérations répétées doivent être définies sous forme de fonctions
---

# Les 10 commandements de la programmation

> <b>7.</b> La vie est trop courte, ton code sera optimisé
---

# Les 10 commandements de la programmation

> <b>8.</b> Et un jour tu disparaîtras, alors assure toi que ton code soit reproductible
---

# Les 10 commandements de la programmation

> <b>9.</b> En tout puissant que tu es, le tirage au sort tu pourras répéter
---

# Les 10 commandements de la programmation

> <b>10.</b> Et dans le passé tu souhaiteras voyager, utilise le contrôle de versions
---

# Google R Style Rules

- Noms de `fichier`: se termine par .R
- `Identifiants`: variable.nom (or VariableNom), FonctionNom
- Longueur de `ligne`: maximum 80 caractères
- `Indentation`: deux espaces, pas de tabulations
- `Espacement`: placer des espaces autour des opérateurs binaires
- `Accolades { }`: s'ouvre sur la même ligne, se ferme sur une ligne indépendente (sauf pour `else`)
- `else` : Entourer `else` avec des accolades (`}else{`)
- `Affectation`: utiliser `<-`, pas `=`
- `Commentaire`: tous les commentaires sont précédés par `#` et suivit d'un espace
- `Fonction`: doivent avoir une section de commentaires

---
class: inverse, middle, center

# Exercice de la semaine
<hr width="65%" size="0.3" color="orange" style="margin-top:-20px;"></hr>

---

# Une situation qui peut arriver tous les jours

1. On jette en face de vous 5 lettres d'un jeu de scrabble
2. Un maniac vous demande d'écrire un programme permettant d'ordonner les 5 lettres

Prenez le temps de distinguer les étapes que vous réalisez lorsque vous triez les lettres. Essayez de les décrire sous forme de pseudo-code.

<b>Note</b>: cet exercice reviendra au cours 4, où vous programmerez cette fonction.
