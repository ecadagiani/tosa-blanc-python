# Chapitre 5 : Programmation Orientée Objet

## Questions

### Question 1 : Définition de classe
Quelle est la syntaxe correcte pour définir une classe en Python ?
- A) `class MaClasse { /* code */ }`
- B) `def MaClasse(): /* code */`
- C) `class MaClasse: # code`
- D) `object MaClasse(): # code`

### Question 2 : Constructeur
Comment définit-on le constructeur d'une classe en Python ?
- A) `def __new__(self): # code`
- B) `def __init__(self): # code`
- C) `def constructor(self): # code`
- D) `def MaClasse(self): # code`

### Question 3 : Attributs d'instance
Quel est le résultat de l'exécution du code suivant ?
```python
class Personne:
    def __init__(self, nom):
        self.nom = nom

p1 = Personne("Alice")
p2 = Personne("Bob")
p1.nom = "Charlie"
print(p2.nom)
```
- A) `Alice`
- B) `Bob`
- C) `Charlie`
- D) Une erreur est générée

### Question 4 : Héritage
Quelle est la syntaxe correcte pour qu'une classe `Fille` hérite d'une classe `Parent` ?
- A) `class Fille inherits Parent: # code`
- B) `class Fille extends Parent: # code`
- C) `class Fille(Parent): # code`
- D) `class Fille -> Parent: # code`

### Question 5 : Méthodes spéciales
Quelle méthode spéciale doit-on implémenter pour permettre l'utilisation de l'opérateur `+` entre deux instances d'une classe ?
- A) `__plus__(self, other)`
- B) `__add__(self, other)`
- C) `__sum__(self, other)`
- D) `__concat__(self, other)`

### Question 6 : Encapsulation
Quelle **convention** est utilisée en Python pour indiquer qu'un attribut devrait être considéré comme "privé" ?
- A) Utiliser le mot-clé `private` avant le nom de l'attribut
- B) Préfixer le nom de l'attribut avec un double underscore `__`
- C) Entourer le nom de l'attribut avec des accolades `{attribut}`
- D) Déclarer l'attribut en dehors de la méthode `__init__` 