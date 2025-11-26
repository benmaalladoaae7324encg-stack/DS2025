# Compte-rendu : College Marks Data Analysis and Grade Prediction

## 📄 Résumé du notebook

- Le projet analyse un jeu de données “College Marks” : notes des étudiants, assiduité, etc. ([Kaggle](https://www.kaggle.com/code/devraai/college-marks-data-analysis-and-grade-prediction))
- L’auteur explore les distributions des notes et des motifs d’assiduité pour repérer des tendances et corrélations.
- Objectif principal : **prédire la note finale** ou la réussite d’un étudiant via des modèles de Machine Learning.

---

## 🔧 Types de régressions proposées et leurs objectifs

### • Régression linéaire

- Estime une relation linéaire entre variables explicatives et variable cible continue.
- Variable cible : note finale (ex. "G3").
- Modèle :
  ```
  note ≈ β0 + β1·feature1 + β2·feature2 + … + ε
  ```
- Intérêt : prédiction simple et interprétable si relation linéaire.

### • Régression logistique

- Utilisée pour des variables cibles binaires (ex : réussite / échec).
- Modélise la **probabilité** d’appartenance à une classe.
- Utile si on transforme la note finale en variable catégorielle.

---

## ✅ Avantages & limites

| Modèle | Avantages | Limites |
|--------|-----------|---------|
| Régression linéaire | Prédit la note précise, coefficients interprétables | Suppose linéarité, sensible aux outliers, hypothèses strictes |
| Régression logistique | Prédit probabilité d’un événement, adaptée pour classification | Ne prédit pas la note exacte, seuil de classification arbitraire |

---

## 🎯 Analyse

- Pour prédire une note exacte → **régression linéaire**.
- Pour prédire réussite / échec → **régression logistique**.
- Pour améliorer la prédiction, combiner EDA + modèles plus puissants (forêts aléatoires, boosting).

---

## 💡 Recommandations

- Régression linéaire : vérifier linéarité, absence de multicolinéarité, distribution des résidus.
- Régression logistique : binariser les notes, analyser les probabilités.
- Toujours effectuer une **EDA complète** et sélectionner les variables pertinentes.

---