# Corrections - Chapitre 4 : Fonctions et Modularité

### Question 1 : Définition de fonction
**Réponse correcte : B) `def ma_fonction(paramètres): instructions`**

En Python, les fonctions sont définies en utilisant le mot-clé `def`, suivi du nom de la fonction, des paramètres entre parenthèses, et d'un deux-points. Les instructions de la fonction sont ensuite indentées dans un bloc de code. Python n'utilise pas d'accolades `{}` pour délimiter les blocs comme le font certains autres langages.

**Exemple :**
```python
# Définition d'une fonction simple sans paramètre
def dire_bonjour():
    print("Bonjour !")

# Appel de la fonction
dire_bonjour()  # Affiche: Bonjour !

# Fonction avec paramètres
def saluer(prenom, moment_journee):
    print(f"Bonjour {prenom}, bonne {moment_journee} !")

# Appel avec arguments
saluer("Marie", "après-midi")  # Affiche: Bonjour Marie, bonne après-midi !

# Fonction avec valeur de retour
def calculer_carre(nombre):
    return nombre * nombre

# Utilisation du résultat retourné
resultat = calculer_carre(5)
print(f"Le carré de 5 est {resultat}")  # Affiche: Le carré de 5 est 25

# Fonction avec documentation (docstring)
def convertir_celsius_en_fahrenheit(celsius):
    """
    Convertit une température en degrés Celsius en degrés Fahrenheit.
    
    Args:
        celsius (float): La température en degrés Celsius
        
    Returns:
        float: La température convertie en degrés Fahrenheit
    """
    return (celsius * 9/5) + 32

# Utilisation de la fonction avec docstring
temp_f = convertir_celsius_en_fahrenheit(20)
print(f"20°C = {temp_f}°F")  # Affiche: 20°C = 68.0°F

# Afficher la documentation de la fonction
print(convertir_celsius_en_fahrenheit.__doc__)
```

### Question 2 : Valeur de retour
**Réponse correcte : C) La fonction retourne `None`**

En Python, si une fonction n'inclut pas explicitement une instruction `return` ou si elle se termine avec `return` sans valeur, elle retourne automatiquement la valeur `None`. Cette valeur spéciale représente l'absence de valeur et est différente de zéro, de chaînes vides ou de `False`.

**Exemple :**
```python
# Fonction sans instruction return
def fonction_sans_return():
    print("Cette fonction ne retourne rien explicitement")

# Appel de la fonction et stockage du résultat
resultat = fonction_sans_return()
print(f"Valeur retournée: {resultat}")  # Affiche: Valeur retournée: None
print(f"Type de la valeur retournée: {type(resultat)}")  # Affiche: <class 'NoneType'>

# Fonction avec return sans valeur
def fonction_return_vide():
    print("Cette fonction a un return sans valeur")
    return

resultat = fonction_return_vide()
print(f"Valeur retournée: {resultat}")  # Affiche: Valeur retournée: None

# Comparaison avec une fonction qui retourne une valeur
def fonction_avec_return():
    print("Cette fonction retourne une valeur")
    return 42

resultat = fonction_avec_return()
print(f"Valeur retournée: {resultat}")  # Affiche: Valeur retournée: 42

# Exemple d'utilisation pratique de None
def trouver_element(liste, element):
    """Trouve l'index d'un élément dans une liste ou retourne None si absent"""
    for i, val in enumerate(liste):
        if val == element:
            return i
    # Si l'élément n'est pas trouvé, aucun return explicite n'est exécuté
    # La fonction retourne None implicitement

nombres = [10, 20, 30, 40, 50]
index = trouver_element(nombres, 30)
if index is not None:  # Vérification si la fonction a trouvé l'élément
    print(f"Élément trouvé à l'index {index}")
else:
    print("Élément non trouvé")

# Vérification si une valeur est None
index = trouver_element(nombres, 60)  # Élément absent
print(f"Résultat: {index}")  # Affiche: Résultat: None
print(f"La valeur est-elle None? {index is None}")  # Affiche: True
```

### Question 3 : Paramètres nommés
**Réponse correcte : B) Cela permet d'ignorer l'ordre des paramètres**

L'utilisation de paramètres nommés lors de l'appel d'une fonction permet d'ignorer l'ordre des paramètres définis dans la fonction. On peut ainsi spécifier les arguments dans n'importe quel ordre en les précédant de leur nom suivi d'un signe égal. Cela rend le code plus lisible et flexible, particulièrement pour les fonctions avec de nombreux paramètres.

**Exemple :**
```python
# Fonction avec plusieurs paramètres
def afficher_personne(nom, age, ville):
    print(f"{nom}, {age} ans, habite à {ville}")

# 1. Appel avec paramètres positionnels (ordre obligatoire)
afficher_personne("Alice", 30, "Paris")  # Affiche: Alice, 30 ans, habite à Paris

# 2. Appel avec paramètres nommés (ordre libre)
afficher_personne(ville="Lyon", nom="Bob", age=25)  # Affiche: Bob, 25 ans, habite à Lyon

# 3. Mélange de paramètres positionnels et nommés
# Les positionnels doivent venir avant les nommés
afficher_personne("Charlie", ville="Marseille", age=35)  # Affiche: Charlie, 35 ans, habite à Marseille

# Cas pratique: fonction avec nombreux paramètres
def calculer_prix(base, quantite=1, remise=0, taxe=0.2, livraison=0):
    prix_ht = base * quantite * (1 - remise)
    prix_ttc = prix_ht * (1 + taxe)
    total = prix_ttc + livraison
    return total

# Sans paramètres nommés, il faut se souvenir de l'ordre et fournir toutes les valeurs
prix1 = calculer_prix(100, 2, 0.1, 0.2, 5)
print(f"Prix total (sans nommage): {prix1}€")  # 185.0€

# Avec paramètres nommés, on peut spécifier uniquement ceux qu'on veut changer
prix2 = calculer_prix(base=100, remise=0.1, livraison=5)
print(f"Prix total (avec nommage): {prix2}€")  # 113.0€

# Les paramètres nommés améliorent la lisibilité
prix3 = calculer_prix(
    base=100,
    quantite=2,
    remise=0.15,  # 15% de remise
    taxe=0.055,   # 5.5% de TVA
    livraison=0   # Livraison gratuite
)
print(f"Prix total (explicite): {prix3}€")  # 179.35€

# La lisibilité peut être encore améliorée avec des commentaires
prix4 = calculer_prix(
    base=99.99,       # Prix unitaire
    quantite=3,       # 3 articles
    remise=0.20,      # Remise fidélité
    taxe=0.2,         # TVA standard
    livraison=4.95    # Frais de port
)
print(f"Prix total détaillé: {prix4}€")  # 243.97€
```

### Question 4 : Valeurs par défaut
**Réponse correcte : A) `Alice a 25 ans`**

Lorsqu'un paramètre a une valeur par défaut et qu'aucune valeur n'est fournie lors de l'appel de la fonction, la valeur par défaut est utilisée. Dans cet exemple, `age` a une valeur par défaut de 25, donc la fonction affiche "Alice a 25 ans" lorsqu'elle est appelée sans spécifier d'âge.

**Exemple :**
```python
# Définition de la fonction avec un paramètre ayant une valeur par défaut
def afficher_info(nom, age=25):
    print(f"{nom} a {age} ans")

# Appel de la fonction sans fournir le paramètre age
afficher_info("Alice")  # Affiche: Alice a 25 ans

# Appel de la fonction en fournissant une valeur pour age
afficher_info("Bob", 30)  # Affiche: Bob a 30 ans

# Utilisation de plusieurs paramètres par défaut
def creer_profil(nom, age=18, ville="Paris", profession="Étudiant"):
    return {
        "nom": nom,
        "age": age,
        "ville": ville,
        "profession": profession
    }

# Utilisation avec seulement le paramètre obligatoire
profil1 = creer_profil("Charlie")
print(profil1)  # Affiche: {'nom': 'Charlie', 'age': 18, 'ville': 'Paris', 'profession': 'Étudiant'}

# Surcharge de certains paramètres par défaut
profil2 = creer_profil("David", ville="Lyon")
print(profil2)  # Affiche: {'nom': 'David', 'age': 18, 'ville': 'Lyon', 'profession': 'Étudiant'}

# Surcharge de tous les paramètres
profil3 = creer_profil("Eve", 45, "Marseille", "Ingénieure")
print(profil3)  # Affiche: {'nom': 'Eve', 'age': 45, 'ville': 'Marseille', 'profession': 'Ingénieure'}

# Attention: les paramètres sans valeur par défaut doivent venir avant ceux avec valeurs par défaut
# La définition suivante provoquerait une erreur:
# def erreur(a=1, b):  # SyntaxError: non-default argument follows default argument
#     return a + b

# Cas particulier: attention aux valeurs mutables comme valeurs par défaut
def ajouter_element(element, liste=[]):  # ATTENTION: liste=[] n'est initialisée qu'une seule fois!
    liste.append(element)
    return liste

# Premier appel
liste1 = ajouter_element(1)
print(liste1)  # Affiche: [1]

# Deuxième appel - le paramètre par défaut conserve son état!
liste2 = ajouter_element(2)
print(liste2)  # Affiche: [1, 2] et non [2] !

# Solution correcte pour éviter ce piège:
def ajouter_element_correct(element, liste=None):
    if liste is None:  # Crée une nouvelle liste à chaque appel si liste n'est pas fourni
        liste = []
    liste.append(element)
    return liste

# Démonstration de la solution correcte
liste3 = ajouter_element_correct(1)
print(liste3)  # Affiche: [1]

liste4 = ajouter_element_correct(2)
print(liste4)  # Affiche: [2]
```

### Question 5 : Arguments variables
**Réponse correcte : A) `def ma_fonction(*args):`**

La syntaxe `*args` permet à une fonction d'accepter un nombre variable d'arguments positionnels. Ces arguments sont collectés dans un tuple nommé `args` (bien que le nom puisse être différent). À l'inverse, `**kwargs` est utilisé pour collecter un nombre variable d'arguments nommés dans un dictionnaire.

**Exemple :**
```python
# Fonction acceptant un nombre variable d'arguments positionnels
def somme_nombres(*args):
    """Calcule la somme de tous les arguments fournis"""
    total = 0
    for nombre in args:
        total += nombre
    return total

# Appels avec différents nombres d'arguments
print(somme_nombres(1, 2))                # Affiche: 3
print(somme_nombres(1, 2, 3, 4, 5))       # Affiche: 15
print(somme_nombres())                    # Affiche: 0
print(somme_nombres(10))                  # Affiche: 10
print(somme_nombres(1, 2, 3, 4, 5, 6, 7)) # Affiche: 28

# Décompression d'une séquence avec l'opérateur *
nombres = [1, 2, 3, 4, 5]
print(somme_nombres(*nombres))  # Équivalent à somme_nombres(1, 2, 3, 4, 5)

# Fonction acceptant des arguments nommés variables avec **kwargs
def afficher_infos(**kwargs):
    """Affiche les informations fournies sous forme de paires clé-valeur"""
    print("Informations:")
    for cle, valeur in kwargs.items():
        print(f"  - {cle}: {valeur}")

# Appel avec différents arguments nommés
afficher_infos(nom="Alice", age=30, ville="Paris")
# Affiche:
# Informations:
#   - nom: Alice
#   - age: 30
#   - ville: Paris

# Décompression d'un dictionnaire avec l'opérateur **
infos = {"profession": "Ingénieur", "salaire": 45000, "experience": "5 ans"}
afficher_infos(**infos)
# Affiche:
# Informations:
#   - profession: Ingénieur
#   - salaire: 45000
#   - experience: 5 ans

# Utilisation combinée de *args et **kwargs
def fonction_complete(param_obligatoire, *args, param_defaut="Défaut", **kwargs):
    print(f"Paramètre obligatoire: {param_obligatoire}")
    print(f"Arguments positionnels (*args): {args}")
    print(f"Paramètre avec valeur par défaut: {param_defaut}")
    print(f"Arguments nommés (**kwargs): {kwargs}")

# Appel complet de la fonction
fonction_complete("Requis", 1, 2, 3, param_defaut="Personnalisé", a=10, b=20, c=30)
# Affiche:
# Paramètre obligatoire: Requis
# Arguments positionnels (*args): (1, 2, 3)
# Paramètre avec valeur par défaut: Personnalisé
# Arguments nommés (**kwargs): {'a': 10, 'b': 20, 'c': 30}

# Cas pratique: fonction de formatage flexible
def formatter_texte(texte, *styles, **attributs):
    """Formate un texte avec différents styles et attributs"""
    resultat = texte
    
    # Appliquer les styles (gras, italique, souligné...)
    if "gras" in styles:
        resultat = f"<strong>{resultat}</strong>"
    if "italique" in styles:
        resultat = f"<em>{resultat}</em>"
    if "souligne" in styles:
        resultat = f"<u>{resultat}</u>"
    
    # Appliquer les attributs personnalisés (couleur, taille...)
    attributs_html = ""
    for nom, valeur in attributs.items():
        attributs_html += f' {nom}="{valeur}"'
    
    if attributs_html:
        resultat = f"<span{attributs_html}>{resultat}</span>"
    
    return resultat

# Exemples d'utilisation de la fonction de formatage
texte1 = formatter_texte("Bonjour", "gras", "italique")
print(texte1)  # Affiche: <em><strong>Bonjour</strong></em>

texte2 = formatter_texte("Attention", "gras", couleur="red", taille="18px")
print(texte2)  # Affiche: <span couleur="red" taille="18px"><strong>Attention</strong></span>
```

### Question 6 : Fonction lambda
**Réponse correcte : C) Elles peuvent seulement contenir une expression unique**

Les fonctions lambda en Python sont des fonctions anonymes limitées à une seule expression. Elles ne peuvent pas contenir de blocs de code avec plusieurs instructions, de boucles, de conditions multiples ou d'autres structures de contrôle complexes. Leur principale utilité est de créer de petites fonctions à usage unique de façon concise.

**Exemple :**
```python
# Fonction lambda qui calcule le carré d'un nombre
carre = lambda x: x**2

# Utilisation de la fonction lambda
print(carre(4))  # Affiche: 16
print(carre(5))  # Affiche: 25

# Équivalent avec une fonction classique
def carre_classique(x):
    return x**2

# Comparaison des fonctions
print(f"Lambda: {carre(3)}, Classique: {carre_classique(3)}")  # Affiche: Lambda: 9, Classique: 9

# Lambda avec plusieurs paramètres
somme = lambda x, y: x + y
print(somme(10, 5))  # Affiche: 15

# Lambda avec paramètre par défaut
salutation = lambda nom, message="Bonjour": f"{message}, {nom}!"
print(salutation("Alice"))         # Affiche: Bonjour, Alice!
print(salutation("Bob", "Salut"))  # Affiche: Salut, Bob!

# Utilisation dans une fonction comme sorted avec une clé personnalisée
noms = ["Alice", "Bob", "Charlie", "David", "Eve"]
# Trier par longueur de nom
noms_tries_longueur = sorted(noms, key=lambda nom: len(nom))
print(f"Noms triés par longueur: {noms_tries_longueur}")  
# Affiche: ['Bob', 'Eve', 'Alice', 'David', 'Charlie']

# Trier par dernière lettre du nom
noms_tries_derniere_lettre = sorted(noms, key=lambda nom: nom[-1])
print(f"Noms triés par dernière lettre: {noms_tries_derniere_lettre}")  
# Affiche: ['Charlie', 'Alice', 'Dave', 'Eve', 'Bob']

# Utilisation avec filter() pour filtrer une liste
nombres = [1, 2, 3, 4, 5, 6, 7, 8, 9, 10]
nombres_pairs = list(filter(lambda x: x % 2 == 0, nombres))
print(f"Nombres pairs: {nombres_pairs}")  # Affiche: [2, 4, 6, 8, 10]

# Utilisation avec map() pour transformer une liste
carres = list(map(lambda x: x**2, nombres))
print(f"Carrés: {carres}")  # Affiche: [1, 4, 9, 16, 25, 36, 49, 64, 81, 100]

# Fonctions lambda dans des structures de données
operations = {
    'addition': lambda x, y: x + y,
    'soustraction': lambda x, y: x - y,
    'multiplication': lambda x, y: x * y,
    'division': lambda x, y: x / y if y != 0 else "Division par zéro impossible"
}

# Utilisation des fonctions stockées dans le dictionnaire
print(operations['addition'](5, 3))       # Affiche: 8
print(operations['soustraction'](5, 3))   # Affiche: 2
print(operations['multiplication'](5, 3)) # Affiche: 15
print(operations['division'](5, 3))       # Affiche: 1.6666666666666667

# Limites des fonctions lambda (une seule expression, pas de blocs de code)
# Ceci n'est PAS possible avec une lambda:
# lambda x: if x > 0: return x else: return -x  # Erreur de syntaxe

# À la place, on peut utiliser un opérateur ternaire:
valeur_absolue = lambda x: x if x >= 0 else -x
print(valeur_absolue(-5))  # Affiche: 5
print(valeur_absolue(7))   # Affiche: 7
```

### Question 7 : Portée des variables
**Réponse correcte : B) `Dans la fonction : 20` puis `Hors de la fonction : 10`**

Ce code illustre le concept de portée des variables. Lorsque `x = 20` est exécuté dans la fonction, cela crée une nouvelle variable locale `x` qui n'affecte pas la variable globale `x`. Ainsi, dans la fonction, `x` vaut 20, mais en dehors, `x` conserve sa valeur initiale de 10. Pour modifier la variable globale depuis une fonction, il faudrait utiliser le mot-clé `global`.

**Exemple :**
```python
# Démonstration de la portée des variables

# Variable globale
x = 10

def modifier():
    x = 20  # Crée une variable locale x, différente de la variable globale
    print("Dans la fonction :", x)

modifier()  # Affiche: Dans la fonction : 20
print("Hors de la fonction :", x)  # Affiche: Hors de la fonction : 10

# Utilisation du mot-clé global pour modifier une variable globale
y = 5

def modifier_global():
    global y  # Indique que nous voulons modifier la variable globale y
    y = 15
    print("Dans la fonction avec global :", y)

modifier_global()  # Affiche: Dans la fonction avec global : 15
print("Hors de la fonction après global :", y)  # Affiche: Hors de la fonction après global : 15

# Exemple avec des variables imbriquées
def fonction_externe():
    z = 100
    
    def fonction_interne():
        print("Accès à z depuis fonction_interne :", z)  # Peut accéder à z de fonction_externe
    
    fonction_interne()  # Affiche: Accès à z depuis fonction_interne : 100
    print("z dans fonction_externe :", z)  # Affiche: z dans fonction_externe : 100

fonction_externe()

# Mot-clé nonlocal pour modifier une variable d'une fonction englobante
def fonction_externe2():
    compteur = 0
    
    def incrementer():
        nonlocal compteur  # Indique que compteur appartient à la fonction englobante
        compteur += 1
        print("Compteur dans incrementer :", compteur)
    
    print("Compteur initial :", compteur)  # Affiche: Compteur initial : 0
    incrementer()  # Affiche: Compteur dans incrementer : 1
    incrementer()  # Affiche: Compteur dans incrementer : 2
    print("Compteur final :", compteur)  # Affiche: Compteur final : 2

fonction_externe2()

# Différents niveaux de portée en Python: LEGB
# L - Local: variables définies dans la fonction actuelle
# E - Enclosing: variables définies dans les fonctions englobantes
# G - Global: variables définies au niveau du module
# B - Built-in: noms pré-définis dans Python (print, len, etc.)

# Exemple illustrant les règles LEGB
var_globale = "Je suis globale"

def exemple_legb():
    var_englobante = "Je suis englobante"
    
    def fonction_interne():
        var_locale = "Je suis locale"
        print(f"Locale: {var_locale}")
        print(f"Englobante: {var_englobante}")
        print(f"Globale: {var_globale}")
        print(f"Built-in: {len('Python')}")  # len est une fonction built-in
    
    fonction_interne()

exemple_legb()
# Affiche:
# Locale: Je suis locale
# Englobante: Je suis englobante
# Globale: Je suis globale
# Built-in: 6

# Problème courant: modification d'une variable locale avant sa première utilisation
def erreur_commune():
    try:
        print(variable)  # Erreur: variable n'est pas définie
        variable = 10    # Cette ligne n'est jamais atteinte
    except UnboundLocalError as e:
        print(f"Erreur: {e}")

erreur_commune()  # Affiche une erreur UnboundLocalError
```

### Question 8 : Import de modules
**Réponse correcte : C) `from module import fonction`**

La syntaxe correcte pour importer une fonction spécifique d'un module est `from module import fonction`. Cela permet d'utiliser directement le nom de la fonction sans préfixe. Alternativement, on peut importer tout le module avec `import module` et accéder à la fonction avec `module.fonction`.

**Exemple :**
```python
# Différentes façons d'importer des modules et leurs composants

# 1. Import d'un module entier
import math

# Utilisation des fonctions et constantes avec le préfixe du module
rayon = 5
aire = math.pi * math.pow(rayon, 2)
print(f"Aire d'un cercle de rayon {rayon} = {aire:.2f}")  # Affiche: Aire d'un cercle de rayon 5 = 78.54

# 2. Import d'éléments spécifiques d'un module (syntaxe correcte de la réponse)
from random import randint, choice

# Utilisation directe des fonctions importées sans préfixe
nombre_aleatoire = randint(1, 100)
print(f"Nombre aléatoire entre 1 et 100: {nombre_aleatoire}")

fruits = ["pomme", "banane", "orange", "kiwi", "fraise"]
fruit_choisi = choice(fruits)
print(f"Fruit choisi au hasard: {fruit_choisi}")

# 3. Import avec un alias
import datetime as dt

maintenant = dt.datetime.now()
print(f"Date et heure actuelles: {maintenant}")
print(f"Année: {maintenant.year}, Mois: {maintenant.month}, Jour: {maintenant.day}")

# 4. Import de tous les éléments d'un module (à utiliser avec précaution)
from math import *

# Les fonctions et constantes sont disponibles directement
print(f"Racine carrée de 16: {sqrt(16)}")  # Affiche: Racine carrée de 16: 4.0
print(f"Cosinus de 0: {cos(0)}")          # Affiche: Cosinus de 0: 1.0

# Note: cette approche peut causer des conflits de noms et rendre le code moins lisible

# 5. Structure de projet avec des modules personnalisés
# Imaginons que nous avons un fichier mon_module.py avec le contenu suivant:
"""
# mon_module.py
def saluer(nom):
    return f"Bonjour, {nom}!"

def au_revoir(nom):
    return f"Au revoir, {nom}!"

PI = 3.14159
"""

# Pour l'importer, nous utiliserions:
# import mon_module
# message = mon_module.saluer("Alice")

# Ou plus spécifiquement:
# from mon_module import saluer, PI
# message = saluer("Alice")

# 6. Import avec gestion des exceptions
try:
    # Tentative d'import d'un module qui pourrait ne pas être installé
    from rich import print as rprint
    rprint("[bold green]Ce texte serait en vert gras si rich était installé[/bold green]")
except ImportError:
    print("Le module 'rich' n'est pas installé. Installation avec pip install rich")

# 7. Modules de la bibliothèque standard couramment utilisés
import os                  # Interaction avec le système d'exploitation
import sys                 # Accès à l'interpréteur Python
import json                # Manipulation de données JSON
import csv                 # Manipulation de fichiers CSV
import re                  # Expressions régulières regex
import time                # Fonctions liées au temps
import random              # Génération de nombres aléatoires
import requests            # Requêtes HTTP
```