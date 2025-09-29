# 📊 Prédiction des coûts ultimes par régression supervisée

Projet réalisé dans le cadre du Master 1 Econométrie, statistiques – Introduction à l’Apprentissage Supervisé.

## 🎯 Objectif
Développer un modèle de machine learning capable de prédire les coûts ultimes d’accidents à partir de données socio-professionnelles et temporelles. L’approche repose sur :
- Une préparation rigoureuse des données
- Un feature engineering avancé
- La comparaison de plusieurs modèles de régression

## 📁 Contenu du projet
- `ML_Notebook.ipynb` : Notebook principal contenant le code, les visualisations et les explications
- `train_etu.xlsx` : Jeu de données d'entraînement

## 🧪 Méthodologie

### 1. Prétraitement des données
- Imputation des valeurs manquantes (moyenne pour les numériques, mode pour les catégoriques)
- Détection et suppression des outliers via IQR et Isolation Forest
- Encodage des variables catégorielles (OneHotEncoder)
- Normalisation des variables numériques (StandardScaler)

### 2. Feature Engineering
- Transformation des dates (`date_diff`, `delai_communication`, `weekend_accident`)
- Création de variables quadratiques (`age²`, `cout_init²`)
- Termes d’interaction (`salaire_semaine × cout_init`, `age × cout_init`, etc.)
- Traitement du texte avec `TfidfVectorizer` sur la variable `description`

### 3. Modélisation
Modèles testés avec pipelines :
- Régression linéaire
- Arbre de décision
- Random Forest (500 arbres)
- Gradient Boosting (500 arbres)

### 4. Évaluation
- **RMSE** (Root Mean Squared Error)
- **R²** (Coefficient de détermination)
- Temps d’inférence

| Modèle              | RMSE     | R²     | Temps d'inférence |
|---------------------|----------|--------|-------------------|
| Régression linéaire | 10 268   | 0.5313 | 0.04 s            |
| Arbre de décision   | 16 423   | -0.198 | 0.02 s            |
| Random Forest       | 10 699   | 0.528  | 1.24 s            |
| Gradient Boosting   | **10 261** | **0.5320** | 0.04 s        |

## 🏆 Conclusion
Le modèle de **Gradient Boosting** est le plus performant en termes de précision. La régression linéaire reste une alternative simple et interprétable. L’arbre de décision nécessite des ajustements pour être compétitif.

## 📚 Technologies utilisées
- Python (pandas, numpy, scikit-learn, matplotlib, seaborn, plotly)
- PyOD pour la détection d’anomalies
- TfidfVectorizer pour le traitement du texte

