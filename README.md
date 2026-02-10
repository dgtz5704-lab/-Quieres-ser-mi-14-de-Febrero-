¿Quieres ser mi San Valentín?
14 de febrero 2026
<!DOCTYPE html>
<html lang="es">
<head>
<meta charset="UTF-8">
<title>Para Ti ❤️</title>
<meta name="viewport" content="width=device-width, initial-scale=1.0">

<style>
/* Reset and Body Styles */
body {
    margin: 0;
    height: 100vh;
    background: linear-gradient(135deg, #ff5f8d, #ffb3c6);
    display: flex;
    align-items: center;
    justify-content: center;
    font-family: 'Arial', sans-serif;
    overflow: hidden;
    color: white;
}

/* Glassmorphism Card */
.card {
    background: rgba(255,255,255,0.18);
    backdrop-filter: blur(12px);
    border-radius: 30px;
    padding: 30px;
    max-width: 340px;
    text-align: center;
    animation: aparecer 1.2s ease;
    box-shadow: 0 20px 40px rgba(0,0,0,.25);
    z-index: 2;
    position: relative; /* Ensures content stays above background hearts */
}

h1 { font-size: 22px; }
p { font-size: 15px; opacity: .95; }

/* Buttons */
.botones { margin-top: 25px; }

button {
    border: none;
    border-radius: 30px;
    padding: 14px 26px;
    font-size: 16px;
    cursor: pointer;
    transition: transform .2s;
}
button:hover { transform: scale(1.1); }

#si { background: #ff2e63; color: white; }
#no { background: white; color: #ff2e63; position: absolute; } 
/* Note: 'absolute' position is crucial for the moving effect */

/* Hidden Elements (Success Message) */
.mensaje {
    margin-top: 20px;
    font-size: 17px;
    display: none;
    animation: pop 0.8s ease;
}

.share { margin-top: 15px; display: none; }
.share button { background: white; color: #ff2e63; font-size: 13px; }

/* Animations */
@keyframes aparecer {
    from {opacity:0; transform: scale(0.85);}
    to {opacity:1; transform: scale(1);}
}

@keyframes pop {
    0% {transform: scale(0);}
    80% {transform: scale(1.1);}
    100% {transform: scale(1);}
}

/* Floating Hearts Background */
.corazon {
    position: absolute;
    font-size: 22px;
    animation: flotar linear infinite;
    opacity: 0.7;
    z-index: 1; /* Behind the card */
}

@keyframes flotar {
    from {transform: translateY(110vh);}
    to {transform: translateY(-10vh);}
}
</style>
</head>

<body>

<div class="card">
    <h1 id="titulo"></h1>
    <p id="texto"></p>

    <div class="botones">
        <button id="si">Sí 💖</button>
        <button id="no">No 🙈</button>
    </div>

    <div class="mensaje" id="mensaje"></div>

    <div class="share" id="share">
        <button onclick="copiarLink()">📲 Compartir link</button>
    </div>
</div>

<script>
// 1. Setup Names from URL
const params = new URLSearchParams(window.location.search);
const from = params.get("from") || "Alguien especial";
const to = params.get("to") || "Tú";

document.getElementById("titulo").innerText = `${to}, ¿quieres ser mi Valentine? 💘`;
document.getElementById("texto").innerText = `Con todo mi cariño, ${from}`;

// 2. "YES" Button Logic
document.getElementById("si").onclick = () => {
    document.getElementById("mensaje").style.display = "block";
    document.getElementById("mensaje").innerHTML =
    `💖 ${from} dice:<br><br>
     Eres una persona increíble y haces mi mundo más bonito.<br><br>
     💘 Feliz 14 de febrero 💘`;
    document.getElementById("share").style.display = "block";
    
    // Hide buttons after saying yes to clean up UI
    document.querySelector('.botones').style.display = 'none';
};

// 3. "NO" Button Logic (The Runaway Button)
const no = document.getElementById("no");

function moverNo() {
    const x = Math.random() * (window.innerWidth - 100);
    const y = Math.random() * (window.innerHeight - 50);
    no.style.left = x + "px";
    no.style.top = y + "px";
}

no.addEventListener("mouseover", moverNo);
no.addEventListener("touchstart", moverNo); // For mobile support

// 4. Background Hearts Generator
setInterval(() => {
    const c = document.createElement("div");
    c.className = "corazon";
    c.innerText = Math.random() > 0.5 ? "❤️" : "💖";
    c.style.left = Math.random() * 100 + "vw";
    c.style.fontSize = (Math.random() * 12 + 16) + "px";
    c.style.animationDuration = (Math.random() * 3 + 5) + "s";
    document.body.appendChild(c);
    setTimeout(() => c.remove(), 7000); // Cleanup to prevent memory leaks
}, 250);

// 5. Copy Link Feature
function copiarLink() {
    navigator.clipboard.writeText(window.location.href);
    alert("💌 Link copiado para compartir");
}
</script>

</body>
</html>
