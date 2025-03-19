# Chapitre 4 : Fonctions et Modularité

## Questions

### Question 1 : Définition de fonction
Quelle est la syntaxe correcte pour définir une fonction en Python ?
- A) `function ma_fonction(paramètres) { instructions }`
- B) `def ma_fonction(paramètres): instructions`
- C) `def ma_fonction(paramètres) { instructions }`
- D) `function ma_fonction(paramètres): instructions`

### Question 2 : Valeur de retour
Que se passe-t-il lorsqu'une fonction Python n'inclut pas d'instruction `return` ?
- A) La fonction retourne `False`
- B) La fonction retourne `0`
- C) La fonction retourne `None`
- D) Une erreur est générée

### Question 3 : Paramètres nommés
Quel est l'avantage d'utiliser des paramètres nommés lors de l'appel d'une fonction ?
- A) Cela rend le code plus concis
- B) Cela permet d'ignorer l'ordre des paramètres
- C) Cela améliore les performances de la fonction
- D) Cela empêche la modification des valeurs des paramètres

### Question 4 : Valeurs par défaut
Quel est le résultat de l'appel suivant ?
```python
def afficher_info(nom, age=25):
    print(f"{nom} a {age} ans")

afficher_info("Alice")
```
- A) `Alice a 25 ans`
- B) `Alice a None ans`
- C) `Alice a  ans`
- D) Une erreur est générée car le paramètre `age` n'est pas fourni

### Question 5 : Arguments variables
Quelle syntaxe permet à une fonction d'accepter un nombre variable d'arguments positionnels ?
- A) `def ma_fonction(*args):`
- B) `def ma_fonction(**kwargs):`
- C) `def ma_fonction(args...):`
- D) `def ma_fonction(&args):`

### Question 6 : Fonction lambda
Quelle affirmation est correcte à propos des fonctions lambda en Python ?
- A) Elles peuvent contenir plusieurs instructions séparées par des points-virgules
- B) Elles sont plus rapides que les fonctions normales
- C) Elles peuvent seulement contenir une expression unique
- D) Elles doivent toujours être affectées à une variable

### Question 7 : Portée des variables
Que produit le code suivant ?
```python
x = 10

def modifier():
    x = 20
    print("Dans la fonction :", x)

modifier()
print("Hors de la fonction :", x)
```
- A) `Dans la fonction : 20` puis `Hors de la fonction : 20`
- B) `Dans la fonction : 20` puis `Hors de la fonction : 10`
- C) `Dans la fonction : 10` puis `Hors de la fonction : 10`
- D) `Dans la fonction : 10` puis `Hors de la fonction : 20`

### Question 8 : Import de modules
Quelle est la manière correcte d'importer une fonction spécifique d'un module ?
- A) `import module.fonction`
- B) `from module include fonction`
- C) `from module import fonction`
- D) `import fonction from module` 