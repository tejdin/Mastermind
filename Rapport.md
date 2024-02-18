# Rapport - Mastermind

## Choix de conception

On a cherché à mutualiser un maximum de code, via de nombreuses classes abstraites.

Pour le calcul du score, nous avions d'abord opté pour une variable stockée dans le plateau
lui-même et qui serait modifiée à la fin de la partie entière. Ainsi, le score ne serait calculée qu'une fois,
et affichée qu'une fois. Néanmoins, il nous a semblé pertinent d'améliorer le feedback, en proposant un score
s'affichant plus régulièrement. Ainsi, nous stockons le score de chaque manche dans leur
modèle ; un élement graphique, mis à jour à chaque manche (Turn) (simple addition du score total actuel avec celui
de la dernière manche), montre au joueur son score total actuel et celui de la manche qu'il vient de jouer.

En plus du MVC et des observers imposés, nous utilisons un __Builder__ pour simplifier la création du plateau et
la génération du code secret. Un __médiateur__ viendra simplifier les interactions entre les boutons de choix de
couleur et le controller de round. Les différentes versions de l'affichage d'une correction (correction) sont gérées
via un design pattern __strategy__.

Tous les paramètres sont stocké dans une classe (agissant presque comme un Record) nommée GameConfig. Elle permet
de résumer l'ensemble des besoins du jeu en un seul objet.

## Noms
A propos des termes problématiques ou ambiguës :
- Les "essais d'un joueur" décrit dans l'énoncé, soit l'ensemble d'un essai (attempt) et de sa correction (correction),
  portent le nom "Round" 
- Les "manches" décrites dans l'énoncé, soit l'ensemble des Rounds ayant permis ou non au joueur de trouver le code secret,
  portent le nom "Turn"