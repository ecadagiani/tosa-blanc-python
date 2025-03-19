
# Corrections - Chapitre 1 : Fondamentaux de Python

### Question 1 : À propos du langage Python
**Réponse correcte : C) Interprété avec compilation à la volée (bytecode)**

Python est un langage interprété qui compile d'abord le code source en bytecode (fichiers .pyc). Ce bytecode est ensuite interprété par la machine virtuelle Python (PVM). Cette approche hybride permet de combiner certains avantages des langages compilés et interprétés.

### Question 2 : Caractéristiques du langage Python
**Réponse correcte : C) Python est un langage à typage dynamique et fortement typé**

Python utilise un typage dynamique (les types sont vérifiés à l'exécution), mais il est fortement typé car il n'effectue pas de conversions implicites entre types incompatibles (par exemple, `"1" + 1` générera une erreur).

### Question 3 : Indentation en Python
**Réponse correcte : C) L'indentation est obligatoire et détermine la structure du code**

En Python, l'indentation n'est pas seulement une question de style, elle détermine la structure du code. Les blocs de code sont définis par leur niveau d'indentation et non par des accolades ou d'autres délimiteurs comme dans d'autres langages.

### Question 4 : Variables en Python
**Réponse correcte : D) `1variable`**

Les noms de variables en Python ne peuvent pas commencer par un chiffre. Ils doivent commencer par une lettre ou un underscore, puis peuvent contenir des lettres, chiffres et underscores.

### Question 5 : Types de données
**Réponse correcte : B) `float`**

En Python 3, la division avec l'opérateur `/` renvoie toujours un nombre à virgule flottante (float), même si les opérandes sont des entiers et que le résultat est un nombre entier. Pour obtenir une division entière, il faut utiliser l'opérateur `//`.

### Question 6 : Opérateurs
**Réponse correcte : A) `3`**

L'opérateur `%` est l'opérateur modulo qui renvoie le reste de la division entière. Dans ce cas, 15 divisé par 4 donne 3 avec un reste de 3, donc `15 % 4` est égal à 3.

### Question 7 : Conversion de types
**Réponse correcte : D) Une erreur est générée**

La fonction `int()` ne peut pas convertir directement une chaîne contenant un point décimal. Elle génère une `ValueError`. Pour convertir "15.5" en entier, il faudrait d'abord convertir en float puis en int, comme ceci : `int(float("15.5"))`.

### Question 8 : Chaînes de caractères
**Réponse correcte : C) **
```
"""Ligne 1
Ligne 2"""
```

Les triples guillemets (soit `"""` soit `'''`) permettent de créer des chaînes multi-lignes en préservant les sauts de ligne dans le texte. L'option A inclut un caractère d'échappement qui représente un saut de ligne mais dans une seule chaîne.

### Question 9 : Opérateurs de comparaison
**Réponse correcte : B) `False`**

Python est sensible à la casse, donc "abc" et "ABC" sont considérés comme deux chaînes différentes. L'opérateur `==` renvoie donc `False` lors de cette comparaison.

### Question 10 : Commentaires
**Réponse correcte : C) `''' Ceci est un commentaire sur plusieurs lignes '''`**

En Python, on peut utiliser des triples guillemets (simples ou doubles) pour créer des commentaires multi-lignes. Bien que techniquement ce soit une chaîne de caractères non affectée (docstring si placée au début d'une fonction ou classe), elle est couramment utilisée comme commentaire multi-lignes. L'autre option est d'utiliser le caractère `#` au début de chaque ligne.
