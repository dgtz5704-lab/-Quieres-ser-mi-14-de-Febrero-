# -Quieres-ser-mi-14-de-Febrero-
Muchas gracias 🫂
@import url('https://fonts.googleapis.com/css2?family=Press+Start+2P&display=swap');

* {
  box-sizing: border-box;
  font-family: 'Press Start 2P', cursive;
}

body {
  margin: 0;
  height: 100vh;
  background: linear-gradient(135deg, #ff9a9e, #fad0c4);
  display: flex;
  justify-content: center;
  align-items: center;
  overflow: hidden;
}

.card {
  background: white;
  padding: 30px;
  border-radius: 25px;
  text-align: center;
  box-shadow: 0 20px 40px rgba(0,0,0,0.2);
  animation: pop 1s ease;
  z-index: 2;
}

h1 {
  color: #ff4d6d;
  font-size: 14px;
  margin-bottom: 30px;
}

.buttons button {
  padding: 15px 20px;
  margin: 10px;
  border: none;
  border-radius: 15px;
  font-size: 12px;
  cursor: pointer;
  transition: transform 0.2s;
}

#yes {
  background: #4CAF50;
  color: white;
}

#no {
  background: #ff4d4d;
  color: white;
  position: relative;
}

button:hover {
  transform: scale(1.1);
}

@keyframes pop {
  0% { transform: scale(0); }
  100% { transform: scale(1); }
}

/* Corazones */
.hearts::before {
  content: "💖 💕 💗 💓 💞 💘";
  position: absolute;
  width: 100%;
  height: 100%;
  animation: float 10s linear infinite;
  font-size: 30px;
}

@keyframes float {
  from { transform: translateY(100%); }
  to { transform: translateY(-100%); }
}
