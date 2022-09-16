# JavaScript Code Design

There's always different ways to structure code.

## Pseudo-Classical Pattern
We can use a constructor function.  Here, we are taking the unique attributes of a function for the purpose of creating objects.
All instances of game will have these unique attributes of the function body. 
In our case, we want each new game to work with a manipulated word bank. It would be like each new Dog instance has a different name;
Also, our new game will always have these important attributes.
Since that is the case, you can see how me manipulate it to our advantage.
We only go on creating the game if certain criteria is met.

```javascript
 var randomWord = function() {
    var words = ['apple', 'banana', 'orange', 'pear'];
    return function() {
      //get word and remove it from selection
      return word;
    };
  }();
function Game() {
    this.incorrect = 0;
    this.lettersGuessed = [];
    this.correctSpaces = 0;
    this.word = randomWord();
    if (!this.word) {
      this.displayMessage("Sorry, I've run out of words!");
      this.hideReplayLink();
      return this;
    }
    this.word = this.word.split("");
    this.init();
  }

let game = new Game();
```

Each new game has access to  functionality/behaviors.
new games are initialized by setting up the view and 
event listeners
```javascript
init: function() {
      this.bind();
      this.setClass();
      this.hideReplayLink();
      this.emptyGuesses();
      this.createBlanks();
      this.setGameStatus();
      this.displayMessage("");
    }
```

We can put the shared code in the prototype object. 
```javascript 
Game.prototype = {
  guesses: 6,
  createBlanks: function() {},
  fillBlanksFor: function(letter) { });
  },
  emptyGuesses: function() {;},
  renderGuess: function(letter) {},
  renderIncorrectGuess: function(letter) {},
  duplicateGuess: function(letter) {},
  setClass: function() {},
  displayMessage: function(text) {},
  showReplayLink: function() {},
  hideReplayLink: function() {},
  processGuess: function(e) {},
  win: function() {},
  lose: function() {},
  setGameStatus: function(status) {},
  bind: function() {},
  unbind: function() {},
};
```

altogether:

```javascript
document.addEventListener('DOMContentLoaded', event => {
  const message = document.querySelector("#message");
  const letters = document.querySelector("#spaces");
  const guesses = document.querySelector("#guesses");
  const apples = document.querySelector("#apples");
  const replay = document.querySelector("#replay");

  var randomWord = function() {}();

  function Game() {
    this.incorrect = 0;
    this.lettersGuessed = [];
    this.correctSpaces = 0;
    this.word = randomWord();
    if (!this.word) {
      this.displayMessage("Sorry, I've run out of words!");
      this.hideReplayLink();
      return this;
    }
    this.word = this.word.split("");
    this.init();
  }

  Game.prototype = {
    guesses: 6,
    createBlanks: function() {},
    fillBlanksFor: function(letter) { });
    },
    emptyGuesses: function() {;},
    renderGuess: function(letter) {},
    renderIncorrectGuess: function(letter) {},
    duplicateGuess: function(letter) {},
    setClass: function() {},
    displayMessage: function(text) {},
    showReplayLink: function() {},
    hideReplayLink: function() {},
    processGuess: function(e) {},
    win: function() {},
    lose: function() {},
    setGameStatus: function(status) {},
    bind: function() {},
    unbind: function() {},
  };

  function notALetter(letter) {
    return letter < 'a' || letter > 'z';
  }

  new Game();

  replay.addEventListener("click", function(e) {
    e.preventDefault();
    new Game();
  });
});
```