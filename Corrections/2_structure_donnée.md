## Corrections - Chapitre 2 : Structures de Données

### Question 1 : Listes en Python
**Réponse correcte : C) Les listes sont mutables (modifiables) alors que les tuples sont immuables (non modifiables)**

La principale différence entre les listes et les tuples en Python est leur mutabilité. Les listes peuvent être modifiées après leur création (ajout, suppression, modification d'éléments), tandis que les tuples sont immuables et ne peuvent pas être modifiés une fois créés. Les deux structures peuvent contenir des éléments de n'importe quel type et sont indexées à partir de 0.

**Exemple :**
```python
# Liste (mutable)
ma_liste = [1, 2, 3]
ma_liste[0] = 10      # Modification possible
ma_liste.append(4)    # Ajout possible
print(ma_liste)       # Affiche: [10, 2, 3, 4]

# Tuple (immuable)
mon_tuple = (1, 2, 3)
# mon_tuple[0] = 10   # Erreur: TypeError: 'tuple' object does not support item assignment
# mon_tuple.append(4) # Erreur: AttributeError: 'tuple' object has no attribute 'append'
print(mon_tuple)      # Affiche: (1, 2, 3)
```

### Question 2 : Opérations sur les listes
**Réponse correcte : A) `[1, 2, 3, 1, 2, 3]`**

L'opérateur `*` appliqué à une liste crée une nouvelle liste qui répète les éléments de la liste originale. Ainsi, `[1, 2, 3] * 2` répète la liste deux fois, ce qui donne `[1, 2, 3, 1, 2, 3]`. Cela ne multiplie pas les valeurs individuelles.

**Exemple :**
```python
liste1 = [1, 2, 3]
liste2 = liste1 * 2
liste3 = [x * 2 for x in liste1]  # Pour multiplier chaque élément

print(liste2)  # Affiche: [1, 2, 3, 1, 2, 3]
print(liste3)  # Affiche: [2, 4, 6]

# Autres exemples d'opérations sur les listes
print([1, 2] + [3, 4])  # Concaténation: [1, 2, 3, 4]
print(["a"] * 3)        # Répétition: ["a", "a", "a"]
```

### Question 3 : Modification de listes
**Réponse correcte : B) Elle ajoute un élément à la fin de la liste**

La méthode `append()` ajoute l'élément spécifié à la fin de la liste. Pour ajouter un élément à un index spécifique, on utiliserait `insert()`. Pour fusionner deux listes, on utiliserait `extend()` ou l'opérateur `+`.

**Exemple :**
```python
# Différentes méthodes de modification de listes
fruits = ["pomme", "banane"]

# append() - Ajoute un élément à la fin
fruits.append("orange")
print(fruits)  # Affiche: ["pomme", "banane", "orange"]

# insert() - Ajoute un élément à un index spécifique
fruits.insert(1, "fraise")
print(fruits)  # Affiche: ["pomme", "fraise", "banane", "orange"]

# extend() - Ajoute tous les éléments d'un itérable
fruits.extend(["kiwi", "mangue"])
print(fruits)  # Affiche: ["pomme", "fraise", "banane", "orange", "kiwi", "mangue"]
```

### Question 4 : Tuples en Python
**Réponse correcte : C) `tuple = (1,)` et D) `tuple = 1,`**

Les deux syntaxes C et D sont correctes pour créer un tuple à un seul élément. La virgule est nécessaire pour distinguer un tuple contenant un seul élément d'une simple expression entre parenthèses. Sans la virgule, `(1)` est simplement interprété comme l'entier 1.

**Exemple :**
```python
# Création de tuples à un seul élément
tuple1 = (1,)
tuple2 = 1,
non_tuple = (1)

print(type(tuple1))   # Affiche: <class 'tuple'>
print(type(tuple2))   # Affiche: <class 'tuple'>
print(type(non_tuple))  # Affiche: <class 'int'>

# Autres exemples de création de tuples
tuple_vide = ()
tuple_multiple = 1, 2, 3  # Parenthèses optionnelles
tuple_avec_parentheses = (1, 2, 3)
```

### Question 5 : Dictionnaires
**Réponse correcte : A) `mon_dict.keys()`**

La méthode `keys()` renvoie un objet de type `dict_keys` contenant toutes les clés du dictionnaire. En Python 3, il s'agit d'une vue dynamique du dictionnaire qui reflète les modifications ultérieures.

**Exemple :**
```python
# Création et manipulation d'un dictionnaire
etudiant = {
    "nom": "Dupont",
    "prenom": "Jean",
    "age": 22
}

# Obtenir les clés
cles = etudiant.keys()
print(cles)  # Affiche: dict_keys(['nom', 'prenom', 'age'])

# Les vues sont dynamiques
etudiant["note"] = 15
print(cles)  # Affiche maintenant: dict_keys(['nom', 'prenom', 'age', 'note'])

# Autres méthodes utiles pour les dictionnaires
print(etudiant.values())  # Valeurs: dict_values(['Dupont', 'Jean', 22, 15])
print(etudiant.items())   # Paires clé-valeur: dict_items([('nom', 'Dupont'), ('prenom', 'Jean'), ('age', 22), ('note', 15)])
```

### Question 6 : Opérations sur les dictionnaires
**Réponse correcte : C) Lève une exception `KeyError`**

Lorsqu'on tente d'accéder à une clé inexistante dans un dictionnaire avec la syntaxe des crochets, Python lève une exception `KeyError`. Pour éviter cela, on peut utiliser la méthode `get()` qui renvoie `None` (ou une valeur par défaut spécifiée) si la clé n'existe pas.

**Exemple :**
```python
etudiant = {
    "nom": "Dupont",
    "prenom": "Jean",
    "age": 22
}

# Accès à une clé existante
print(etudiant["nom"])  # Affiche: Dupont

# Accès à une clé inexistante avec la syntaxe des crochets
try:
    print(etudiant["adresse"])
except KeyError as e:
    print(f"Erreur: {e}")  # Affiche: Erreur: 'adresse'

# Utilisation de get() pour éviter l'exception
print(etudiant.get("adresse"))  # Affiche: None
print(etudiant.get("adresse", "Non spécifiée"))  # Affiche: Non spécifiée
```

### Question 7 : Ensembles (sets)
**Réponse correcte : D) Il n'est pas ordonné et ne peut pas contenir de doublons**

Un ensemble (set) en Python est une collection non ordonnée d'éléments uniques. Cela signifie que l'ordre des éléments n'est pas garanti et qu'un ensemble ne peut pas contenir de doublons. Si vous essayez d'ajouter un élément qui existe déjà, il sera ignoré.

**Exemple :**
```python
# Création et manipulation d'ensembles
couleurs = {"rouge", "bleu", "vert", "rouge"}  # Le doublon "rouge" est éliminé
print(couleurs)  # L'ordre n'est pas garanti, par exemple: {'vert', 'rouge', 'bleu'}

# Vérification de l'unicité
nombres = [1, 2, 2, 3, 3, 3, 4, 4, 4, 4]
nombres_uniques = set(nombres)
print(nombres_uniques)  # Affiche: {1, 2, 3, 4}

# Opérations sur les ensembles
set1 = {1, 2, 3, 4, 5}
set2 = {4, 5, 6, 7, 8}

print(set1.union(set2))        # Union: {1, 2, 3, 4, 5, 6, 7, 8}
print(set1.intersection(set2))  # Intersection: {4, 5}
print(set1.difference(set2))    # Différence: {1, 2, 3}
```

### Question 8 : Opérations sur les ensembles
**Réponse correcte : C) `set.add(élément)`**

Pour ajouter un élément à un ensemble, on utilise la méthode `add()`. Les méthodes `append()` et `insert()` sont spécifiques aux listes, tandis que `extend()` est utilisée pour ajouter plusieurs éléments d'un itérable à une liste.

**Exemple :**
```python
# Ajout d'éléments à un ensemble
couleurs = {"rouge", "bleu"}

# Ajouter un élément
couleurs.add("vert")
print(couleurs)  # Affiche: {'rouge', 'bleu', 'vert'}

# Ajouter un élément déjà présent (sans effet)
couleurs.add("rouge")
print(couleurs)  # Inchangé

# Pour ajouter plusieurs éléments à la fois
couleurs.update(["jaune", "orange"])
print(couleurs)  # Affiche: {'rouge', 'bleu', 'vert', 'jaune', 'orange'}
```

### Question 9 : Compréhensions de listes
**Réponse correcte : A) `[0, 4, 16]`**

Cette compréhension de liste crée une liste contenant le carré (`x**2`) de chaque nombre `x` de 0 à 4 (via `range(5)`), mais uniquement si `x` est pair (`x % 2 == 0`). Les nombres pairs dans `range(5)` sont 0, 2, et 4, et leurs carrés sont respectivement 0, 4, et 16.

**Exemple :**
```python
# Compréhension de liste de base
carres = [x**2 for x in range(5)]
print(carres)  # Affiche: [0, 1, 4, 9, 16]

# Compréhension de liste avec condition
carres_pairs = [x**2 for x in range(5) if x % 2 == 0]
print(carres_pairs)  # Affiche: [0, 4, 16]

# Autres exemples de compréhensions
nombres = [1, 2, 3, 4, 5]
doubles = [x * 2 for x in nombres]
print(doubles)  # Affiche: [2, 4, 6, 8, 10]

# Compréhension de dictionnaire
carre_dict = {x: x**2 for x in range(5)}
print(carre_dict)  # Affiche: {0: 0, 1: 1, 2: 4, 3: 9, 4: 16}
```

### Question 10 : Méthodes de chaînes de caractères
**Réponse correcte : A) `split()`**

La méthode `split()` divise une chaîne de caractères en une liste de sous-chaînes en utilisant le séparateur spécifié (ou les espaces par défaut). Par exemple, `"a,b,c".split(",")` renvoie `["a", "b", "c"]`.

**Exemple :**
```python
# Utilisation de split() avec différents séparateurs
phrase = "Python est un langage de programmation"
mots = phrase.split()  # Séparateur par défaut: espace
print(mots)  # Affiche: ['Python', 'est', 'un', 'langage', 'de', 'programmation']

csv_ligne = "nom,prenom,age,ville"
donnees = csv_ligne.split(",")
print(donnees)  # Affiche: ['nom', 'prenom', 'age', 'ville']

# Spécifier un nombre maximal de divisions
chemin = "dossier1/dossier2/dossier3/fichier.txt"
parties = chemin.split("/", 2)
print(parties)  # Affiche: ['dossier1', 'dossier2', 'dossier3/fichier.txt']

# Autres méthodes utiles pour les chaînes
print(", ".join(["a", "b", "c"]))  # join(): Inverse de split(), affiche: a, b, c
print("  texte  ".strip())         # strip(): Enlève les espaces, affiche: texte
print("Python".upper())            # upper(): Convertit en majuscules, affiche: PYTHON
print("PYTHON".lower())            # lower(): Convertit en minuscules, affiche: python
```