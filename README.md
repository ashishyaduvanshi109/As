<!DOCTYPE html><html lang="en">
<head>
  <meta charset="UTF-8">
  <title>Ashish Mac OS Clone</title>
  <style>
    * { margin: 0; padding: 0; box-sizing: border-box; }
    html, body {
      height: 100%;
      font-family: 'Segoe UI', sans-serif;
      background: black;
      overflow: hidden;
    }
    #boot, #login, #desktop {
      position: absolute;
      width: 100%; height: 100%;
      display: none;
    }
    #boot {
      background: black;
      color: white;
      display: flex;
      flex-direction: column;
      justify-content: center;
      align-items: center;
      animation: fadein 2s ease-in-out;
    }
    @keyframes fadein {
      from {opacity: 0;}
      to {opacity: 1;}
    }
    #boot img {
      width: 100px;
      animation: pulse 2s infinite alternate;
    }
    @keyframes pulse {
      from {opacity: 0.3;}
      to {opacity: 1;}
    }
    #login {
      background: linear-gradient(to bottom right, #1e1e1e, #2e2e2e);
      display: flex;
      justify-content: center;
      align-items: center;
      flex-direction: column;
      color: white;
    }
    #login input {
      padding: 10px;
      font-size: 16px;
      border: none;
      margin: 10px;
    }
    #login button {
      padding: 10px 20px;
      font-size: 16px;
      background: #0078d7;
      color: white;
      border: none;
      cursor: pointer;
    }
    #desktop {
      background: url('https://wallpapercave.com/wp/wp2757874.jpg') no-repeat center center/cover;
    }
    .dock {
      position: absolute;
      bottom: 10px;
      left: 50%;
      transform: translateX(-50%);
      background: rgba(0,0,0,0.5);
      border-radius: 20px;
      padding: 10px;
      display: flex;
      gap: 10px;
    }
    .dock img {
      width: 50px;
      height: 50px;
      cursor: pointer;
      transition: transform 0.2s;
    }
    .dock img:hover {
      transform: scale(1.2);
    }
    .window {
      position: absolute;
      top: 100px;
      left: 100px;
      width: 500px;
      height: 300px;
      background: white;
      border-radius: 8px;
      box-shadow: 0 0 10px black;
      overflow: hidden;
    }
    .window-header {
      background: #444;
      color: white;
      padding: 5px;
      display: flex;
      justify-content: space-between;
    }
    .window-body {
      padding: 10px;
      height: calc(100% - 30px);
    }
  </style>
</head>
<body><div id="boot">
  <img src="https://upload.wikimedia.org/wikipedia/commons/f/fa/Apple_logo_black.svg">
  <p>Booting Ashish Mac OS...</p>
</div><div id="login">
  <h2>Welcome to Ashish Mac OS</h2>
  <input type="password" id="password" placeholder="Enter password">
  <button onclick="login()">Login</button>
</div><div id="desktop">
  <div class="dock">
    <img src="https://icons.iconarchive.com/icons/custom-icon-design/flatastic-1/512/notepad-icon.png" onclick="openApp('notepad')">
    <img src="https://icons.iconarchive.com/icons/google/chrome/512/Google-Chrome-icon.png" onclick="openApp('browser')">
    <img src="https://icons.iconarchive.com/icons/paomedia/small-n-flat/1024/calculator-icon.png" onclick="openApp('calc')">
    <img src="https://icons.iconarchive.com/icons/graphicloads/100-flat/256/picture-icon.png" onclick="openApp('media')">
  </div>
</div><script>
  document.getElementById("boot").style.display = "flex";
  setTimeout(() => {
    document.getElementById("boot").style.display = "none";
    document.getElementById("login").style.display = "flex";
  }, 2000);

  function login() {
    const pass = document.getElementById("password").value;
    if (pass === "1234") {
      document.getElementById("login").style.display = "none";
      document.getElementById("desktop").style.display = "block";
    } else {
      alert("Wrong password");
    }
  }

  function openApp(app) {
    const win = document.createElement("div");
    win.className = "window";
    let content = "";
    if (app === "notepad") {
      content = '<textarea style="width:100%; height:100%; border:none;">Welcome to Notepad!</textarea>';} else if (app === "browser") {
  window.open("https://google.com", "_blank"); return;
} else if (app === "calc") {
  content = '<iframe src="https://www.online-calculator.com/full-screen-calculator/" style="width:100%; height:100%; border:none;"></iframe>';
} else if (app === "media") {
  content = '<video src="https://www.w3schools.com/html/mov_bbb.mp4" controls autoplay style="width:100%; height:100%;"></video>';
}
win.innerHTML = `<div class='window-header'><span>${app.toUpperCase()}</span><button onclick="this.closest('.window').remove()">X</button></div><div class='window-body'>${content}</div>`;
document.body.appendChild(win);

} </script>

</body>
</html> As
