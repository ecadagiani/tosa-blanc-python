# Corrections - Chapitre 9 : Bonnes Pratiques et Optimisation

### Question 1 : Conventions de style
**Réponse correcte : C) Les noms de constantes doivent être en MAJUSCULES_AVEC_UNDERSCORES**

Selon les conventions de style PEP 8, les différentes conventions de nommage en Python sont:
- Les noms de classes utilisent la convention CapWords (ou PascalCase) : `MaClasse`
- Les noms de fonctions et variables utilisent snake_case (minuscules avec underscores) : `ma_fonction`, `ma_variable`
- Les noms de constantes sont en MAJUSCULES avec des underscores : `MA_CONSTANTE`
- Les méthodes privées et attributs commencent par un underscore : `_methode_privee`

**Exemple :**
```python
# Constante
PI = 3.14159
MAX_UTILISATEURS = 100

# Classe
class VoitureElectrique:
    # Méthode
    def calculer_autonomie(self, charge_actuelle):
        return charge_actuelle * self.autonomie_max

# Fonction
def convertir_kilometres_en_miles(kilometres):
    return kilometres * 0.621371

# Variable
distance_totale = 150
```

### Question 2 : Documentation du code
**Réponse correcte : B) 
```python
def fonction():
    """ Cette fonction fait quelque chose. """
    pass
```**

En Python, les docstrings sont des chaînes de documentation définies avec des triples guillemets (""" ou '''). Elles sont utilisées pour documenter des modules, classes, fonctions et méthodes. Contrairement aux commentaires ordinaires (qui commencent par #), les docstrings sont accessibles via l'attribut `__doc__` et sont utilisées par les outils de génération de documentation comme Sphinx.

**Exemple :**
```python
def calculer_moyenne(nombres):
    """
    Calcule la moyenne arithmétique d'une liste de nombres.
    
    Args:
        nombres (list): Une liste de nombres (int ou float)
        
    Returns:
        float: La moyenne des nombres
        
    Raises:
        ValueError: Si la liste est vide
        TypeError: Si la liste contient des éléments non numériques
    """
    if not nombres:
        raise ValueError("La liste ne peut pas être vide")
    
    return sum(nombres) / len(nombres)

# On peut accéder à la docstring ainsi
print(calculer_moyenne.__doc__)
```

### Question 3 : Tests
**Réponse correcte : C) `unittest`**

Python inclut le module `unittest` dans sa bibliothèque standard pour écrire et exécuter des tests unitaires. Ce module est inspiré par JUnit et fournit des classes et méthodes pour structurer les tests. D'autres frameworks de test comme `pytest` sont populaires mais ne font pas partie de la bibliothèque standard.

**Exemple :**
```python
import unittest

# Fonction à tester
def additionner(a, b):
    return a + b

# Classe de test
class TestAddition(unittest.TestCase):
    def test_addition_entiers_positifs(self):
        self.assertEqual(additionner(1, 2), 3)
        
    def test_addition_entiers_negatifs(self):
        self.assertEqual(additionner(-1, -1), -2)
        
    def test_addition_decimaux(self):
        self.assertAlmostEqual(additionner(0.1, 0.2), 0.3, places=1)
        
    def test_addition_chaines(self):
        # Vérifier qu'une exception TypeError est levée
        with self.assertRaises(TypeError):
            additionner("1", 2)

# Exécuter les tests si le script est lancé directement
if __name__ == '__main__':
    unittest.main()
```