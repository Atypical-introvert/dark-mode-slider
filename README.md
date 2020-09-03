# dark-mode-slider
/* The switch - the box around the slider */
body {
    background-color: white;
  }
  
  .switch {
    position: relative;
    display: inline-block;
    width: 60px;
    height: 34px;
  }
  
  /*   // Hide checkbox
   */
  .switch input {
    opacity: 0;
    width: 0;
    height: 0;
  }
  
  /*   // The slider
     */
  .slider {
    position: absolute;
    cursor: pointer;
    top: 0;
    left: 0;
    right: 0;
    bottom: 0;
    background-color: lightblue;
    transition: 0.4s ease-in-out;
  }
  
  /*   
    // Design of slider for light mode
   */
  .slider:before {
    position: absolute;
    content: "";
    height: 23px;
    width: 23px;
    left: 6px;
    bottom: 6px;
    background-color: yellow;
    box-shadow: 0px 0px 5px 4px #ffd900;
    transition: 0.4s;
  }
  
  /*   // When theme is dark, background is dark */
  .theme-dark .slider {
    background-color: #3a2864;
  }
  
  /*    // If theme is dark, but slider is to the left, move it to the right and turn it into a moon
   */
  .theme-dark .slider:before {
    transform: translateX(26px);
    height: 3px;
    width: 3px;
    background-color: lightgrey;
    bottom: 15px;
    left: 10px;
    box-shadow: 10px -7px 0px 1px lightgrey, -4px -8px 0px 0px lightgrey, 6px 6px 0px 1px lightgrey, 5px -1px 5px 13px white, 5px -1px 0px 12px white;
  }
  
  /* Rounded sliders */
  .slider.round {
    border-radius: 34px;
  }
  
  .slider.round:before {
    border-radius: 50%;
  }
  
  .theme-dark body {
    background-color: black;
  }
  
  .theme-light body {
    background-color: aliceblue;
  }
  
function setTheme(themeName) {
    localStorage.setItem("theme", themeName);
    document.documentElement.className = themeName;
  }
  
  // When toggle is switched, check local storage for the currently stored theme, and switch it to the opposite
  
  function toggleTheme() {
    if (localStorage.getItem("theme") === "theme-dark") {
      setTheme("theme-light");
    } else {
      setTheme("theme-dark");
    }
  }
  
  // Invoke function on loading page - check storage if a previous theme was stored, if not, load default (light) theme
  
  (function () {
    if (localStorage.getItem("theme") === "theme-dark") {
      setTheme("theme-dark");
    } else {
      setTheme("theme-light");
    }
  })();
<!DOCTYPE html>
<head>
    <title>Dark Mode by Anuj</title>
    <link rel="stylesheet" href="style.css">
    <script src="darkmode.js"></script>
</head>
<body>
    <!--for the dark mode slider-->
<label id ="switch" class="switch">
    <input type="checkbox" onchange="toggleTheme()" id="slider">
    <span class="slider round"></span>
</label>
</body>
