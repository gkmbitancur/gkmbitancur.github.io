<!DOCTYPE html>
<html lang="en">
<head>
  <meta charset="UTF-8" />
  <meta name="viewport" content="width=device-width, initial-scale=1.0"/>
  <title>Minimalist Manifesto</title>
  <style>
    /* Basic Reset */
    * {
      margin: 0;
      padding: 0;
      box-sizing: border-box;
    }

    /* Fullscreen Black Background */
    body {
      display: flex;
      align-items: center;
      justify-content: center;
      height: 100vh;
      background-color: #000;
      margin: 0;
    }

    /* Centered Text Container */
    #text-container {
      color: #fff;
      font-family: -apple-system, BlinkMacSystemFont, 
                   "Helvetica Neue", Arial, sans-serif;
      font-size: 2rem;
      text-align: center;
      opacity: 0;           /* Start invisible */
      transition: opacity 1s ease; /* Fade transition */
      max-width: 80%;
    }

    /* Fade-in Class: toggled via JS */
    .fade-in {
      opacity: 1;
    }
  </style>
</head>
<body>

  <!-- Container for Manifesto Text -->
  <div id="text-container"></div>

  <script>
    // Array of lines to display
    const lines = [
      "One board.",
      "One manifesto.",
      "One future reimagined.",
      "We are Group 1.",
      "Fiction for the New Millennium.",
      "We mourn what we lose...",
      "We solve what we must...",
      "We conjure what’s yet to come.",
      "Alex: The Critic of Lost Worlds.",
      "Benjamin: The Voice of Urgent Solutions.",
      "Carla: The Visionary of Boundless Tomorrows.",
      "Taylor: The Weaver of Art & Design.",
      "Together, we echo one truth:",
      "Fiction is not just a mirror.",
      "It’s a catalyst.",
      "We write.",
      "We disrupt.",
      "We transform.",
      "This is our call.",
      "This is our vow.",
      "This is our future.",
      "Looping in 3...",
      "2...",
      "1..."
    ];

    // Timing Configuration (milliseconds)
    const fadeDuration = 1000;   // 1 second fade in/out
    const holdDuration = 1500;   // 1.5 seconds fully visible
    const totalDuration = fadeDuration + holdDuration + fadeDuration; 
    // => 1 + 1.5 + 1 = 3.5 seconds per line

    let currentIndex = 0;
    const textContainer = document.getElementById('text-container');

    // Main function to display lines in sequence
    function displayLine(index) {
      // Set the text
      textContainer.textContent = lines[index];
      // Fade in
      textContainer.classList.add('fade-in');

      // After fadeDuration + holdDuration, start fade out
      setTimeout(() => {
        textContainer.classList.remove('fade-in');
      }, fadeDuration + holdDuration);

      // After totalDuration, move to next line
      setTimeout(() => {
        currentIndex++;
        // If we've reached the end, loop back to start
        if (currentIndex >= lines.length) {
          currentIndex = 0;
        }
        displayLine(currentIndex);
      }, totalDuration);
    }

    // Start the cycle
    displayLine(currentIndex);
  </script>
</body>
</html>
