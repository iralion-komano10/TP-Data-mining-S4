# TP4 Individuel - Data Mining S4

## Dataset Titanic (Kaggle)

---

## Objectifs
- Charger le dataset Titanic
- Afficher les 10 premières lignes
- Calculer les statistiques descriptives
- Grouper les données par classe et sexe
- Identifier et traiter les valeurs manquantes

---

## Code notebook

```python
import pandas as pd

# Charger le dataset
df = pd.read_csv("titanic.csv")

# Afficher les 10 premières lignes
print(df.head(10))

# Taille du dataset
print(df.shape)

# Informations générales
print(df.info())

# Statistiques descriptives
print(df.describe())

# Moyenne de survie par classe
print(df.groupby('Pclass')['Survived'].mean())

# Moyenne de survie par sexe
print(df.groupby('Sex')['Survived'].mean())

# Valeurs manquantes
print(df.isnull().sum())

# Remplacement des valeurs manquantes
df['Age'] = df['Age'].fillna(df['Age'].median())
df['Embarked'] = df['Embarked'].fillna(df['Embarked'].mode()[0])

# Vérification finale
print(df.isnull().sum())
