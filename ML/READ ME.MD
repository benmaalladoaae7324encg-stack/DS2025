#DOAAE BENMMAALLA
#  Classification de la Qualité du Vin avec KNN

## 1. Introduction

Ce projet utilise l'algorithme des K plus proches voisins (KNN) pour classifier la qualité du vin blanc à partir du dataset UCI Wine Quality. L'objectif est de prédire si un vin est de bonne ou mauvaise qualité en fonction de ses propriétés physicochimiques.

## 2. Dataset

### 2.1 Source des données
- **Dataset**: Wine Quality (UCI Machine Learning Repository)
- **Type**: Vin blanc portugais (Vinho Verde)
- **Nombre d'instances**: 4898
- **Nombre de caractéristiques**: 11
- **Variable cible**: Qualité (score de 0 à 10)

### 2.2 Caractéristiques

Les 11 variables physicochimiques sont :
1. Acidité fixe (fixed acidity)
2. Acidité volatile (volatile acidity)
3. Acide citrique (citric acid)
4. Sucre résiduel (residual sugar)
5. Chlorures (chlorides)
6. Dioxyde de soufre libre (free sulfur dioxide)
7. Dioxyde de soufre total (total sulfur dioxide)
8. Densité (density)
9. pH
10. Sulfates
11. Alcool (alcohol)

### 2.3 Prétraitement

**Binarisation de la variable cible** :
- Mauvaise qualité (y=0) : qualité ≤ 5
- Bonne qualité (y=1) : qualité > 5

## 3. Analyse Exploratoire

### 3.1 Distribution des classes

```
Qualité 6: 2198 échantillons
Qualité 5: 1457 échantillons
Qualité 7: 880 échantillons
Qualité 8: 175 échantillons
Qualité 4: 163 échantillons
Qualité 3: 20 échantillons
Qualité 9: 5 échantillons
```

### 3.2 Visualisations

- **Boxplots** : Montrent la distribution de chaque variable
- **Heatmap de corrélation** : Visualise les corrélations entre les différentes caractéristiques

## 4. Méthodologie

### 4.1 Division des données

Le dataset a été divisé en trois ensembles :
- **Ensemble d'entraînement (Xa, Ya)** : ~33.3% des données
- **Ensemble de validation (Xv, Yv)** : ~33.3% des données
- **Ensemble de test (Xt, Yt)** : ~33.3% des données

La stratification a été appliquée pour maintenir les proportions des classes dans chaque ensemble.

### 4.2 Sélection du modèle

**Algorithme** : K-Nearest Neighbors (KNN)

**Recherche d'hyperparamètre** :
- Valeurs de k testées : [1, 3, 5, 7, 9, ..., 35] (18 valeurs)
- Méthode : Validation sur ensemble de validation
- Critère : Minimisation de l'erreur de classification

## 5. Résultats

### 5.1 Performance sur l'ensemble d'entraînement

```
Erreurs d'entraînement : [0, 0, 0, ..., 0]
```
Toutes les valeurs de k donnent une erreur d'entraînement nulle, ce qui suggère un **surapprentissage**.

### 5.2 Performance sur l'ensemble de validation

```
Erreurs de validation : [0, 0, 0, ..., 0]
```
 **Résultat suspect** : Toutes les erreurs de validation sont nulles.

### 5.3 Hyperparamètre optimal

- **k* = 1** (meilleure valeur de k)
- **Erreur de validation minimale = 0.0**

### 5.4 Performance finale sur l'ensemble de test

```
Erreur de test = 0.0
```

## 6. Analyse Critique

### 6.1 Problèmes identifiés

1. **Résultats suspects** : Une erreur nulle sur tous les ensembles est hautement improbable
2. **Possible fuite de données** : Les ensembles de validation et test pourraient contenir des doublons
3. **Problème de binarisation** : La transformation de la variable cible pourrait être trop simpliste
4. **Surapprentissage évident** : k=1 suggère un surapprentissage sévère

### 6.2 Recommandations

Pour améliorer l'analyse :

1. **Vérifier l'intégrité des données** :
   - Supprimer les éventuels doublons
   - Vérifier la séparation train/validation/test

2. **Normalisation** :
   ```python
   from sklearn.preprocessing import StandardScaler
   scaler = StandardScaler()
   Xa_scaled = scaler.fit_transform(Xa)
   ```

3. **Cross-validation** :
   ```python
   from sklearn.model_selection import cross_val_score
   scores = cross_val_score(clf, X, Y, cv=5)
   ```

4. **Métriques supplémentaires** :
   - Matrice de confusion
   - Précision, rappel, F1-score
   - Courbe ROC et AUC

## 7. Code Principal

```python
# Import et préparation
from ucimlrepo import fetch_ucirepo
wine_quality = fetch_ucirepo(id=186)
X = wine_quality.data.features
Y = [0 if val <= 5 else 1 for val in wine_quality.data.targets]

# Division des données
from sklearn.model_selection import train_test_split
Xa, Xt, Ya, Yt = train_test_split(X, Y, test_size=1/3, stratify=Y)
Xa, Xv, Ya, Yv = train_test_split(Xa, Ya, test_size=0.5, stratify=Ya)

# Recherche du meilleur k
from sklearn.neighbors import KNeighborsClassifier
k_vector = np.arange(1, 37, 2)
for k in k_vector:
    clf = KNeighborsClassifier(n_neighbors=k)
    clf.fit(Xa, Ya)
    # Évaluation...

# Modèle final
clf = KNeighborsClassifier(n_neighbors=k_star)
clf.fit(Xa, Ya)
Ypred_test = clf.predict(Xt)
```

## 8. Conclusion

Bien que les résultats montrent une performance parfaite (erreur = 0), cela indique très probablement un **problème dans l'implémentation** plutôt qu'un véritable succès. Une analyse plus approfondie avec des techniques de validation croisée et une vérification de l'intégrité des données est nécessaire pour obtenir des résultats fiables.


