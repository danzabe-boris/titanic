# titanic
README.md pour le projet Titanic Database Analysis

Notre objectif dans cette analyse de la base de données est de prédire si un passager aurait survécu au naufrage du Titanic avec une précision de 80%.

## Analyse exploratoire de la base de données Titanic

Nous avons utilisé les packages suivants pour effectuer notre analyse :

```python
import numpy as np
import pandas as pd 
import seaborn as sns
import matplotlib.pyplot as plt
```

### Description de la base de données

La base de données contient 891 observations et 11 variables. Les variables sont définies comme suit :

* survival : Survie (0 = Non, 1 = Oui)
* pclass : Classe de billet (1 = 1ère, 2 = 2ème, 3 = 3ème)
* sex : Sexe 
* age : Âge en années
* sibsp : Nombre de frères et soeurs / conjoints à bord du Titanic
* parch : Nombre de parents / enfants à bord du Titanic
* ticket : Numéro de billet
* fare : Prix du billet
* cabin : Numéro de cabine
* embarked : Port d'embarquement (C = Cherbourg, Q = Queenstown, S = Southampton)

Nous avons supprimé les variables "Name" et "Ticket", car elles ne sont pas pertinentes pour notre analyse.

```python
data = data.drop(["Name", "Ticket"], axis = 1)
```

Nous avons également converti les variables qualitatives déguisées en variables qualitatives. En particulier, nous avons converti les variables Survived, Pclass, Sibsp et Parch.

```python
data.Survived = data.Survived.astype("object")
data.Pclass = data.Pclass.astype("object")
data.SibSp = data.SibSp.astype("object")
data.Parch = data.Parch.astype("object")
```

Le pourcentage de valeurs manquantes dans la base de données est d'environ 1 %. La variable "Cabin" a plus de 77 % de valeurs manquantes et ne nous donne pas beaucoup d'informations utiles pour notre analyse.

```python
data = data.drop("Cabin", axis = 1)
```

### Analyse fondamentale

#### Visualisation de la variable cible

Nous avons examiné la variable Survived et avons constaté que 62 % des passagers sont décédés et 38 % ont survécu.

```python
survived = data.Survived.value_counts()
survived
```

Nous avons également utilisé une histogramme pour visualiser la distribution de la variable Survived.

```python
sns.histplot(data = data, x="Survived")
```

#### Visualisation des relations entre la variable cible et les variables

##### Variables quantitatives

Nous avons tracé des graphiques pour visualiser la relation entre les variables Survived et Age, ainsi que Survived et Fare.

```python
sns.barplot(data = data, x="Survived", y="Age")
sns.boxplot(data = data, y="Age", x="Survived")
sns.barplot(data = data, x="Survived", y="Fare")
```

## Conclusion

Dans cette analyse, nous avons exploré la base de données Titanic et avons utilisé des techniques de visualisation pour comprendre les relations entre les différentes variables et la variable cible. Nous avons également préparé les données pour l'analyse en supprimant des variables inutiles et en convertissant les variables en variables qualitatives. Notre
