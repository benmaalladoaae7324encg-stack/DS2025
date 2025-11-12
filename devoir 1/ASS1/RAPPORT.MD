# Benmaalla doaae
<img src="DOAE.jfif" style="height:464px;margin-right:432px"/>

#Thème: l’application de la science des données et de l’apprentissage automatique sur un jeu pour analyser et prédire des résultats.

#Descriptif:Le dataset Tic‑Tac‑Toe Endgame a été créé par David W. Aha en 1991 et est disponible sur le UCI Machine Learning Repository. Il contient 958 positions finales du jeu classique Tic‑Tac‑Toe sur un plateau 3×3, où chaque case peut être X, O ou vide. La variable cible indique si le joueur X a gagné ou non.

#Ce dataset est destiné à l’apprentissage automatique et à la science des données, pour analyser les configurations de jeu et prévoir les résultats finaux. Il sert principalement à enseigner et tester des algorithmes de classification, comme les arbres de décision, k-NN ou les réseaux de neurones, dans un contexte simple et pédagogique.

# Compte-Rendu : Dataset Tic‑Tac‑Toe Endgame

## 1. Contexte
Le dataset **Tic‑Tac‑Toe Endgame** a été créé par **David W. Aha en 1991** et est disponible sur le **UCI Machine Learning Repository**. Il contient **958 positions finales** du jeu classique Tic‑Tac‑Toe sur un plateau 3×3.

Le but est d'utiliser la **science des données et l’apprentissage automatique** pour **analyser les configurations de jeu** et **prédire si le joueur X gagne ou non**.

---

## 2. Variables du dataset

| Type | Nom | Description |
|------|-----|-------------|
| Feature | top-left-square | Contenu de la case (x, o, b) |
| Feature | top-middle-square | Contenu de la case (x, o, b) |
| Feature | top-right-square | Contenu de la case (x, o, b) |
| Feature | middle-left-square | Contenu de la case (x, o, b) |
| Feature | middle-middle-square | Contenu de la case (x, o, b) |
| Feature | middle-right-square | Contenu de la case (x, o, b) |
| Feature | bottom-left-square | Contenu de la case (x, o, b) |
| Feature | bottom-middle-square | Contenu de la case (x, o, b) |
| Feature | bottom-right-square | Contenu de la case (x, o, b) |
| Target | target | Indique si X a gagné (`positive`) ou non (`negative`) |

---

## 3. Objectifs
- Analyser les positions finales du jeu.
- Comprendre comment chaque case influence la victoire.
- Construire des **modèles de classification** pour prédire le résultat final.
- Visualiser les données pour identifier des **patterns et relations entre les cases**.

---

## 4. Analyses et visualisations

### 4.1 Répartition des cases
- Chaque case peut contenir `x`, `o` ou `b` (vide).  
- Exemple : `top-left-square` est répartie sur les 958 instances, donnant une idée des positions de départ.

### 4.2 Répartition de la cible
- La variable cible montre la proportion de victoires de X (`positive`) et non-victoires (`
