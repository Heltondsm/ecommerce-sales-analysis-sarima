# 📈 Prévision de ventes e-commerce : modélisation SARIMA

![Python](https://img.shields.io/badge/Python-3776AB?style=flat-square&logo=python&logoColor=white)
![Pandas](https://img.shields.io/badge/Pandas-150458?style=flat-square&logo=pandas&logoColor=white)
![Statsmodels](https://img.shields.io/badge/Statsmodels-10b981?style=flat-square)
![Scikit--learn](https://img.shields.io/badge/Scikit--learn-F7931E?style=flat-square&logo=scikitlearn&logoColor=white)
![Jupyter](https://img.shields.io/badge/Jupyter-F37626?style=flat-square&logo=jupyter&logoColor=white)
![Status](https://img.shields.io/badge/Status-Completed-22c55e?style=flat-square)

Quatre ans de ventes d'un e-commerce américain analysées, puis un modèle **SARIMA choisi parmi 64 combinaisons** pour prévoir les ventes des jours suivants. L'analyse montre où se fait le chiffre d'affaires : **la technologie, la Californie et New York, et le segment des particuliers.**

**Données :** SuperStore Sales Dataset (Kaggle), 9 800 lignes de commandes, de 2015 à 2018.

---

## 📖 Le problème

Un e-commerce veut passer d'une lecture du passé à une anticipation de ses ventes, pour mieux préparer ses stocks et ses campagnes. Il faut d'abord savoir où se fait le chiffre d'affaires, puis construire une prévision fiable.

---

## 🛠️ Ma solution

1. **Préparation des données** : dates converties, valeurs manquantes traitées (code postal), commandes triées dans le temps
2. **Analyse exploratoire** : ventes par catégorie, produit, État, client, segment et mode de livraison
3. **Analyse de la série temporelle** : test de stationnarité, décomposition en tendance, saisonnalité et résidus
4. **Choix du modèle** : 64 combinaisons de paramètres SARIMA comparées sur leur AIC
5. **Prévision** des ventes quotidiennes, avec leur intervalle de confiance

---

## 🔍 Résultats clés

### 1️⃣ Où se fait le chiffre d'affaires

Sur 2,26 millions de dollars de ventes :

| Dimension | Ce qui domine | Part des ventes |
|---|---|---|
| Catégorie | Technologie | **36,6 %** |
| Segment | Particuliers (Consumer) | **50,8 %** |
| Mode de livraison | Livraison standard | **59,3 %** |
| État | Californie, puis New York | 446 000 $ et 306 000 $ |

### 2️⃣ Une série prête à être modélisée

Le test de Dickey-Fuller augmenté confirme que la série est stationnaire (statistique de -20,81, p-value de 0) : elle peut être modélisée directement.

### 3️⃣ Le meilleur modèle sur 64

```python
p = d = q = range(0, 2)
pdq = list(itertools.product(p, d, q))
seasonal_pdq_comb = [(i[0], i[1], i[2], 12) for i in list(itertools.product(p, d, q))]
# 8 combinaisons de tendance x 8 combinaisons saisonnières = 64 modèles comparés
```

Le modèle retenu, **SARIMA(1,1,1)(1,1,1,12)**, a l'AIC le plus faible des 64 : **20 079,17**. Son erreur quadratique moyenne (RMSE) est de **267,66**.

### 4️⃣ La prévision

Les ventes sont modélisées en montant moyen par jour. Pour les premiers jours de janvier 2019, le modèle prévoit **entre 196 et 254 dollars de vente moyenne selon le jour**, avec leur intervalle de confiance.

---

## 💡 Ce que ça permet de décider

- **Stocks** : sécuriser en priorité la technologie, première catégorie du chiffre d'affaires
- **Promotions** : concentrer l'effort sur la Californie et New York
- **Fidélisation** : cibler les particuliers, qui font plus de la moitié des ventes
- **Logistique** : soigner la livraison standard, qui porte près de 60 % du chiffre d'affaires

---

## 🛠️ Stack technique

- **Python** · **Pandas** · **NumPy**
- **Matplotlib** et **Seaborn** : visualisation
- **Statsmodels** : test de stationnarité, décomposition et SARIMA
- **Scikit-learn** : calcul de l'erreur (RMSE)

---

## 📁 Structure du projet

```
ecommerce-sales-analysis-sarima/
├── README.md
├── sales_forecasting_sarima.ipynb
└── data/
    └── train.csv
```

---

## 🚀 Lancer le projet

```bash
git clone https://github.com/Heltondsm/ecommerce-sales-analysis-sarima.git
cd ecommerce-sales-analysis-sarima
pip install pandas numpy matplotlib seaborn statsmodels scikit-learn jupyter
jupyter notebook sales_forecasting_sarima.ipynb
```

---

## 📧 Contact

**Helton Dos Santos Moreira**
Data Analyst / Data Engineer | 10 ans d'expérience business (retail et e-commerce)

- 📧 Email : heltonmail8@gmail.com
- 💼 LinkedIn : [in/helton-dsm-data](https://linkedin.com/in/helton-dsm-data)
- 🐙 GitHub : [Heltondsm](https://github.com/Heltondsm)

---

## 🔗 Autres projets

- [CRM data et agents IA : centraliser offres, contacts et échanges](https://github.com/Heltondsm/crm-data-agents-ia), PostgreSQL alimenté par des API, collecte Python planifiée, offres notées par IA, 2 168 relations LinkedIn analysées
- [Tableau de bord Power BI : portefeuille de projets](https://github.com/Heltondsm/powerbi-portefeuille-projets-rls), 104 projets dans 52 pays, sécurité au niveau des lignes sur 3 rôles, 25 mesures DAX
- [Audit données catalogue : e-commerce vins](https://github.com/Heltondsm/python-audit-donnees-catalogue), 3 sources réconciliées, 9 anomalies, 276 859 € de stock valorisé
- [Tendances du streaming musical](https://github.com/Heltondsm/analyse-streaming-musical), 114 000 morceaux, tests statistiques et calendrier de sortie

---
