 <!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Birthday Surprise - Sahanaz Parvin</title>
    <link href="https://fonts.googleapis.com/css2?family=Dancing+Script:wght@700&family=Poppins:wght@300&display=swap" rel="stylesheet">
    <style>
        :root { --pink: #ffb7c5; --deep-pink: #d02090; }
        * { margin: 0; padding: 0; box-sizing: border-box; }
        
        body { height: 100vh; display: flex; justify-content: center; align-items: center; background: #000; font-family: 'Poppins', sans-serif; overflow: hidden; }

        /* Animated Sakura Forest Background */
        .forest-bg { position: fixed; inset: 0; background: url('https://images.unsplash.com/photo-1522383225653-ed111181a951?q=80&w=2070&auto=format&fit=crop') no-repeat center center; background-size: cover; z-index: -2; filter: brightness(0.7); }

        /* Password Entrance */
        #lock-screen { position: fixed; inset: 0; background: rgba(255, 183, 197, 0.98); z-index: 100; display: flex; flex-direction: column; justify-content: center; align-items: center; transition: 1s; }
        #lock-screen.hidden { opacity: 0; pointer-events: none; }
        .pw-box { padding: 30px; background: white; border-radius: 20px; box-shadow: 0 10px 30px rgba(0,0,0,0.1); text-align: center; }
        input { padding: 12px; border: 2px solid var(--pink); border-radius: 8px; margin: 15px 0; outline: none; text-align: center; width: 200px; }
        button { padding: 10px 25px; background: var(--deep-pink); color: white; border: none; border-radius: 8px; cursor: pointer; font-weight: bold; }

        /* 3D Flip Book */
        .book { width: 320px; height: 450px; position: relative; perspective: 1500px; z-index: 5; }
        .page { position: absolute; width: 100%; height: 100%; top: 0; left: 0; background: rgba(255, 240, 245, 0.95); border-radius: 0 15px 15px 0; transform-origin: left; transform-style: preserve-3d; transition: transform 1.2s cubic-bezier(0.645, 0.045, 0.355, 1); box-shadow: inset 3px 0 10px rgba(0,0,0,0.1), 5px 5px 20px rgba(0,0,0,0.3); display: flex; flex-direction: column; justify-content: center; align-items: center; padding: 25px; text-align: center; backface-visibility: hidden; cursor: pointer; border-left: 1px solid rgba(0,0,0,0.1); }
        
        .flipped { transform: rotateY(-180deg); }
        .cover { background: var(--deep-pink); color: white; z-index: 10; border-left: none; }
        .cover h1 { color: white; font-size: 2.2rem; font-family: 'Dancing Script', cursive; }

        /* Sister's Photo Frame */
        .photo-frame { width: 220px; height: 220px; border: 8px solid white; border-radius: 5px; overflow: hidden; margin-bottom: 15px; box-shadow: 0 5px 15px rgba(0,0,0,0.2); background: #eee; }
        .photo-frame img { width: 100%; height: 100%; object-fit: cover; }

        h1 { font-family: 'Dancing Script', cursive; font-size: 1.8rem; color: var(--deep-pink); }
        p { font-size: 0.9rem; line-height: 1.6; color: #444; margin-top: 10px; font-weight: 500; }

        /* Floating Petals - Highest Z-Index to stay in front */
        .petal { position: absolute; background-color: var(--pink); border-radius: 150% 0 150% 0; opacity: 0.8; pointer-events: none; z-index: 20; animation: fall linear infinite; }
        @keyframes fall { 0% { transform: translateY(-10vh) rotate(0deg); } 100% { transform: translateY(110vh) rotate(360deg) translateX(50px); } }
    </style>
</head>
<body>

    <div id="lock-screen">
        <div class="pw-box">
            <h3>Enter Password</h3>
            <p>Hint: Key will be provided by admin on 5th March</p>
            <input type="password" id="pw" placeholder="password...">
            <br>
            <button onclick="checkPw()">Enter Surprise</button>
        </div>
    </div>

    <div class="forest-bg"></div>

    <div class="book">
        <div class="page" style="z-index: 1;">
            <div class="photo-frame">
         <img src="Screenshot_2026-03-02-10-33-03-52_40deb401b9ffe8e1df2f1cc5ba480b12.jpg" alt="Shahnaz Parvin">
         
         
            </div>
            <h1>Happy Birthday!</h1>
            <p>To my sister. ❤️</p>
        </div>

        <div class="page" id="p3" style="z-index: 2;" onclick="flip('p3')">
            <h1>Always With You</h1>
            <p>Thank you for your love and support.  🌸</p>
        </div>

        <div class="page" id="p2" style="z-index: 3;" onclick="flip('p2')">
            <h1>A Special Wish</h1>
            <p>May your day be filled with as much joy as you give to others. 🌷</p>
        </div>

        <div class="page cover" id="p1" style="z-index: 4;" onclick="flip('p1')">
            <h1>Happy Birthday<br>Shahnaz Parvin</h1>
            <p style="color: white; margin-top: 20px;">(Tap to open)</p>
        </div>
    </div>

    <script>
        function checkPw() {
            const pw = document.getElementById('pw').value;
            if(pw.toLowerCase() === 'shahnaz') {
                document.getElementById('lock-screen').classList.add('hidden');
            } else {
                alert("Wrong password!");
            }
        }

        function flip(id) {
            document.getElementById(id).classList.add('flipped');
        }

        function createPetal() {
            const petal = document.createElement('div');
            petal.classList.add('petal');
            const size = Math.random() * 8 + 5 + 'px';
            petal.style.width = size; petal.style.height = size;
            petal.style.left = Math.random() * 100 + 'vw';
            petal.style.animationDuration = Math.random() * 3 + 3 + 's';
            document.body.appendChild(petal);
            setTimeout(() => petal.remove(), 6000);
        }
        setInterval(createPetal, 150);
    </script>
</body>
</html>
