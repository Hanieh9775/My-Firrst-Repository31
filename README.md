<!DOCTYPE html>
<html lang="en">
<head>
<meta charset="UTF-8">
<meta name="viewport" content="width=device-width, initial-scale=1.0">
<title>Gradient Background Generator</title>
<style>
    body {
        margin: 0;
        height: 100vh;
        display: flex;
        justify-content: center;
        align-items: center;
        font-family: "Poppins", sans-serif;
        transition: background 1s ease;
        color: #fff;
    }
    .panel {
        background: rgba(0, 0, 0, 0.4);
        padding: 25px;
        border-radius: 20px;
        text-align: center;
        width: 350px;
        backdrop-filter: blur(10px);
        box-shadow: 0 0 20px #00eaff;
        animation: fade .7s ease;
    }
    h2 {
        margin-bottom: 15px;
        font-size: 24px;
        color: #00eaff;
    }
    button {
        padding: 12px 20px;
        border-radius: 8px;
        border: none;
        background: #00eaff;
        color: #000;
        font-size: 16px;
        cursor: pointer;
        font-weight: bold;
        transition: .3s;
        width: 85%;
    }
    button:hover {
        background: #009bb8;
    }
    .colors {
        margin-top: 20px;
        font-size: 16px;
        background: rgba(255,255,255,0.1);
        padding: 10px;
        border-radius: 10px;
        cursor: pointer;
        transition: .3s;
    }
    .colors:hover {
        background: rgba(255,255,255,0.2);
    }
    @keyframes fade {
        from {opacity: 0; transform: translateY(20px);}
        to   {opacity: 1; transform: translateY(0);}
    }
</style>
</head>
<body>

<div class="panel">
    <h2>Gradient Generator</h2>
    <button onclick="generate()">Generate Gradient</button>

    <div id="colors" class="colors" onclick="copyColors()">
        Click “Generate” to start
    </div>
</div>

<script>
function randomColor() {
    return "#" + Math.floor(Math.random() * 16777215).toString(16).padStart(6, '0');
}

function generate() {
    const c1 = randomColor();
    const c2 = randomColor();
    const angle = Math.floor(Math.random() * 360);

    const gradient = `linear-gradient(${angle}deg, ${c1}, ${c2})`;

    document.body.style.background = gradient;
    document.getElementById("colors").textContent = `${c1}  →  ${c2}`;
}

function copyColors() {
    const text = document.getElementById("colors").textContent;
    navigator.clipboard.writeText(text);
    alert("Copied: " + text);
}
</script>

</body>
</html>
