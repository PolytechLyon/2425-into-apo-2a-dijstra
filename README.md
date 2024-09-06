# Calcule du chemin le plus court

Dans cet exercice, vous allez réaliser un code Java
qui calcule le chemin le moins coûteux entre un point de départ et un point d'arrivée.

## Modalités
* Cet exercice est noté.
* Il est à réaliser en binôme.
* Sauf exception approuvée par l'enseignant, vous ne devez pas réaliser cet exercice seul.
* Le compte rendu à remplir se trouve [ici](Rapport.md).

## Algorithme de Dijkstra
Étant donné un graphe orienté $G = (V, E)$ où :
* $V$ est un ensemble fini de sommets,
* $E \in V \times V \times \Bbb{R}^+$ est un ensemble fini des arcs pondérés par des réels positifs.

L'algorithme de Dijkstra sert à trouver les chemins les plus courts à partir d'un sommet $v_{0} \in V$
vers tous les autres sommets du graphe.
La distance parcourue par un chemin liant deux sommets est calculée en fonctionne de la somme des poids
des arcs qui constituent ce chemin.
Le chemin entre deux sommets et donc le plus court quand cette distance est minimale.

L'algorithme peut être décrit par le pseudocode suivant. 


> **entrée** : $G = (V, E)$, $v_{0} \in V$ (sommet de départ)
> * $U := \phi{} $
> * **pour chaque** $v \in V$
>   * $distances[v] := +\infty{} $
> * $distance[v_0] := 0$
> * **tant que** $V \setminus U \neq \phi{}$
>   * $v := \underset{x \in V \setminus U}{\arg \min} ~(distance[x])$ (le somment dans $V \setminus U$ où $distances[v]$ est minimal)
>   * $U := U \cup \\{ \{ v \} \\}$
>   * **pour chaque** $u \in V \setminus U$ où $\exists{} (v, u, w) \in E $
>     * $d := distances[v] + w$
>     * **si** $d < distances[u]$
>       * $distances[u] := d$

## Calcule de plus court voyage en train
Le fichier `input.txt` décrit les connexions par train entre différentes villes.

Nous voulons pouvoir calculer le trajet optimal, c'est-à-dire avec la durée totale la plus coutre,
à partir d'une ville donnée et vers toutes les autres villes accèssible par train depuis la ville de départ.

La durée totale est calculée à partir de la somme des durées individuelles de chaque voyage,
et sans prendre en compte le temps d'attente lors d'une connexion.

### Format de fichier d'entrée
Le fichier `input.txt` a le format suivant :
* Une liste des noms de toutes les villes desservies. Les noms sont séparés par des retours à la ligne.
* Une ligne vide séparant les noms de villes de leurs connexions.
* Une liste des connexions entre les villes.
Les connexions sont séparés par des retours à la ligne.
Chaque connexion est un triplet des élements suivants, dans l'ordre :
  * L'indice de la ville de départ, dans la liste des villes, en partant de zéro,
  * L'indice de la ville de destination, dans la liste des villes, en partant de zéro,
  * La durée de trajet en heure.

## Objectif

L'objectif est donc de créer une application Java qui permet, à partir des données d'entrée,
de calculer les trajets les plus courts vers chaque destination en utilisant l'algorithme de Dijkstra.

### Structure de données

Proposer des structures de données adaptées pour permettre une représentation du graphe orienté
et une exécution efficace de l'algorithme.

Par exemple,
la structure d'un sommet peut contenir une valeur booléenne pour indiquer si le sommet est visité
(appartient à l'ensemble $U$).
Une autre valeur peut indiquer la distance calculée à ce stade (valeurs du tableau $distances$).

### Construction du graphe

Réaliser un code qui construit le graphe décrit dans le fichier `input.txt`
selon la structure de données proposée.

Pour construire ce graphe, vous pouvez écrire un code qui remplit votre structure de donnée
d'une manière statique en suivant les informations dans le fichier `input.txt`.

Sinon, et de préférence, vous pouvez écrire un code qui lit le fichier `input.txt` et remplit dynamiquement
votre structure de données.

Pour vous aider à réaliser la lécture dynamique de fichier, la classe `com.acme.Convertor`, fourni dans ce dépôt,
donne un exemple d'un code qui lit un fichier du même format que `input.txt`
et le convertit en format dot, compris par des outils tel que `graphviz`.

### Determiner la plus courte durée pour atteindre une destination

Écrire un code qui réalise l'algorithme de Dijkstra pour calculer la durée optimale
pour atteindre chaque autre destination, si cela est possible, à partir d'une ville donnée.

Tester cet algorithme avec la ville de Lyon et la ville de Grenoble.

### Determiner le chemin le plus rapid pour atteindre une destination

Une variante de l'algorithme décrit ci-dessus peut être utilisé
pour determiner le chemin le plus court,
en plus de son coût optimal.
Cela peut se faire en ajustant l'algorithme
et éventuellement la structure de données associée.

Modifier le code pour pouvoir afficher le chemin le plus court vers chaque autre ville,
avec leurs coûts respectifs,
en partant d'une ville donnée.
Tester ce code avec la ville de Lyon et la ville de Grenoble.

### Passer le nom de ville en argument du programme

Faire en sort que le programme accepte en entrée le nom de ville.
Le code doit donc lister les chemins les plus courts et leurs durées pour atteindre
toutes les autres villes à partir de la ville dont le nom est passé en argument au programme.

## Ressources
* [Java et son Écosystème](https://docs.google.com/presentation/d/1b8Kfmd2WVZWY8TeAW6yfV6q3GUwcE5J-ppxUQBUYfZw).
* [Du code à l'exécution](https://docs.google.com/presentation/d/1IcpexTVIk0sD1hjwEoLNs4Ba4ggitTOej4rtZrTmgdw).
* [Éléments de langage](https://docs.google.com/presentation/d/1uJ_10-4d3ui-0dVb2ISOev4oR0jG3TWXOWfZ3QkP6kw).








