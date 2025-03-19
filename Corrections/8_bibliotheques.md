# Corrections - Chapitre 8 : Bibliothèques Standard et Externes

### Question 1 : Module datetime
**Réponse correcte : B) `datetime.datetime.now()`**

Le module `datetime` contient plusieurs classes, dont la classe `datetime`. Pour obtenir la date et l'heure actuelles, on utilise la méthode `now()` de la classe `datetime` dans le module `datetime`, soit `datetime.datetime.now()`. Cette méthode retourne un objet `datetime` représentant la date et l'heure courantes.

**Exemple :**
```python
import datetime

# Obtenir la date et l'heure actuelles
maintenant = datetime.datetime.now()
print(maintenant)  # Par exemple: 2023-06-15 14:30:45.123456

# Accéder aux composants individuels
print(maintenant.year)    # Année
print(maintenant.month)   # Mois
print(maintenant.day)     # Jour
print(maintenant.hour)    # Heure
print(maintenant.minute)  # Minute
print(maintenant.second)  # Seconde
```

### Question 2 : Expressions régulières
**Réponse correcte : C) `re.findall()`**

Le module `re` fournit plusieurs fonctions pour travailler avec les expressions régulières:
- `re.match()` vérifie si le motif correspond au début de la chaîne
- `re.search()` cherche la première occurrence du motif dans la chaîne
- `re.findall()` trouve toutes les occurrences du motif dans la chaîne et les retourne dans une liste
- `re.locate()` n'existe pas dans le module `re`

**Exemple :**
```python
import re

# Trouver tous les nombres dans une chaîne
texte = "J'ai 25 ans et mon frère a 30 ans."
nombres = re.findall(r'\d+', texte)
print(nombres)  # Affiche: ['25', '30']

# Trouver tous les mots commençant par une lettre majuscule
texte = "Python est un langage de programmation. Java et C++ sont aussi populaires."
mots_majuscules = re.findall(r'\b[A-Z][a-z]*\b', texte)
print(mots_majuscules)  # Affiche: ['Python', 'Java', 'C']
```

### Question 3 : Module collections
**Réponse correcte : C) `Counter`**

Le module `collections` fournit plusieurs structures de données alternatives:
- `OrderedDict` est un dictionnaire qui conserve l'ordre d'insertion des clés
- `defaultdict` est un dictionnaire qui fournit une valeur par défaut lorsqu'une clé n'existe pas
- `Counter` est spécialisé pour compter des éléments hashables
- `namedtuple` permet de créer des tuples avec des champs nommés

`Counter` est particulièrement adapté pour compter des éléments, car il offre des méthodes spécifiques comme `most_common()` pour obtenir les éléments les plus fréquents.

**Exemple :**
```python
from collections import Counter

# Compter les occurrences des caractères dans une chaîne
texte = "mississippi"
compteur = Counter(texte)
print(compteur)  # Affiche: Counter({'i': 4, 's': 4, 'p': 2, 'm': 1})

# Obtenir les éléments les plus fréquents
print(compteur.most_common(2))  # Affiche: [('i', 4), ('s', 4)]

# Utiliser Counter avec une liste
notes = [12, 15, 7, 12, 20, 15, 7, 12]
compteur_notes = Counter(notes)
print(compteur_notes)  # Affiche: Counter({12: 3, 15: 2, 7: 2, 20: 1})
```

### Question 4 : Bibliothèques numériques
**Réponse correcte : C) `random.random()`**

Le module `random` fournit plusieurs fonctions pour générer des nombres aléatoires:
- `random.randint(a, b)` génère un entier aléatoire entre a et b inclus
- `random.uniform(a, b)` génère un nombre à virgule flottante aléatoire entre a et b
- `random.random()` génère spécifiquement un nombre à virgule flottante entre 0.0 et 1.0
- `random.float()` n'existe pas dans le module `random`

**Exemple :**
```python
import random

# Générer un nombre aléatoire entre 0.0 et 1.0
nombre = random.random()
print(nombre)  # Par exemple: 0.7234058439813323

# Autres fonctions utiles du module random
print(random.randint(1, 10))     # Entier aléatoire entre 1 et 10 inclus
print(random.uniform(0, 100))    # Nombre à virgule flottante entre 0 et 100
print(random.choice([1, 2, 3]))  # Élément aléatoire d'une séquence

# Mélanger une liste
liste = [1, 2, 3, 4, 5]
random.shuffle(liste)
print(liste)  # Liste mélangée aléatoirement
```

### Question 5 : Modules système
**Réponse correcte : B) `sys.argv`**

Le module `sys` fournit l'accès à des variables et fonctions spécifiques au système. La liste `sys.argv` contient les arguments de la ligne de commande passés au script Python. Le premier élément (`sys.argv[0]`) est toujours le nom du script.

**Exemple :**
```python
import sys

# Afficher tous les arguments de la ligne de commande
print("Nom du script:", sys.argv[0])
print("Arguments:", sys.argv[1:])

# Traiter les arguments
if len(sys.argv) > 1:
    print("Premier argument:", sys.argv[1])
else:
    print("Aucun argument fourni")

# Exemple d'utilisation dans un script simple
# Si on exécute: python mon_script.py fichier.txt sortie.txt
if len(sys.argv) == 3:
    fichier_entree = sys.argv[1]
    fichier_sortie = sys.argv[2]
    print(f"Traitement de {fichier_entree} vers {fichier_sortie}")
```
