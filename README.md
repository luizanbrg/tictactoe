# Projet Tic-Tac-Toe

Ce projet est une application de jeu Tic-Tac-Toe développée en Java. Il utilise Swing pour créer une interface graphique (GUI) qui permet à deux joueurs de s’affronter en temps réel. Le projet inclut des fonctionnalités pour détecter les conditions de victoire, alterner les tours des joueurs et gérer un match nul.

## Table des matières

1. [Fonctionnalités principales](#fonctionnalités-principales)
2. [Bibliothèques utilisées](#bibliothèques-utilisées)
3. [Architecture du projet](#architecture-du-projet)
4. [Explication du code et approches](#explication-du-code-et-approches)
5. [Fonctionnalités supplémentaires possibles](#fonctionnalités-supplémentaires-possibles)

## Fonctionnalités principales

- **Interface utilisateur graphique** : Utilisation de Swing pour construire l'interface.
- **Gestion de l'alternance des tours** : Le programme détermine aléatoirement qui commence et alterne entre les joueurs à chaque tour.
- **Conditions de victoire et match nul** : Le programme détecte les conditions de victoire et affiche un message de fin.
- **Style personnalisé** : Couleurs et polices sont personnalisées pour une expérience utilisateur plaisante.

## Bibliothèques utilisées

- `java.awt` : Fournit les composants de base de l'interface graphique et la gestion des événements.
- `javax.swing` : Offre les composants graphiques comme les `JFrame`, `JPanel`, `JLabel`, et `JButton` utilisés pour la création de l'interface utilisateur.

## Architecture du projet

Le programme est composé de deux parties principales :

1. **Interface utilisateur (GUI)** :
   - Les éléments principaux de la GUI incluent `JFrame` pour la fenêtre principale, `JPanel` pour les sections de titre et les boutons, et `JLabel` pour afficher le texte et les messages d'état.
   - Un tableau de `JButton` est utilisé pour représenter les neuf cases du plateau de jeu.

2. **Logique du jeu** :
   - Une logique est mise en place pour gérer les tours des joueurs, vérifier les combinaisons gagnantes et détecter les matchs nuls.
   - Une méthode `check()` examine toutes les conditions gagnantes, et `isBoardFull()` détecte un plateau rempli sans gagnant, entraînant un match nul.

## Explication du code et approches

### Initialisation des composants

La méthode `TicTacToe()` initialise les composants graphiques, configure leur apparence, ajoute des écouteurs d'événements et définit les paramètres de base du jeu.

```java
frame.setSize(800,800);
textfield.setFont(new Font("Ink Free", Font.BOLD, 75));
button_panel.setLayout(new GridLayout(3, 3));
```

- **Conception de la fenêtre** : La fenêtre est configurée avec une taille de 800x800 pixels et un agencement de bordure.
- **Tableau de boutons** : Utilisation d'un tableau de neuf `JButton` pour représenter les cases du plateau de jeu et gestion des clics par `ActionListener`.

### Gestion des tours

La méthode `firstTurn()` sélectionne aléatoirement le premier joueur, ce qui rend le jeu équitable. La variable `player1_turn` indique de manière booléenne si c'est le tour du joueur 1 (X) ou du joueur 2 (O).

```java
if (random.nextInt(2) == 0) {
    player1_turn = true;
    textfield.setText("X turn");
} else {
    player1_turn = false;
    textfield.setText("O turn");
}
```

### Détection des victoires et des matchs nuls

La méthode `check()` teste toutes les combinaisons gagnantes possibles pour les joueurs X et O. En cas de victoire, la méthode `xWins()` ou `oWins()` est appelée pour indiquer le vainqueur.

- **Composants désactivés** : Tous les boutons sont désactivés pour arrêter le jeu une fois la victoire ou le match nul détecté.
- **Couleur de fond** : Les cases gagnantes sont colorées en vert clair pour une meilleure visualisation.

```java
if ((buttons[0].getText() == "X") && (buttons[1].getText() == "X") && (buttons[2].getText() == "X")) {
    xWins(0,1,2);
}
```

### Résolution des défis techniques

- **Contrôle des entrées utilisateur** : Chaque clic de bouton vérifie si la case est vide avant de placer un symbole (`X` ou `O`). Cette approche évite les erreurs de saisie et garantit une intégrité du plateau.
- **Gestion des états** : La gestion de l'état `player1_turn` avec un `boolean` rend la logique simple et efficace pour alterner les tours.
- **Gestion de la synchronisation avec `Thread.sleep`** : Un léger délai de 1 seconde est ajouté avant de déterminer le premier tour pour offrir une expérience utilisateur plus fluide.

## Fonctionnalités supplémentaires possibles

1. **Rematch** : Ajouter une fonctionnalité de nouvelle partie sans redémarrer l'application.
2. **Score Tracking** : Ajouter un compteur de score pour suivre le nombre de victoires de chaque joueur.
3. **Mode contre l'ordinateur** : Créer une intelligence artificielle pour jouer contre l'ordinateur avec différents niveaux de difficulté.
