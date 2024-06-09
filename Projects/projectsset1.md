# Projects related to DOM

## project link
[Click here](https://stackblitz.com/edit/dom-project-chaiaurcode?file=index.html)

```
JavaScript

const btns = document.querySelectorAll('.button');
const body = document.querySelector('body');

btns.forEach(function (button) {
  button.addEventListener('click', function (e) {
    // if (e.target.id == 'grey') body.style.backgroundColor = 'grey';
    // else if (e.target.id == 'white') body.style.backgroundColor = 'white';
    // else if (e.target.id == 'blue') body.style.backgroundColor = 'blue';
    // else if (e.target.id == 'yellow') body.style.backgroundColor = 'yellow';
    body.style.backgroundColor = e.target.id;
  });
});
`
```

# Project - digital clock
```
JavaScript

const clock = document.getElementById('clock');

setInterval(function () {
  let date = new Date();
  clock.innerHTML = date.toLocaleTimeString();
}, 1000);
```

```
Guess the number - JavaScript

let randomNumber = parseInt(Math.random() * 10 + 1);
const submit = document.querySelector('#subt');
const userInput = document.querySelector('#guessField');
const guessSlot = document.querySelector('.guesses');
const lastResult = document.querySelector('.lastResult');
const lowOrHi = document.querySelector('.lowOrHi');
const startOver = document.querySelector('.resultParas');

const p = document.createElement('p');
let prevGuess = [];
let numGuesses = 1;
let playGame = true;

if (playGame) {
  submit.addEventListener('click', function (e) {
    e.preventDefault();
    guess = parseInt(userInput.value);
    validateGuess(guess);
  });
}

function validateGuess(guess) {
  if (guess === '' || isNaN(guess)) {
    alert('Please give a valid number');
  } else if (guess < 1 || guess > 10) {
    alert('Please give a number between 1 and 100');
  } else {
    prevGuess.push(guess);
    if (numGuesses === 10) {
      displayGuess(guess);
      displayMessage(`Game Over, random number was ${randomNumber}`);
      endGame();
    } else {
      displayGuess(guess);
      checkGuess(guess);
    }
  }
}

function checkGuess(guess) {
  if (guess === randomNumber) {
    displayMessage('You guessed it right');
  } else if (guess < randomNumber) {
    displayMessage('Number is Too Low');
  } else {
    displayMessage('Number is Too High');
  }
}

function displayGuess(guess) {
  userInput.value = '';
  guessSlot.innerHTML += `${guess} `;
  numGuesses += 1;
  lastResult.innerHTML = `${11 - numGuesses}`;
}
function displayMessage(message) {
  lowOrHi.innerHTML = `<h2> ${message} </h2>`;
}

function endGame() {
  userInput.value = '';
  userInput.setAttribute('disabled', '');
  p.classList.add('button');
  p.innerHTML = '<h2 id="newgame"> Start a new Game</h2>';
  startOver.appendChild(p);
  playGame = false;
  newGame();
}

function newGame() {
  const button = document.querySelector('#newgame');
  button.addEventListener('click', function (e) {
    randomNumber = parseInt(Math.random() * 10 + 1);
    prevGuess = [];
    numGuesses = 1;
    guessSlot.innerHTML = '';
    lastResult.innerHTML = `${11 - numGuesses}`;
    lowOrHi.innerHTML = '';
    startOver.removeChild(p);
    userInput.removeAttribute('disabled');
    playGame = true;
  });
}

```

```
JavaScript - Keyboard Project
const insert = document.getElementById('insert');

window.addEventListener('keydown', (e) => {
  insert.innerHTML = `
    <div class = 'color'>
      <table>
      <tr>
        <th>Key</th>
        <th>KeyCode</th>
        <th>Code</th>
      </tr>
      <tr>
        <td>${e.key}</td>
        <td>${e.keyCode}</td>
        <td>${e.code}</td>
      </tr>
      </table>
    </div>
  `;
});

```


```
JavaScript- Unlimited Colors
const colorGenerator = function () {
  const hex = '0123456789ABCDEF';
  let color = '#';

  for (let i = 0; i < 6; i++) {
    color += hex[Math.floor(Math.random() * 16)];
  }
  return color;
};

let interval;
const startGenerator = function () {
  const bgChanger = function () {
    document.body.style.backgroundColor = colorGenerator();
  };
  interval = setInterval(bgChanger, 1000);
};

const stopGenerator = function () {
  clearInterval(interval);
  interval = null;
};

document.querySelector('#start').addEventListener('click', startGenerator);
document.querySelector('#stop').addEventListener('click', stopGenerator);

```
