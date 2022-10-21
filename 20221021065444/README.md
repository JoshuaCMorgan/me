# disable a HTMLButtonElement 

You may want too disable a button's default behavior

Below, you'll see that we have `input` submit button. 

- css has a psuedo selector, on line 2

```html
 <style>
	input[type="submit"]:disabled {
    background: #ccc;
    border-color: #ccc;
    box-shadow: none;
  }
  input[type="submit"] {
    display: block;
    width: 100%;
   }
</style>
<body>
    <main>
      <h1>Number Guessing Game</h1>
      <p>Loading...</p>
      <form action="" method="get">
        <fieldset>
          <input type="text" id="guess" maxlength="3" />
          <input type="submit" value="Guess" />
        </fieldset>
      </form>
      <a href="#">New game</a>
    </main>
    <script src="javascript.js"></script>
  </body>
```

If we wanted to disable this at any time...

- On line two, we invoke `disabled` on the element (the retrieval and setting not shown) and set to `false`.  `disabled` takes a boolean
- on line 22, we set `disabled` to `true` if guessed properly.

```js
function newGame() {
    guessBtn.disabled = false;
    form.reset();
    answer = Math.floor(Math.random() * 100) + 1;
    guesses = 0;
    paragraph.textContent = 'Guess a number from 1 to 100';
  }

form.addEventListener('submit', event => {
    event.preventDefault();

    let guess = parseInt(input.value, 10);
    let message;

    guesses += 1;
    
     if (Number.isNaN(guess)) {
       message = 'Please enter a number';
     } else {
       if (guess === answer) {
       message = `You guessed it! It took you ${guesses} guesses.`;
       guessBtn.disabled = true;
      //rest of code removed
  })
```

#disable #button