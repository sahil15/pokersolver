## Description
pokersolver is a poker hand solver and comparison tool written in Javascript. 

* Evaluating a hand of up to 7 cards
* Calculating the score of the hand (0-9)
* Returning the name of the hand (Pair, Flush, etc)
* Returning a detailed description (Two Pair, A's & 8's)
* Comparing an array of hands and returning the winner(s)
* Identifying all cards involved in creating the winning hand
* Support for wilds and other game types
* Works in both the browser and Node.js

Solve two hands and then determine the winner between the two of them.
```javascript
var hand1 = Hand.solve(['Ad', 'As', 'Jc', 'Th', '2d', '3c', 'Kd']);
var hand2 = Hand.solve(['Ad', 'As', 'Jc', 'Th', '2d', 'Qs', 'Qd']);
var winner = Hand.winners([hand1, hand2]); // hand2
```

Solve a hand and return the type and the description.
```javascript
var hand = Hand.solve(['Ad', 'As', 'Jc', 'Th', '2d', 'Qs', 'Qd']);
console.log(hand.name); // Two Pair
console.log(hand.descr); // Two Pair, A's & Q's
```

## API
### Hand Methods
#### solve(cards, game, canDisqualify)
Solves the hand passed in, whether 3 cards or 7. Returns various information such as name, description, score and cards involved.
* **cards**: `Array` All cards involved in the hand, example: `['Ad', '2d', '3d', '4d', 'Qc', 'Ks', '7h']`. Note that a `10` should be passed as a `T` (`Th` for example).
* **game**: `String` Which rule set is used, based on the game being played. Default: 'standard'
* **canDisqualify**: `Boolean` Is this hand subject to qualification rules, which some games have? Default: false

#### winners(hands)
Compare the passed hands and determine which is the best hand(s). Can return multiple if there is a tie.
* **hands** `Array` All hands solved with `Hand.solve` that should be compared.

#### toString()
Returns a formatted string of all cards involved in the identified hand type (maximum of 5 cards).

### Solved Hand Properties
#### cardPool `Array`
All of the cards passed into the hand.
#### cards `Array`
All of the cards involved in the identified hand type.
#### descr `String`
Detailed description of the identified hand type (`Two Pair, A's & Q's` for example).
#### name `String`
Type of hand identified (`Two Pair` for example).
#### rank `Number`
Ranking of the hand type (Varies from game to game; 0 being the lowest hand).

#### solve(cards)
Solves the hand passed in, sets it according to House Way, and solves both hands.
* **cards**: `Array` All cards involved in the hand, example: `['Ad', '2d', '3d', '4d', 'Qc', 'Ks', '7h']`.

#### setHands(hiHand, loHand)
Sets the hands according to the input, and solves both hands.
* **hiHand** `Array` Five cards involved in the high hand, example: `['Ad', '2d', '3d', '4d', '7h']`.
* **loHand** `Array` Two cards involved in the low hand, example: `['Qc', 'Ks']`.

#### winners(player, banker)
Compare the hands and determine who wins. 1 = Player, -1 = Banker, 0 = Push.


#### baseHand `Hand`
All of the cards passed into the helper, run against `Hand.solve`.
#### hiHand `Hand`
Five card high hand, whether calculated or passed into the helper, run against `Hand.solve`.
#### loHand `Hand`
Two card low hand, whether calculated or passed into the helper, run against `Hand.solve`.



## Testing
```
npm install
npm test
```
