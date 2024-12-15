# ICO - Intelligence Collaborative Optimization

## Description
Ce projet porte sur l'optimisation collaborative dans le cadre du **Vehicle Routing Problem (VRP)**, un problème NP-difficile, où l'objectif est de minimiser les coûts associés aux tournées de véhicules (distances parcourues, nombre de véhicules utilisés). Nous avons débuté par l'application de trois métaheuristiques classiques (algorithme tabou, recuit simulé, algorithme génétique) afin de résoudre ce problème. Par la suite, nous avons exploré des approches plus collaboratives avec des protocoles multi-agents (amis/ennemis) et amélioré les performances grâce à des méthodes d'apprentissage par renforcement (Q-learning).

## Détails des algorithmes utilisés

### 1. Résolution par métaheuristiques
Nous avons d'abord implémenté trois algorithmes métaheuristiques pour résoudre le problème d'ordonnancement des tournées de véhicules :

- **Algorithme tabou** :
  - Cet algorithme explore les solutions voisines de manière itérative et maintient une liste tabou pour éviter de revisiter les mêmes solutions.
  - Les voisins sont générés par des permutations aléatoires des clients, comme l'échange de deux clients ou le déplacement d'un client vers une autre position.
  - Résultats notables : réduction progressive du coût des tournées à chaque itération.  
  ![Figure 3 - Réduction progressive du coût](images/figure3.png)

- **Recuit simulé** :
  - Inspiré du processus de refroidissement des métaux, cet algorithme alterne entre exploration et exploitation grâce à une température décroissante.
  - Les voisins sont générés en modifiant les routes existantes via des stratégies telles que l'échange entre routes ou le déplacement au sein d'une même route.
  - Résultats : meilleur équilibre entre exploration globale et convergence rapide.  
  ![Figure 6 - Comparaison des méthodes de voisinage](images/figure6.png)

- **Algorithme génétique** :
  - Cet algorithme imite les mécanismes de l'évolution biologique (sélection, croisement, mutation).
  - Une population initiale de solutions est générée aléatoirement, puis affinée au fil des itérations pour améliorer la qualité des solutions.
  - Paramètres importants : taille de la population, probabilités de croisement et de mutation.  
  ![Figure 14 - Evolution du coût](images/figure14.png)

### 2. Protocoles multi-agents
Pour exploiter les avantages des métaheuristiques, nous avons développé deux protocoles de collaboration entre agents :

- **Protocole Ami** :
  - Les agents partagent leurs meilleures solutions via un pool collaboratif.
  - Cela permet une convergence plus rapide vers des solutions optimales grâce à une exploration guidée.  
  ![Figure 38 - Meilleure solution avec le protocole Ami](images/figure38.png)

- **Protocole Ennemi** :
  - Les agents fonctionnent en compétition, chaque équipe tentant de surpasser les solutions de l'autre.
  - Ce protocole encourage une amélioration continue des performances des agents.  
  ![Figure 40 - Résultats du protocole Ennemi](images/figure40.png)

### 3. Renforcement par Q-learning
Pour aller encore plus loin dans l'optimisation, nous avons intégré un apprentissage par renforcement (Q-learning) dans nos métaheuristiques :

- Les voisins sont évalués en fonction de leur coût et les meilleures solutions sont favorisées pour guider l'exploration.
- Une stratégie E-greedy équilibre l'exploitation des solutions optimales et l'exploration de nouvelles options.
- Résultats : amélioration significative des solutions, avec une réduction notable des distances totales parcourues.  
  ![Figure 43 - Influence de E-greedy sur les solutions](images/figure43.png)

## Résultats principaux

### Comparaison des métaheuristiques
- Les métaheuristiques ont été testées sur des bases de données de tailles différentes. Par exemple, pour une base de 20 clients :
  - Tabou : coût optimal ≈ 260.
  - Recuit simulé : coût optimal ≈ 255.
  - Génétique : coût optimal ≈ 250.  
  ![Figure 3 - Comparaison des métaheuristiques](images/figure3.png)

- Pour une base complète de 107 clients, l'algorithme génétique converge plus rapidement et donne une solution meilleure.  
  ![Figure 36 - Comparaison des algorithmes](images/figure36.png)

### Protocole Ami
- Le protocole Ami améliore de 180 points les solutions obtenues par les métaheuristiques seules.  
  ![Figure 38 - Meilleure solution trouvée avec le protocole Ami](images/figure38.png)

### Protocole Ennemi
- Avec le protocole Ennemi, les équipes d'agents convergent vers une solution optimale où chaque équipe atteint un plateau.  
  ![Figure 40 - Résultats du protocole Ennemi](images/figure40.png)

### Apprentissage par renforcement
- Avec Q-learning, la meilleure solution obtenue est ≈ 379 km (E-greedy = 0.02), contre 530 km sans Q-learning.  
  ![Figure 43 - Influence de E-greedy sur les solutions](images/figure43.png)

### Résultats finaux
- Les métaheuristiques seules atteignent un coût final d'environ 560.
- En combinant SMA et Q-learning, le coût final est réduit à ≈ 350.  
  ![Figure 44 - Résultats finaux](images/figure44.png)

## Auteurs
- Matthieu Richard, Ilyasse Chaouki, Antoine Deschamps, Virgile Devillers, Antoine Greaume

## Licence
Ce projet est distribué sous la licence MIT.
