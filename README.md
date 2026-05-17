# Manifold Learning for Geometric Shape Deformations

## Analyse géométrique de déformations de formes planes par apprentissage de variétés et réduction de dimension

# Aperçu du projet

Ce projet explore l’analyse géométrique de formes planes à l’aide de :

- géométrie riemannienne,
- apprentissage de variétés (*manifold learning*),
- réduction de dimension,
- statistiques sur variétés.

Le dataset contient **51 formes 2D** représentant une transformation géodésique progressive entre deux formes de référence.

Les données sont étudiées sur la **variété de Stiefel**, un espace riemannien de matrices orthonormées.

---

# Objectifs

- Étudier la géométrie des formes
- Manipuler les espaces tangents
- Utiliser les applications logarithme et exponentielle
- Calculer une moyenne de Fréchet
- Comparer des méthodes de réduction de dimension
- Visualiser des trajectoires géodésiques

---

# Structure mathématique

Chaque forme est représentée par :

$$
A \in \mathbb{R}^{100 \times 2}
$$

avec la contrainte :

$$
A^T A = I
$$

Les données appartiennent donc à :

$$
\mathrm{St}(100,2)
$$

où :

- les géodésiques sont courbes,
- les distances sont riemanniennes,
- les moyennes euclidiennes ne sont plus adaptées.

---

# Dataset

Le fichier :

```text
Shapes_Gr.mat
```

contient :

- 51 formes,
- 100 points 2D par forme,
- un chemin géodésique entre deux formes extrêmes.

Transformation observée :

- \( t = 0 \) → forme papillon
- \( t = 1 \) → forme fleur

---

# Méthodologie

## 1. Exploration des données

- Chargement du dataset MATLAB
- Vérification des contraintes d’orthonormalité
- Visualisation des formes géométriques

---

## 2. Moyenne de Fréchet

Calcul de la moyenne géométrique sur la variété :

$$
\mu = \arg\min_{Y \in \mathcal{M}} \sum_i d^2(Y,X_i)
$$

La moyenne représente la forme centrale du chemin géodésique.

---

## 3. Projection tangentielle

Projection locale des formes via :

$$
V_i = \log_\mu(X_i)
$$

Reconstruction avec :

$$
X_i = \exp_\mu(V_i)
$$

Contrainte tangentielle :

$$
A^T V + V^T A = 0
$$

---

# Réduction de dimension

## Méthodes linéaires

### PCA

- Analyse en composantes principales
- Projection des vecteurs tangents

### MDS

- Préservation des distances entre points

---

## Méthodes non linéaires

### Kernel PCA (RBF)

Projection non linéaire via noyau gaussien.

### Kernel PCA Polynomial

Projection polynomiale de degré 2.

### Isomap

Préservation des distances géodésiques globales.

### t-SNE

Préservation des voisinages locaux.

### LLE

Locally Linear Embedding.

### Laplacian Eigenmaps

Méthode spectrale basée sur le Laplacien du graphe.

---

# Résultats principaux

## Observations géométriques

- Vérification des contraintes de Stiefel
- Très faible erreur numérique des opérations log/exp
- Reconstruction géodésique stable

---

## Réduction de dimension

### PCA et MDS

- Très bonne préservation locale
- Structure tangentielle bien capturée

### Méthodes non linéaires

- Kernel PCA RBF : distorsions plus importantes
- Kernel Polynomial : bon compromis
- Isomap et t-SNE : meilleure structure globale

---

# Technologies utilisées

- Python
- NumPy
- SciPy
- Matplotlib
- Scikit-learn
- Geomstats

---

# Installation

## Cloner le projet

```bash
git clone https://gitlab.com/maramnasrr/manifold-learning-shape-analysis.git
cd manifold-learning-shape-analysis
```

## Installer les dépendances

```bash
pip install numpy scipy matplotlib scikit-learn geomstats
```

---

# Perspectives

- Génération de nouvelles formes
- Interpolation géodésique
- Classification de formes
- Clustering riemannien
- Deep Learning géométrique

---

# Conclusion

Ce projet illustre l’intérêt des approches riemanniennes pour l’analyse de données géométriques complexes vivant sur des espaces non euclidiens.

Il combine :

- géométrie différentielle,
- apprentissage automatique,
- réduction de dimension,
- statistiques sur variétés.
