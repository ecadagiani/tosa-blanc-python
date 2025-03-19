# Corrections - Chapitre 5 : Programmation Orientée Objet

### Question 1 : Définition de classe
**Réponse correcte : C) `class MaClasse: # code`**

En Python, une classe est définie en utilisant le mot-clé `class`, suivi du nom de la classe et d'un deux-points. Le corps de la classe est ensuite indenté. Contrairement à d'autres langages comme Java ou C++, Python n'utilise pas d'accolades pour délimiter le corps de la classe.

**Exemple :**
```python
# Définition d'une classe simple
class Voiture:
    # Attribut de classe (partagé par toutes les instances)
    nombre_de_roues = 4
    
    # Méthode de la classe
    def klaxonner(self):
        return "Pouet pouet!"

# Création d'une instance de la classe
ma_voiture = Voiture()
print(ma_voiture.nombre_de_roues)  # Affiche: 4
print(ma_voiture.klaxonner())      # Affiche: Pouet pouet!

# En Python, pas besoin d'accolades comme en Java:
# Java: class Voiture { ... }
# C++:  class Voiture { ... };

# Classe vide (utilise pass comme placeholder)
class ClasseVide:
    pass

# Vérification du type
print(type(ma_voiture))  # Affiche: <class '__main__.Voiture'>
print(isinstance(ma_voiture, Voiture))  # Affiche: True
```

### Question 2 : Constructeur
**Réponse correcte : B) `def __init__(self): # code`**

En Python, le constructeur d'une classe est défini par la méthode spéciale `__init__`. Cette méthode est appelée automatiquement lorsqu'une nouvelle instance de la classe est créée. Le premier paramètre, conventionnellement nommé `self`, fait référence à l'instance nouvellement créée. Le véritable constructeur en Python est `__new__`, mais dans la pratique, c'est `__init__` qui est utilisé pour initialiser les attributs d'instance.

**Exemple :**
```python
# Définition d'une classe avec un constructeur
class Personne:
    def __init__(self, nom, age):
        # Initialisation des attributs d'instance
        self.nom = nom
        self.age = age
        print(f"Nouvelle personne créée: {nom}, {age} ans")
    
    def presenter(self):
        return f"Je m'appelle {self.nom} et j'ai {self.age} ans."

# Création d'instances - le constructeur est appelé automatiquement
personne1 = Personne("Alice", 30)  # Affiche: Nouvelle personne créée: Alice, 30 ans
personne2 = Personne("Bob", 25)    # Affiche: Nouvelle personne créée: Bob, 25 ans

# Utilisation des attributs et méthodes
print(personne1.nom)               # Affiche: Alice
print(personne2.presenter())       # Affiche: Je m'appelle Bob et j'ai 25 ans.

# Constructeur avec paramètres par défaut
class Produit:
    def __init__(self, nom, prix=0, stock=0):
        self.nom = nom
        self.prix = prix
        self.stock = stock
    
    def valeur_totale(self):
        return self.prix * self.stock

# Création d'instances avec différentes combinaisons de paramètres
produit1 = Produit("Ordinateur", 1000, 5)
produit2 = Produit("Souris", 20)  # stock prend la valeur par défaut 0
produit3 = Produit("Clavier")      # prix et stock prennent les valeurs par défaut

print(f"Valeur du stock d'ordinateurs: {produit1.valeur_totale()}€")  # Affiche: 5000€
```

### Question 3 : Attributs d'instance
**Réponse correcte : B) `Bob`**

Dans ce code, deux instances de la classe `Personne` sont créées : `p1` avec le nom "Alice" et `p2` avec le nom "Bob". Ensuite, l'attribut `nom` de `p1` est modifié pour devenir "Charlie". Cela n'affecte pas l'attribut `nom` de `p2` qui reste "Bob". Chaque instance a ses propres attributs indépendants.

**Exemple détaillé :**
```python
# Définition de la classe Personne
class Personne:
    def __init__(self, nom):
        self.nom = nom  # Chaque instance a son propre attribut nom

# Création de deux instances distinctes
p1 = Personne("Alice")
p2 = Personne("Bob")

print("État initial:")
print(f"p1.nom = {p1.nom}")  # Affiche: Alice
print(f"p2.nom = {p2.nom}")  # Affiche: Bob

# Modification de l'attribut nom de p1 uniquement
p1.nom = "Charlie"

print("\nAprès modification:")
print(f"p1.nom = {p1.nom}")  # Affiche: Charlie
print(f"p2.nom = {p2.nom}")  # Affiche: Bob (inchangé)

# Démonstration de l'indépendance des instances
p1.age = 30  # Ajout d'un nouvel attribut à p1 uniquement
print("\nAjout d'un attribut à p1:")
print(f"p1.age = {p1.age}")  # Affiche: 30
# print(p2.age)  # Génèrerait une erreur AttributeError

# Attributs de classe vs attributs d'instance
class Compteur:
    total = 0  # Attribut de classe (partagé entre toutes les instances)
    
    def __init__(self, valeur):
        self.valeur = valeur  # Attribut d'instance (unique à chaque instance)
        Compteur.total += 1   # Modifie l'attribut de classe

# Création de plusieurs instances
c1 = Compteur(5)
c2 = Compteur(10)
c3 = Compteur(15)

print("\nCompteurs:")
print(f"c1.valeur = {c1.valeur}")  # Attribut d'instance: 5
print(f"c2.valeur = {c2.valeur}")  # Attribut d'instance: 10
print(f"c3.valeur = {c3.valeur}")  # Attribut d'instance: 15
print(f"Nombre de compteurs: {Compteur.total}")  # Attribut de classe: 3
```

### Question 4 : Héritage
**Réponse correcte : C) `class Fille(Parent): # code`**

En Python, l'héritage est spécifié en plaçant le nom de la classe parente entre parenthèses après le nom de la classe fille. Une classe peut hériter de plusieurs classes en les séparant par des virgules dans les parenthèses (héritage multiple).

**Exemple :**
```python
# Classe parente (superclasse)
class Animal:
    def __init__(self, nom):
        self.nom = nom
    
    def manger(self):
        return f"{self.nom} est en train de manger."
    
    def dormir(self):
        return f"{self.nom} est en train de dormir."

# Classe fille (sous-classe) héritant de Animal
class Chien(Animal):
    def __init__(self, nom, race):
        # Appel du constructeur de la classe parente
        super().__init__(nom)
        self.race = race
    
    def aboyer(self):
        return f"{self.nom} aboie: Wouaf!"
    
    # Redéfinition (override) d'une méthode de la classe parente
    def dormir(self):
        return f"{self.nom} ronfle paisiblement."

# Création d'instances
animal = Animal("Créature")
chien = Chien("Rex", "Berger Allemand")

# Utilisation des méthodes
print(animal.manger())   # Méthode de Animal: Créature est en train de manger.
print(chien.manger())    # Méthode héritée: Rex est en train de manger.
print(chien.aboyer())    # Méthode spécifique à Chien: Rex aboie: Wouaf!
print(animal.dormir())   # Méthode de Animal: Créature est en train de dormir.
print(chien.dormir())    # Méthode redéfinie: Rex ronfle paisiblement.

# Vérification du type et des relations d'héritage
print(f"chien est une instance de Chien: {isinstance(chien, Chien)}")       # True
print(f"chien est aussi une instance de Animal: {isinstance(chien, Animal)}") # True
print(f"animal est une instance de Chien: {isinstance(animal, Chien)}")     # False

# Exemple d'héritage multiple
class Mammifere:
    def allaiter(self):
        return "Allaite ses petits"

class Aquatique:
    def nager(self):
        return "Nage dans l'eau"

# Classe héritant de plusieurs classes parentes
class Dauphin(Mammifere, Aquatique):
    def __init__(self, nom):
        self.nom = nom

# Utilisation de l'héritage multiple
flipper = Dauphin("Flipper")
print(f"{flipper.nom} peut nager: {flipper.nager()}")
print(f"{flipper.nom} est un mammifère: {flipper.allaiter()}")
```

### Question 5 : Méthodes spéciales
**Réponse correcte : B) `__add__(self, other)`**

Pour permettre l'utilisation de l'opérateur `+` entre deux instances d'une classe, il faut implémenter la méthode spéciale `__add__`. Cette méthode prend deux paramètres : `self` (l'instance sur laquelle la méthode est appelée) et `other` (l'instance qui est ajoutée). Python appelle automatiquement cette méthode lorsque l'opérateur `+` est utilisé avec des instances de cette classe.

**Exemple :**
```python
class Point:
    def __init__(self, x, y):
        self.x = x
        self.y = y
    
    def __add__(self, other):
        # Permet d'additionner deux points en additionnant leurs coordonnées
        return Point(self.x + other.x, self.y + other.y)
    
    def __str__(self):
        # Pour afficher le point de façon lisible
        return f"Point({self.x}, {self.y})"

# Création de deux points
p1 = Point(1, 2)
p2 = Point(3, 4)

# Addition des points avec l'opérateur +
p3 = p1 + p2

print(p1)  # Affiche: Point(1, 2)
print(p2)  # Affiche: Point(3, 4)
print(p3)  # Affiche: Point(4, 6)
```

Dans cet exemple, nous définissons une classe `Point` avec une méthode `__add__` qui permet d'additionner deux points en créant un nouveau point dont les coordonnées sont la somme des coordonnées des points originaux. L'opérateur `+` entre deux instances de `Point` appelle automatiquement cette méthode.

### Question 6 : Encapsulation
**Réponse correcte : B) Préfixer le nom de l'attribut avec un double underscore `__`**

En Python, il n'existe pas de mécanisme strict pour rendre les attributs privés comme dans d'autres langages orientés objet. Cependant, une convention consiste à préfixer les noms d'attributs avec un double underscore (`__`). Cela déclenche le "name mangling" (déformation de nom) en Python, ce qui rend l'attribut plus difficile à accéder depuis l'extérieur de la classe (mais pas impossible). C'est une façon de signaler que l'attribut est destiné à un usage interne de la classe.

**Exemple :**
```python
# Démonstration des différentes conventions d'encapsulation en Python

class CompteBancaire:
    def __init__(self, proprietaire, solde_initial):
        self.proprietaire = proprietaire      # Attribut public
        self._solde = solde_initial           # Convention: attribut "protégé" (underscore simple)
        self.__numero_secret = "123456"       # Convention: attribut "privé" (double underscore)
    
    def depot(self, montant):
        """Méthode publique pour déposer de l'argent"""
        if montant > 0:
            self._solde += montant
            print(f"Dépôt de {montant}€ effectué. Nouveau solde: {self._solde}€")
        else:
            print("Le montant du dépôt doit être positif")
    
    def retrait(self, montant):
        """Méthode publique pour retirer de l'argent"""
        if 0 < montant <= self._solde:
            self._solde -= montant
            print(f"Retrait de {montant}€ effectué. Nouveau solde: {self._solde}€")
        else:
            print("Montant invalide ou solde insuffisant")
    
    def _calculer_interets(self):
        """Méthode "protégée" pour calculer les intérêts (usage interne)"""
        return self._solde * 0.02
    
    def __operation_secrete(self):
        """Méthode "privée" (usage strictement interne à la classe)"""
        print("Opération secrète en cours...")
    
    def obtenir_infos(self):
        """Méthode publique pour accéder aux informations du compte"""
        self.__operation_secrete()  # La classe peut accéder à ses propres méthodes privées
        interet = self._calculer_interets()
        return f"Propriétaire: {self.proprietaire}, Solde: {self._solde}€, Intérêts annuels: {interet}€"

# Création d'un compte
compte = CompteBancaire("Alice", 1000)

# Accès et manipulation des attributs
print(compte.proprietaire)  # Accès normal à un attribut public: "Alice"
compte.proprietaire = "Bob"  # Modification d'un attribut public
print(compte.proprietaire)  # Affiche: "Bob"

# Accès à l'attribut "protégé" - techniquement possible mais déconseillé
print(compte._solde)  # Affiche: 1000

# Tentative d'accès à l'attribut "privé"
try:
    print(compte.__numero_secret)  # Génère une AttributeError
except AttributeError as e:
    print(f"Erreur: {e}")

# Le "name mangling" transforme __numero_secret en _CompteBancaire__numero_secret
# Ce n'est pas vraiment privé, mais difficile à accéder par accident
print(compte._CompteBancaire__numero_secret)  # Affiche: "123456"

# Utilisation des méthodes publiques
compte.depot(500)  # Utilisation normale
compte.retrait(200)  # Utilisation normale

# On peut accéder à la méthode protégée, mais ce n'est pas recommandé
print(f"Intérêts calculés directement: {compte._calculer_interets()}€")

# Tentative d'accès à la méthode privée
try:
    compte.__operation_secrete()  # Génère une AttributeError
except AttributeError as e:
    print(f"Erreur: {e}")

# Accès aux informations via la méthode publique
print(compte.obtenir_infos())

# Résumé des conventions d'encapsulation en Python:
# - attribut         : public, accessible de partout
# - _attribut        : protégé, devrait être utilisé seulement par la classe et ses sous-classes
# - __attribut       : privé, devrait être utilisé seulement à l'intérieur de la classe
``` 