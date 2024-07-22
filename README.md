# Facebook-scripts

The automated script to poke people on Facebook

## Code to poke everyone on the screen

```js
// Find all the poke buttons on the page
const pokeButtons = document.querySelectorAll('div[aria-label="Poke"][role="button"]');

// Function to click each poke button
function pokeEveryone() {
  pokeButtons.forEach(button => {
    button.click();
  });
}

// Execute the function
pokeEveryone();
```

## Code to scroll and keep poking everyone on your contact list

```js
// Function to scroll to the bottom of the page
function scrollToEnd() {
  return new Promise((resolve) => {
    let totalHeight = 0;
    let distance = 100;

    let timer = setInterval(() => {
      let scrollHeight = document.body.scrollHeight;
      window.scrollBy(0, distance);
      totalHeight += distance;

      if (totalHeight >= scrollHeight) {
        clearInterval(timer);
        resolve();
      }
    }, 100);
  });
}

// Function to click each poke button
function pokeEveryone() {
  const pokeButtons = document.querySelectorAll('div[aria-label="Poke"][role="button"]');
  pokeButtons.forEach(button => {
    button.click();
  });
}

// Execute the scrolling and then poke everyone
async function scrollAndPoke() {
  await scrollToEnd();
  pokeEveryone();
}

// Start the process
scrollAndPoke();

```
