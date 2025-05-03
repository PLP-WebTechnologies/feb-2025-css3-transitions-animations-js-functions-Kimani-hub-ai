# CSS3 Transitions, Animations, and Advanced JavaScript Functions

## Objectives

Create smooth CSS transitions and animations.
Use JavaScript functions for dynamic behavior.
Implement local storage for data persistence.

## Instructions
Add CSS animations to elements like buttons or images.

>[!NOTE]
> - Write a JavaScript function that:
> - Stores and retrieves user preferences using localStorage.
> - Implements an animation triggered by user actions.

## Tasks

Create a CSS animation.
Store data in localStorage.
Apply JavaScript to trigger animations.

Happy Coding! 💻✨

<!-- index.html -->
<!DOCTYPE html>
<html lang="en">
<head>
  <meta charset="UTF-8">
  <meta name="viewport" content="width=device-width, initial-scale=1.0">
  <title>Animation Toggle</title>
  <link rel="stylesheet" href="style.css">
</head>
<body>
  <h1>Toggle Animation Example</h1>
  <div class="box"></div>
  <button id="toggleBtn">Toggle Animation</button>

  <script src="script.js"></script>
</body>
</html>
/* style.css */
@keyframes boxAnimation {
  0% {
    transform: scale(1);
    background-color: blue;
  }
  50% {
    transform: scale(1.5);
    background-color: green;
  }
  100% {
    transform: scale(1);
    background-color: blue;
  }
}

.box {
  width: 200px;
  height: 200px;
  background-color: blue;
  transition: transform 1s, background-color 1s;
}

/* Active state triggered by the animation */
.animate {
  animation: boxAnimation 2s infinite;
}
// script.js

// Function to store user preference
function storePreference(isAnimated) {
  // Store the preference in localStorage
  localStorage.setItem("animationEnabled", JSON.stringify(isAnimated));
}

// Function to retrieve user preference
function getPreference() {
  const preference = localStorage.getItem("animationEnabled");
  return preference ? JSON.parse(preference) : true; // Default is true (animation enabled)
}

// Function to toggle the animation on the box
function toggleAnimation() {
  const box = document.querySelector(".box");
  const isAnimated = getPreference(); // Retrieve the current preference

  // Toggle the animation class based on the stored preference
  if (isAnimated) {
    box.classList.add("animate");
  } else {
    box.classList.remove("animate");
  }

  // Store the new preference after toggling
  storePreference(!isAnimated);
}

// Event listener to trigger the animation when the button is clicked
document.querySelector("#toggleBtn").addEventListener("click", toggleAnimation);

// Apply the animation on page load based on user preference
document.addEventListener("DOMContentLoaded", () => {
  const box = document.querySelector(".box");
  const isAnimated = getPreference();
  if (isAnimated) {
    box.classList.add("animate");
  }
});

