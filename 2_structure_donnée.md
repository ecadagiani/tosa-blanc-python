# Chapitre 2 : Structures de Données

## Questions

### Question 1 : Listes en Python
Quelle est la différence fondamentale entre une liste et un tuple en Python ?
- A) Les listes peuvent contenir n'importe quel type de données alors que les tuples ne peuvent contenir que des nombres
- B) Les listes sont indexées à partir de 0, les tuples à partir de 1
- C) Les listes sont mutables (modifiables) alors que les tuples sont immuables (non modifiables)
- D) Les listes peuvent être itérées, les tuples ne le peuvent pas

### Question 2 : Opérations sur les listes
Quel est le résultat de l'expression suivante : `[1, 2, 3] * 2` ?
- A) `[1, 2, 3, 1, 2, 3]`
- B) `[2, 4, 6]`
- C) `[1, 1, 2, 2, 3, 3]`
- D) `[1, 2, 3, 2]`

### Question 3 : Modification de listes
Que fait la méthode `append()` sur une liste ?
- A) Elle ajoute un élément à l'index spécifié de la liste
- B) Elle ajoute un élément à la fin de la liste
- C) Elle fusionne deux listes
- D) Elle trie la liste et ajoute le nouvel élément à sa position correcte

### Question 4 : Tuples en Python (2 réponses attendues)
Quelle est la syntaxe correcte pour créer un tuple contenant un seul élément ?
- A) `tuple = (1)`
- B) `tuple = [1]`
- C) `tuple = (1,)`
- D) `tuple = 1,`

### Question 5 : Dictionnaires
Quel code permet de récupérer toutes les clés d'un dictionnaire nommé `mon_dict` ?
- A) `mon_dict.keys()`
- B) `mon_dict.get_keys()`
- C) `keys(mon_dict)`
- D) `mon_dict.all_keys()`

### Question 6 : Opérations sur les dictionnaires
Que se passe-t-il quand on essaie d'accéder à une clé qui n'existe pas dans un dictionnaire avec la syntaxe `mon_dict['clé_inexistante']` ?
- A) Renvoie `None`
- B) Crée automatiquement la clé avec une valeur vide
- C) Lève une exception `KeyError`
- D) Renvoie une chaîne vide `""`

### Question 7 : Ensembles (sets)
Quelle est la particularité d'un ensemble (set) en Python ?
- A) Il est ordonné et peut contenir des doublons
- B) Il est ordonné et ne peut pas contenir de doublons
- C) Il n'est pas ordonné et peut contenir des doublons
- D) Il n'est pas ordonné et ne peut pas contenir de doublons

### Question 8 : Opérations sur les ensembles
Quelle méthode permet d'ajouter un élément à un ensemble (set) ?
- A) `set.append(élément)`
- B) `set.extend(élément)`
- C) `set.add(élément)`
- D) `set.insert(élément)`

### Question 9 : Compréhensions de listes
Quel est le résultat de la compréhension de liste suivante : `[x**2 for x in range(5) if x % 2 == 0]` ?
- A) `[0, 4, 16]`
- B) `[0, 1, 4, 9, 16]`
- C) `[0, 2, 4]`
- D) `[0, 4]`

### Question 10 : Méthodes de chaînes de caractères
Quelle méthode permet de diviser une chaîne en une liste de sous-chaînes à partir d'un séparateur ?
- A) `split()`
- B) `slice()`
- C) `divide()`
- D) `cut()`