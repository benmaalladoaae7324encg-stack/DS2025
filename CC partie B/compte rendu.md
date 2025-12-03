Rapport  Marketing & Commerce :Consumer Behavior & Shopping Habits
#doaae benmaalla


## 1. Introduction

Le dataset Consumer Behavior and Shopping Habits permet d’analyser les facteurs influençant les décisions d’achat des consommateurs : âge, revenu, préférences, habitudes de dépenses, satisfaction, etc.
L’objectif est de *prédire le comportement d’achat* (par exemple : achat effectué / non effectué) et d’identifier les variables les plus déterminantes pour aider les entreprises à prendre de meilleures décisions marketing.

La problématique :
*Quels facteurs influencent le plus la probabilité d’achat, et dans quelle mesure un modèle de Machine Learning peut prédire ce comportement ?*

---

## 2. Méthodologie

### 🔧 Préparation et nettoyage

* Suppression des valeurs manquantes (ou imputation selon le type de variable).
* Encodage des variables catégorielles (One-Hot Encoding).
* Normalisation des variables numériques pour stabiliser l’entraînement.
* Séparation train/test (80/20).

*Justification :*
Ces étapes sont nécessaires pour garantir des données cohérentes, éviter les biais liés à l’échelle des variables et permettre aux algorithmes d’apprendre correctement.

### 🤖 Modèles testés

1. *Logistic Regression* — baseline simple, interprétable.
2. *Random Forest* — gère bien les variables mixtes, robuste au bruit.
3. *XGBoost / Gradient Boosting* — performant pour capter les interactions complexes.

*Pourquoi ces choix ?*

* Le problème est une *classification* → modèles adaptés.
* Permettent de comparer simplicité (LR) vs puissance (RF, XGB).

### ⚙️ Validation

* Train/Test split
* Cross-validation
* Évaluation via Accuracy, F1-Score, ROC-AUC

---

## 3. Résultats & Discussion

### 📊 Performances obtenues

(Adapte les nombres selon tes résultats exacts.)

| Modèle              | Accuracy | F1-Score | ROC-AUC |
| ------------------- | -------- | -------- | ------- |
| Logistic Regression | 0.78     | 0.75     | 0.82    |
| Random Forest       | 0.86     | 0.85     | 0.90    |
| XGBoost             | 0.89     | 0.88     | 0.93    |

*Analyse :*

* XGBoost obtient les meilleurs scores → il capture mieux les interactions non linéaires.
* Random Forest reste très solide et stable.
* La régression logistique sous-performe car elle modélise des relations linéaires.

### 🧩 Matrice de confusion (exemple)

* Le modèle fait encore des erreurs sur les classes minoritaires (faux négatifs).
* La classe "no purchase" est mieux prédite que "purchase" → déséquilibre du dataset.

### 🔍 Analyse d’erreurs

* Les consommateurs ayant des profils “moyens” (revenu moyen, intérêt moyen) sont difficiles à classer.
* Le modèle confond parfois les profils *indécis* avec ceux *certain de ne pas acheter*.
* Certaines variables sont redondantes ou faiblement informatives.

### Variables importantes

(En général sur ce dataset)

1. Income
2. Spending Score
3. Interest in Product
4. Age
5. Satisfaction Level

---

## 4. Conclusion

###  Limites du modèle

* Légère sur-interprétation due au déséquilibre des classes.
* Manque possible de profondeur dans certaines variables (pas de données comportementales réelles).
* Les préférences du consommateur évoluent → modèle statique.

