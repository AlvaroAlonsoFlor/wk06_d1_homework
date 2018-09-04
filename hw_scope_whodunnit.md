# Scope Homework: Who Dunnit

### Learning Objectives

- Understand function scope
- Know the difference in between the `let` and `const` keywords

## Brief

Using your knowledge about scope and variable declarations in JavaScript, look at the following code snippets and predict what the output or error will be and why.

### MVP

#### Episode 1

```js
const scenario = {
  murderer: 'Miss Scarlet',
  room: 'Library',
  weapon: 'Rope'
};

const declareMurderer = function() {
  return `The murderer is ${scenario.murderer}.`;
}

const verdict = declareMurderer();
console.log(verdict);

// The murderer is Miss Scarlet
```

#### Episode 2

```js
const murderer = 'Professor Plum';

const changeMurderer = function() {
  murderer = 'Mrs. Peacock';
}

// It is not possible to change a constant

const declareMurderer = function() {
  return `The murderer is ${murderer}.`;
}

changeMurderer();
const verdict = declareMurderer();
console.log(verdict);

// The murderer is Professor Plum
//Because murderer is a constant
```

#### Episode 3

```js
let murderer = 'Professor Plum';

const declareMurderer = function() {
  let murderer = 'Mrs. Peacock';
  return `The murderer is ${murderer}.`;
}

const firstVerdict = declareMurderer();
console.log('First Verdict: ', firstVerdict);

// The murderer is Mrs. Peacock

const secondVerdict = `The murderer is ${murderer}.`;
console.log('Second Verdict: ', secondVerdict);

// murderer is Professor Plum, the murderer from declareMurderer only exists inside the function
```

#### Episode 4

```js
let suspectOne = 'Miss Scarlet';
let suspectTwo = 'Professor Plum';
let suspectThree = 'Mrs. Peacock';

const declareAllSuspects = function() {
  let suspectThree = 'Colonel Mustard';
  return `The suspects are ${suspectOne}, ${suspectTwo}, ${suspectThree}.`;
}

// suspectOne = 'Miss Scarlet', suspectTwo = 'Professor Plum', suspectThree = 'Colonel Mustard'

const suspects = declareAllSuspects();
console.log(suspects);
// let suspectOne = 'Miss Scarlet';
// let suspectTwo = 'Professor Plum';
// let suspectThree = 'Colonel Mustard';
console.log(`Suspect three is ${suspectThree}.`);
// let suspectThree = 'Mrs. Peacock';
```

#### Episode 5

```js
const scenario = {
  murderer: 'Miss Scarlet',
  room: 'Kitchen',
  weapon: 'Candle Stick'
};

const changeWeapon = function(newWeapon) {
  scenario.weapon = newWeapon;
}

const declareWeapon = function() {
  return `The weapon is the ${scenario.weapon}.`;
}

changeWeapon('Revolver');
const verdict = declareWeapon();
console.log(verdict);

// The weapon is the Revolver

```

#### Episode 6

```js
let murderer = 'Colonel Mustard';

const changeMurderer = function() {
  murderer = 'Mr. Green';

  const plotTwist = function() {
    murderer = 'Mrs. White';
  }

  plotTwist();
}

// murderer = Mrs. White is the function result

const declareMurderer = function () {
  return `The murderer is ${murderer}.`;
}

changeMurderer();
const verdict = declareMurderer();
console.log(verdict);
// murderer = Mrs White, because we run changeMurderer
```

#### Episode 7

```js
let murderer = 'Professor Plum';

const changeMurderer = function() {
  murderer = 'Mr. Green';
  // is a global variable
  const plotTwist = function() {
    let murderer = 'Colonel Mustard';
    //murderer won't leave the function
    const unexpectedOutcome = function() {
      murderer = 'Miss Scarlet';
      //murderer won't go further than the previous murderer variable
    }

    unexpectedOutcome();
  }

  plotTwist();
}



const declareMurderer = function() {
  return `The murderer is ${murderer}.`;
}

const another = changeMurderer();
const verdict = declareMurderer();
console.log(verdict);
// The murderer is Mr Green

```

#### Episode 8

```js
const scenario = {
  murderer: 'Mrs. Peacock',
  room: 'Conservatory',
  weapon: 'Lead Pipe'
};

const changeScenario = function() {
  scenario.murderer = 'Mrs. Peacock';
  scenario.room = 'Dining Room';

  const plotTwist = function(room) {
    if (scenario.room === room) {
      scenario.murderer = 'Colonel Mustard';
    }

    const unexpectedOutcome = function(murderer) {
      if (scenario.murderer === murderer) {
        scenario.weapon = 'Candle Stick';
      }
    }

    unexpectedOutcome('Colonel Mustard');
  }

  plotTwist('Dining Room');
}

const declareWeapon = function() {
  return `The weapon is ${scenario.weapon}.`
}

changeScenario();
const verdict = declareWeapon();
console.log(verdict);
// Candle stick
```

#### Episode 9

```js
let murderer = 'Professor Plum';

if (murderer === 'Professor Plum') {
  let murderer = 'Mrs. Peacock';
}

const declareMurderer = function() {
  return `The murderer is ${murderer}.`;
}

const verdict = declareMurderer();
console.log(verdict);

// Professor Plum

```

### Extensions

Make up your own episode!

```js

  const isDuck = function(weapon) {
    let murderer = 'Mr Proper';
    if (weapon.toLowerCase() === 'toilet roll' ) {
      murderer = 'Duck';
    }

    return murderer
  }


  console.log(isDuck('toilet roll'));
  console.log(isDuck('other'));



```
