# Corrections - Chapitre 7 : Manipulation de Fichiers et Données

### Question 1 : Ouverture de fichiers
**Réponse correcte : B) `with open("data.txt", "r") as file: ...`**

La meilleure pratique pour ouvrir des fichiers en Python est d'utiliser le gestionnaire de contexte `with`. Cette approche garantit que le fichier sera correctement fermé à la fin du bloc, même si une exception est levée. Cela évite les fuites de ressources et simplifie le code en éliminant la nécessité d'appeler explicitement `file.close()`.

**Exemple :**
```python
# Lecture d'un fichier avec le gestionnaire de contexte
with open("data.txt", "r") as fichier:
    contenu = fichier.read()
    print(contenu)
# À ce point, le fichier est automatiquement fermé
```

### Question 2 : Modes d'ouverture de fichiers
**Réponse correcte : B) `w+`**

Le mode `w+` permet d'ouvrir un fichier en lecture et écriture. Si le fichier existe, son contenu est effacé. Si le fichier n'existe pas, il est créé. Les autres modes:
- `r+` : Lecture et écriture, mais le fichier doit exister
- `a+` : Lecture et écriture, ajout à la fin du fichier (sans effacer), crée le fichier s'il n'existe pas
- `rw` n'est pas un mode valide en Python

**Exemple :**
```python
with open("nouveau_fichier.txt", "w+") as f:
    f.write("Première ligne\n")
    f.write("Deuxième ligne\n")
    
    # Retour au début du fichier pour lire le contenu
    f.seek(0)
    contenu = f.read()
    print(contenu)
```

### Question 3 : Manipulation de fichiers CSV
**Réponse correcte : B) `csv`**

Python inclut le module `csv` dans sa bibliothèque standard pour faciliter la lecture et l'écriture de fichiers CSV (Comma-Separated Values). Ce module fournit des classes et des fonctions pour travailler avec différents formats CSV et gère les détails comme les délimiteurs, les guillemets et les caractères d'échappement.

**Exemple :**
```python
import csv

# Écriture dans un fichier CSV
with open('donnees.csv', 'w', newline='') as fichier:
    writer = csv.writer(fichier)
    writer.writerow(['Nom', 'Âge', 'Ville'])
    writer.writerow(['Alice', 30, 'Paris'])
    writer.writerow(['Bob', 25, 'Lyon'])

# Lecture d'un fichier CSV
with open('donnees.csv', 'r') as fichier:
    reader = csv.reader(fichier)
    for ligne in reader:
        print(ligne)
```

### Question 4 : Sérialisation avec JSON
**Réponse correcte : D) `json.dumps()` et `json.loads()`**

Le module `json` de Python utilise les méthodes `dumps()` (dump string) pour convertir des objets Python en chaînes JSON et `loads()` (load string) pour convertir des chaînes JSON en objets Python. Pour travailler directement avec des fichiers, le module fournit également les méthodes `dump()` et `load()`.

**Exemple :**
```python
import json

# Création d'un dictionnaire Python
donnees = {
    'nom': 'Alice',
    'age': 30,
    'ville': 'Paris',
    'langages': ['Python', 'JavaScript', 'SQL'],
    'actif': True
}

# Conversion Python → JSON (sérialisation)
json_str = json.dumps(donnees, indent=4)
print(json_str)

# Conversion JSON → Python (désérialisation)
donnees_python = json.loads(json_str)
print(donnees_python['langages'][0])  # Affiche: Python

# Écriture directe dans un fichier JSON
with open('donnees.json', 'w') as f:
    json.dump(donnees, f, indent=4)

# Lecture directe depuis un fichier JSON
with open('donnees.json', 'r') as f:
    donnees_lues = json.load(f)
```