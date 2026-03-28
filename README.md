# 📈 Prévision de ventes e-commerce — Modélisation SARIMA

![Python](https://img.shields.io/badge/Python-3776AB?style=flat-square&logo=python&logoColor=white)
![Pandas](https://img.shields.io/badge/Pandas-150458?style=flat-square&logo=pandas&logoColor=white)
![Statsmodels](https://img.shields.io/badge/Statsmodels-10b981?style=flat-square)
![Scikit--learn](https://img.shields.io/badge/Scikit--learn-F7931E?style=flat-square&logo=scikitlearn&logoColor=white)
![Jupyter](https://img.shields.io/badge/Jupyter-F37626?style=flat-square&logo=jupyter&logoColor=white)
![Status](https://img.shields.io/badge/Status-Completed-22c55e?style=flat-square)

Prévision des ventes mensuelles d'un e-commerce par modélisation statistique. Décomposition de la série temporelle, sélection du modèle par grid search (64 combinaisons), prévisions SARIMA avec intervalles de confiance à 95%.

**Dataset :** Kaggle — SuperStore Sales Dataset

---

## 📝 Présentation

Modèle **SARIMA** (Seasonal AutoRegressive Integrated Moving Average) appliqué à des données de ventes e-commerce réelles. L'objectif : dépasser l'analyse descriptive pour anticiper les tendances futures et appuyer les décisions de stock et marketing.

Après 10 ans dans le business e-commerce avec Google Analytics ouvert chaque matin, ce projet traduit cette intuition terrain en méthode statistique rigoureuse.

---

## 🎯 Objectifs

1. **Analyse exploratoire des données** : Identifier les produits, régions et segments clients les plus performants
2. **Analyse de corrélation** : Tester les relations entre les ventes et différentes dimensions business
3. **Décomposition des séries temporelles** : Séparer la tendance, la saisonnalité et les résidus
4. **Prévision** : Construire un modèle SARIMA pour prédire les ventes des 7 prochains jours

---

## 🔍 Résultats clés

### Insights business

- Les **produits technologiques** génèrent le chiffre d'affaires le plus élevé (33 % des ventes totales)
- **La Californie et New York** sont les États les plus performants
- La **livraison standard** représente 60 % du chiffre d'affaires
- Le **segment Consumer** représente plus de 50 % des ventes totales

---

### Analyse statistique

- **Test de stationnarité** : Le test ADF confirme que la série est stationnaire (p-value < 0,05)
- **Saisonnalité** : Présence d'un cycle saisonnier clair sur 12 mois
- **Sélection du modèle** : SARIMA(1,1,1)(1,1,1,12) sélectionné via recherche par grille (AIC le plus faible : 20738,35)
- **Performance du modèle** : RMSE = 267,66 (taux d'erreur ±12 %)

---

### Analyse de corrélation

Corrélations testées entre les ventes et :

- Segments clients → Pas de corrélation forte
- Catégories de produits → Pas de corrélation forte
- Modes de livraison → Pas de corrélation forte

**Conclusion** : D'autres facteurs (prix, saisonnalité, promotions) semblent avoir un impact plus significatif sur les ventes.

---

## 🛠️ Stack technique

- **Python 3.8+**
- **Pandas** – Manipulation des données
- **NumPy** – Calculs numériques
- **Matplotlib & Seaborn** – Visualisation des données
- **Statsmodels** – Analyse de séries temporelles & SARIMA
- **Scikit-learn** – Évaluation du modèle (RMSE)

---

## 📊 Méthodologie

### 1. Préparation des données

- Conversion des dates au format datetime
- Gestion des valeurs manquantes (Code postal)
- Tri des données par date de commande
- Rééchantillonnage en moyennes journalières avec interpolation linéaire

---

### 2. Analyse exploratoire

- Ventes par catégorie, produit, État et client
- Chiffre d'affaires par mode de livraison
- Top 10 produits et clients

---

### 3. Analyse de séries temporelles

```python
# Test de stationnarité
Statistique ADF : -20.81 (p-value : 0.0)
→ La série est stationnaire

# Décomposition
- Tendance : Croissance stable dans le temps
- Saisonnalité : Cycle détecté sur 12 mois
- Résidus : Bruit aléatoire
```

---

### 4. Modèle SARIMA

```python
# Recherche par grille testant 64 combinaisons de paramètres
Meilleur modèle : SARIMA(1,1,1)(1,1,1,12)
AIC : 20738.35
RMSE : 267.66
```

---

### 5. Prévision

Prévision sur 7 jours avec intervalles de confiance :

- 2019-01-01 : 241 $
- 2019-01-02 : 244 $
- 2019-01-03 : 229 $
- 2019-01-04 : 196 $
- 2019-01-05 : 254 $ (pic)
- 2019-01-06 : 223 $
- 2019-01-07 : 229 $

---

## 💡 Recommandations business

Sur la base de cette analyse :

1. **Planification des stocks**
→ Anticiper les pics de ventes sur les produits technologiques

2. **Campagnes marketing**
→ Concentrer les dépenses publicitaires pendant les périodes de fort trafic (les dimanches montrent +40 % de ventes)

3. **Focus régional**
→ Prioriser la Californie et New York pour les promotions

4. **Fidélisation client**
→ Cibler le segment Consumer (50 %+ du chiffre d'affaires) avec des programmes de fidélité

5. **Stratégie de livraison**
→ Optimiser la livraison standard (60 % des commandes)

---

## 📁 Structure du projet

ecommerce-sales-analysis-sarima/
│
├── README.md
├── sales_forecasting_sarima.ipynb
└── data/
  └── train.csv

---

## 🚀 Lancer le projet

1. Cloner le dépôt

```
git clone https://github.com/Heltondsm/ecommerce-sales-analysis-sarima.git
cd ecommerce-sales-analysis-sarima
```

2. Installer les dépendances

```
pip install pandas numpy matplotlib seaborn statsmodels scikit-learn jupyter
```

3. Lancer le notebook

```
jupyter notebook sales_forecasting_sarima.ipynb
```

---

## 📈 Exemples de visualisations

- Ventes par catégorie
→ Les produits technologiques dominent avec 836K $ (33 % du total)

- Décomposition des séries temporelles
→ Tendance claire et saisonnalité sur 12 mois

- Diagnostics SARIMA
→ Résidus proches d'une distribution normale

- Prévision sur 7 jours
→ Prédictions avec intervalle de confiance à 95 %

---

## 🎓 Compétences démontrées

- Analyse exploratoire des données (EDA)
- Nettoyage et prétraitement des données
- Tests statistiques (ADF)
- Décomposition de séries temporelles
- Modélisation SARIMA
- Optimisation des hyperparamètres (Grid Search)
- Validation de modèle (RMSE, diagnostics)
- Visualisation de données
- Traduction d'analyses en recommandations business

---

## 📫 Contact

**Helton Dos Santos Moreira**
Data Analyst | 10 ans d'expérience Business (retail + e-commerce) → Reconversion Data

- 📧 Email : heltonmail8@gmail.com
- 💼 LinkedIn : [in/helton-dsm-data](https://linkedin.com/in/helton-dsm-data)
- 🐙 GitHub : [Heltondsm](https://github.com/Heltondsm)

---

## 🔗 Autres projets

- [Exploration SQL — Portefeuille assurances habitation](https://github.com/Heltondsm/sql-assurances-habitation) — 50K+ contrats, jointures, agrégations, segmentation géographique
- [Sous-nutrition mondiale — Données FAO](https://github.com/Heltondsm/etude-sante-publique-fao) — Python, 4 datasets, 528M personnes, conclusion : problème de distribution
- [Performance e-commerce — Le Grand Marché](https://github.com/Heltondsm/analyse-ventes-ecommerce) — Excel, KPIs, trafic ×30, segmentation 2 profils

---

**Projet réalisé en juin 2025**
