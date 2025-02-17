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
      "Gusto ko red na C2",
      "At yung ayaw ko, green na C2",
      "Kasi iba, kakaiba",
      "Iba yung lasa (nakakapukinangina)",
      "Fiction for the New Millennium.",
      "Ayaw ko yung lasa ng C2 na kulay green",
      "Ayos lang naman yung lasa ng kulay dilaw",
      "Nung tinikman ko yung color green",
      "Nung tinikman ko yung color green",
      "'Yoko na ulitin",
      "Pag bibili ako sa labas",
      "Alam ko na yung sasabihin",
      "Ate, pabili nga po C2 na red",
      "Wala nang red, green na lang",
      "Hindi pwede yan",
      "Ayaw kong uminom nyan",
      "Gusto ko yung red na C2.",
      "Sa akin, sa'kin ibigay",
      "(red) Na C2 sa akin",
      "Sa akin ibigay",
      "(red) Na C2 sa akin",
      "Sa akin ibigay",
      "Thank you",
      "Sir Toffer"
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
