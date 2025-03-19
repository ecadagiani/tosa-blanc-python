# Chapitre 3 : Structures de Contrôle

## Questions

### Question 1 : Instructions conditionnelles
Quelle affirmation est vraie à propos des instructions conditionnelles en Python ?
- A) Les blocs if doivent toujours être accompagnés d'un bloc else
- B) On peut avoir plusieurs blocs elif mais un seul bloc else
- C) Les blocs if, elif et else doivent être délimités par des accolades {}
- D) Les conditions doivent obligatoirement être entourées de parenthèses

### Question 2 : Boucles for
Quelle est la principale différence entre les boucles for en Python et dans d'autres langages comme C ou Java ?
- A) Python n'a pas de boucle `for`, seulement while
- B) Les boucles `for` de Python itèrent seulement sur des séquences d'objets
- C) Les boucles `for` de Python ne peuvent pas utiliser de compteur
- D) Les boucles `for` de Python sont plus lentes que dans les autres langages

### Question 3 : Itération avec for
Quel est le résultat de l'exécution du code suivant ?
```python
somme = 0
for i in range(1, 5):
    somme += i
print(somme)
```
- A) `10`
- B) `15`
- C) `6`
- D) `4`

### Question 4 : Boucles while
Quel est le résultat de l'exécution du code suivant ?
```python
i = 0
while i < 5:
    i += 2
print(i)
```
- A) `4`
- B) `5`
- C) `6`
- D) `8`

### Question 5 : Instruction break
Quelle affirmation est correcte concernant l'instruction `break` ?
- A) Elle met fin uniquement à l'itération courante d'une boucle
- B) Elle met fin à la boucle la plus interne et continue l'exécution après la boucle
- C) Elle termine complètement le programme
- D) Elle est utilisée uniquement dans les instructions conditionnelles (if)

### Question 6 : Instruction continue
Que fait l'instruction `continue` dans une boucle ?
- A) Elle passe à l'itération suivante de la boucle
- B) Elle réinitialise la condition de la boucle
- C) Elle termine la boucle et continue l'exécution après la boucle
- D) Elle affiche la valeur actuelle de l'itérateur

### Question 7 : Mot-clé pass
À quoi sert le mot-clé `pass` en Python ?
- A) Il permet de sauter une itération dans une boucle
- B) Il sert à définir un bloc de code vide qui ne fait rien
- C) Il interrompt l'exécution du programme
- D) Il vérifie si une condition est vraie

### Question 8 : Opérateur ternaire
Quelle est la syntaxe correcte pour l'opérateur ternaire (expression conditionnelle) en Python ?
- A) `condition ? valeur_si_vrai : valeur_si_faux`
- B) `valeur_si_vrai if condition else valeur_si_faux`
- C) `if(condition) valeur_si_vrai else valeur_si_faux`
- D) `condition ? then valeur_si_vrai else valeur_si_faux` 