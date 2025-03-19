# Corrections - Chapitre 6 : Gestion des Erreurs et Débogage

### Question 1 : Gestion des exceptions
**Réponse correcte : B) `try: # code except Exception as e: # gestion`**

En Python, la gestion des exceptions se fait avec les blocs `try` et `except`. Le code susceptible de générer une exception est placé dans le bloc `try`, et le traitement à effectuer en cas d'exception est placé dans le bloc `except`. La variable qui suit `as` permet de récupérer l'objet exception pour l'utiliser dans le bloc de gestion.

**Exemple :**
```python
try:
    resultat = 10 / 0  # Cette ligne va générer une ZeroDivisionError
except ZeroDivisionError as e:
    print(f"Une erreur s'est produite: {e}")
    resultat = None
```

### Question 2 : Types d'exceptions
**Réponse correcte : C) `ZeroDivisionError`**

En Python, l'exception `ZeroDivisionError` est levée lorsqu'on tente de diviser un nombre par zéro. C'est une sous-classe de `ArithmeticError`, elle-même sous-classe de `Exception`. Python possède une hiérarchie d'exceptions bien définie, et il est important de connaître les types d'exceptions courants pour les gérer correctement.

### Question 3 : Structure try/except/else/finally
**Réponse correcte : B) Quand aucune exception n'est levée dans le bloc try**

Dans une structure try/except/else/finally, le bloc `else` est exécuté uniquement si aucune exception n'est levée dans le bloc `try`. C'est un moyen de séparer le code qui peut générer des exceptions du code qui devrait s'exécuter seulement si tout s'est bien passé. Le bloc `finally`, quant à lui, s'exécute toujours, qu'une exception ait été levée ou non.

**Exemple :**
```python
try:
    fichier = open("donnees.txt", "r")
    contenu = fichier.read()
except FileNotFoundError:
    print("Le fichier n'existe pas")
else:
    # Ce bloc s'exécute si aucune exception n'est levée
    print(f"Le fichier contient {len(contenu)} caractères")
    fichier.close()
finally:
    # Ce bloc s'exécute toujours
    print("Opération terminée")
```

### Question 4 : Levée d'exceptions
**Réponse correcte : B) `raise Exception("message")`**

Pour lever manuellement une exception en Python, on utilise le mot-clé `raise` suivi du type d'exception à lever et éventuellement d'un message d'erreur. On peut lever des exceptions standards de Python ou des exceptions personnalisées qui héritent de la classe `Exception`.

**Exemple :**
```python
def verifier_age(age):
    if age < 0:
        raise ValueError("L'âge ne peut pas être négatif")
    elif age < 18:
        raise Exception("Vous devez être majeur")
    return "Âge valide"

try:
    resultat = verifier_age(-5)
    print(resultat)
except ValueError as e:
    print(f"Erreur de valeur: {e}")
except Exception as e:
    print(f"Autre erreur: {e}")
```

Dans cet exemple, la fonction `verifier_age` lève deux types d'exceptions différents selon la valeur de l'âge, et le bloc try/except qui l'entoure gère ces exceptions de manière appropriée. 