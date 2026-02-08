<!DOCTYPE html>
<html lang="en">
<head>
<meta charset="UTF-8">
<title>Valentine Website</title>

<style>
    body {
        margin: 0;
        font-family: 'Comic Sans MS', cursive;
        height: 100vh;
        text-align: center;
        background: radial-gradient(circle at top, #ff9a9e, #fad0c4, #fbc2eb);
        overflow: hidden;
    }

    .page {
        display: none;
        padding-top: 80px;
    }

    .active {
        display: block;
    }

    h1 {
        color: white;
        text-shadow: 2px 2px 6px #000;
    }

    button {
        padding: 12px 28px;
        font-size: 18px;
        border: none;
        border-radius: 25px;
        cursor: pointer;
        margin: 10px;
    }

    .green { background: #2ecc71; color: white; }
    .red { background: #ff4d6d; color: white; }

    .gap { margin-left: 96px; } /* ~12 spaces */

    /* Colour blast */
    .blast {
        position: absolute;
        width: 14px;
        height: 14px;
        border-radius: 50%;
        animation: blast 1.2s linear forwards;
    }

    @keyframes blast {
        from { transform: scale(1); opacity: 1; }
        to { transform: scale(6); opacity: 0; }
    }
</style>
</head>

<body>

<!-- PAGE 1 -->
<div class="page active" id="p1">
    <h1>Say Hi</h1>
    <br>
    <button class="green" onclick="go('p2')">Hi</button>
    <span class="gap"></span>
    <button class="red" onclick="go('p6')">Bye</button>
</div>

<!-- Hi -> Valentine -->
<div class="page" id="p2">
    <h1>Will you be my Valentine?</h1>
    <button class="green" onclick="go('p3')">Yes</button>
    <button class="red" onclick="go('p4')">No</button>
</div>

<!-- Yes -> Engaged -->
<div class="page" id="p3">
    <h1>💍 Let's get engaged 💍</h1>
    <button class="green" onclick="go('p9')">Yes</button>
    <button class="red" onclick="go('p9')">No</button>
</div>

<!-- No -> Then Valentine -->
<div class="page" id="p4">
    <h1>Then I will be your Valentine</h1>
    <button class="green" onclick="blast()">Yes</button>
    <button class="red" onclick="blast()">Yes</button>
</div>

<!-- Bye -> Date -->
<div class="page" id="p6">
    <h1>Will you come for a date with me?</h1>
    <button class="green" onclick="go('p7')">Yes</button>
    <button class="red" onclick="go('p7')">No</button>
</div>

<!-- Married page -->
<div class="page" id="p7">
    <h1>💖 Let's get married 💖</h1>
    <button class="green" onclick="blast()">Yes</button>
    <button class="red" onclick="blast()">Yes</button>
</div>

<!-- Engaged -> Married -->
<div class="page" id="p9">
    <h1>💖 Let's get married 💖</h1>
    <button class="green" onclick="blast()">Yes</button>
    <button class="red" onclick="blast()">Yes</button>
</div>

<script>
function go(id) {
    document.querySelectorAll('.page').forEach(p => p.classList.remove('active'));
    document.getElementById(id).classList.add('active');
}

function blast() {
    for (let i = 0; i < 90; i++) {
        const d = document.createElement('div');
        d.className = 'blast';
        d.style.backgroundColor = `hsl(${Math.random()*360},100%,60%)`;
        d.style.left = Math.random() * innerWidth + 'px';
        d.style.top = Math.random() * innerHeight + 'px';
        document.body.appendChild(d);
        setTimeout(() => d.remove(), 1200);
    }
}
</script>

</body>
</html>
