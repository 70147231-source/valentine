<!DOCTYPE html>
<html lang="en">
<head>
<meta charset="UTF-8">
<title>💖 Valentine 💖</title>

<style>
body {
    margin: 0;
    height: 100vh;
    overflow: hidden;
    display: flex;
    flex-direction: column;
    justify-content: center;
    align-items: center;
    background: linear-gradient(135deg, #ffdde1, #ee9ca7);
    font-family: 'Segoe UI', sans-serif;
}

h1 {
    color: #b30047;
    font-size: 2.5em;
    margin-bottom: 40px;
    text-align: center;
}

button {
    padding: 12px 26px;
    font-size: 18px;
    border: none;
    border-radius: 30px;
    cursor: pointer;
    position: absolute;
}

#yes {
    background: #ff4d6d;
    color: white;
    left: 40%;
    top: 60%;
}

#no {
    background: #f1f1f1;
    color: #333;
    left: 55%;
    top: 60%;
}

/* Floating hearts */
.heart {
    position: absolute;
    color: rgba(255, 0, 100, 0.6);
    font-size: 20px;
    animation: float 6s linear infinite;
}

@keyframes float {
    0% { transform: translateY(0); opacity: 1; }
    100% { transform: translateY(-800px); opacity: 0; }
}
</style>
</head>

<body>

<h1>Will you be my Valentine? 💕</h1>

<button id="yes">YES ❤️</button>
<button id="no">NO 💔</button>

<!-- Romantic music -->
<audio id="music" loop>
    <source src="https://cdn.pixabay.com/download/audio/2022/03/15/audio_78c3d61b6b.mp3" type="audio/mpeg">
</audio>

<script>
const noBtn = document.getElementById("no");
const yesBtn = document.getElementById("yes");
const music = document.getElementById("music");

// Move "NO" button randomly
noBtn.addEventListener("mouseover", () => {
    const x = Math.random() * (window.innerWidth - 120);
    const y = Math.random() * (window.innerHeight - 120);
    noBtn.style.left = x + "px";
    noBtn.style.top = y + "px";
});

// Play music and show Valentine message on "YES" click
yesBtn.addEventListener("click", () => {
    music.play(); // start music
    document.body.innerHTML = `
        <h1>Yayyyy 💖🥰<br>You are my Valentine ❤️</h1>
        <p style="font-size:22px;color:#800040;">Made with love 💕</p>
    `;

    // Keep floating hearts going
    setInterval(() => {
        const heart = document.createElement("div");
        heart.classList.add("heart");
        heart.innerHTML = "❤️";
        heart.style.left = Math.random() * window.innerWidth + "px";
        heart.style.fontSize = Math.random() * 20 + 15 + "px";
        document.body.appendChild(heart);

        setTimeout(() => heart.remove(), 6000);
    }, 300);
});

// Optional: start music on any first click anywhere
document.body.addEventListener("click", () => {
    music.play();
}, { once: true });
</script>

</body>
</html>
