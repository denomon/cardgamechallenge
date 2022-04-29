# Card Game Challenge

## Project setup
```
npm install
```

### Compiles and hot-reloads for development
```
npm run serve
```

### Compiles and minifies for production
```
npm run build
```

### Lints and fixes files
```
npm run lint
```

### Customize configuration
See [Configuration Reference](https://cli.vuejs.org/config/).


# Card game challenge
## Instructions
1. The game involves a single deck of 52 cards.
2. Initially a single card is randomly chosen from the deck and displayed to the user face up.
 1. (As long as you use some sort of pseudo randomness to choose the cards then that is fine).
3. The user gets to choose if the next card is higher or lower than the one displayed.
4. The user submits their choice and the next card is displayed.
5. If their guess is correct then they continue the game until they have correctly guessed 5 times at which point they are given a message indicating that they have won the game. At this point there will be 5 cards laid face up.
6. If at any point their guess is wrong then the game stops and they are told they have lost.
7. If the card dealt is of the same value as the previous card then that constitutes an incorrect guess and they lose.
8. The value of the cards from lowest to highest goes:
   2 3 4 5 6 7 8 9 10 J Q K A
9. At the end of the game they should be given the chance to start a new game.
10. For extra marks a record should be displayed onscreen of their number of wins vs losses (which does not need to persist after browser refresh).
