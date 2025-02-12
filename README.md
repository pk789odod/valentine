<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Do You Love Me?</title>
    <link href="https://fonts.googleapis.com/css2?family=Pacifico&display=swap" rel="stylesheet">
    <style>
        body {
            margin: 0;
            padding: 0;
            background: #ff3860;
            display: flex;
            justify-content: center;
            align-items: center;
            min-height: 100vh;
            font-family: 'Pacifico', cursive;
            overflow: hidden;
            position: relative;
        }

        .container {
            text-align: center;
            animation: fadeIn 1s ease-in;
        }

        @keyframes fadeIn {
            from { opacity: 0; transform: translateY(20px); }
            to { opacity: 1; transform: translateY(0); }
        }

        h1 {
            color: #fff;
            font-size: 3em;
            text-shadow: 2px 2px 4px rgba(0,0,0,0.3);
            margin-bottom: 30px;
        }

        .buttons {
            display: flex;
            gap: 20px;
            justify-content: center;
            flex-wrap: wrap;
        }

        .yes-btn {
            background: #4CAF50;
            color: white;
            padding: 20px 50px;
            font-size: 1.8em;
            border: none;
            border-radius: 30px;
            cursor: pointer;
            transition: all 0.3s ease;
            box-shadow: 0 4px 15px rgba(0,0,0,0.2);
        }

        .little-bit-btn {
            background: #FF69B4;
            color: white;
            padding: 20px 50px;
            font-size: 1.8em;
            border: none;
            border-radius: 30px;
            cursor: pointer;
            transition: all 0.3s ease;
            box-shadow: 0 4px 15px rgba(0,0,0,0.2);
        }

        .yes-btn:hover {
            transform: scale(1.1) rotate(3deg);
            background: #45a049;
        }

        .little-bit-btn:hover {
            animation: shake 0.5s ease infinite;
            background: #ff1493;
        }

        @keyframes shake {
            0%, 100% { transform: translateX(0); }
            25% { transform: translateX(10px); }
            75% { transform: translateX(-10px); }
        }

        .celebration {
            position: fixed;
            top: 0;
            left: 0;
            width: 100%;
            height: 100%;
            background: rgba(255, 56, 96, 0.95);
            display: none;
            justify-content: center;
            align-items: center;
            z-index: 1000;
            animation: zoomIn 0.5s ease;
        }

        @keyframes zoomIn {
            from { transform: scale(0); }
            to { transform: scale(1); }
        }

        .hearts {
            position: fixed;
            width: 100%;
            height: 100%;
            pointer-events: none;
        }

        .heart {
            position: absolute;
            animation: float 3s linear infinite;
            opacity: 0;
            font-size: 24px;
        }

        @keyframes float {
            0% { transform: translateY(100vh); opacity: 0; }
            50% { opacity: 1; }
            100% { transform: translateY(-100vh); opacity: 0; }
        }
    </style>
</head>
<body>
    <div class="hearts" id="heartsContainer"></div>
    <div class="container">
        <h1>💖 Do You Love Me? 💖</h1>
        <div class="buttons">
            <button class="yes-btn" onclick="showLove()">Yes! 😍</button>
            <button class="little-bit-btn" onclick="handleLittleBit()">A little bit? 🥺</button>
        </div>
    </div>

    <div class="celebration" id="celebration">
        <div style="text-align: center; color: white;">
            <h1 style="font-size: 4em;">🎉 I KNEW IT! 💝</h1>
            <p style="font-size: 2em;">I knew it my kuchu, come here 🤗🤗</p>
            <div style="font-size: 3em; margin-top: 20px;">
                ❤️🤗💞🔥😘
            </div>
        </div>
    </div>

    <script>
        // Floating hearts initialization
        function createHearts() {
            const heartsContainer = document.getElementById('heartsContainer');
            for(let i = 0; i < 15; i++) {
                const heart = document.createElement('div');
                heart.className = 'heart';
                heart.innerHTML = '💖';
                heart.style.cssText = `
                    left: ${Math.random() * 100}%;
                    animation-delay: ${Math.random() * 2}s;
                `;
                heartsContainer.appendChild(heart);
            }
        }
        createHearts();

        // "A little bit" button logic
        let clickCount = 0;
        const littleBitMessages = [
            "Are you sure?",
            "Maybe a bit more? 😊",
            "How about medium love?",
            "Pretty please? 🥺",
            "I'll wait... ⏳",
            "My heart says more! 💓",
            "Let's negotiate! 🤝",
            "Cookies? 🍪",
            "Final offer: Lots? 💖",
            "Any amount! 😍"
        ];

        function handleLittleBit() {
            const btn = document.querySelector('.little-bit-btn');
            // Cycle through messages
            btn.textContent = littleBitMessages[clickCount % littleBitMessages.length];
            // Add shake animation
            btn.style.animation = 'shake 0.5s ease';
            
            // Create new heart
            const heart = document.createElement('div');
            heart.className = 'heart';
            heart.innerHTML = '💖';
            heart.style.cssText = `
                left: ${Math.random() * 80 + 10}%;
                animation-duration: ${Math.random() * 2 + 2}s;
            `;
            document.getElementById('heartsContainer').appendChild(heart);
            
            clickCount++;
            
            // Increase Yes button size
            const yesBtn = document.querySelector('.yes-btn');
            const currentSize = parseFloat(window.getComputedStyle(yesBtn).fontSize);
            yesBtn.style.fontSize = `${currentSize * 1.1}px`;
        }

        // Yes button handler
        function showLove() {
            const celebration = document.getElementById('celebration');
            celebration.style.display = 'flex';
            
            // Add celebration hearts
            for(let i = 0; i < 50; i++) {
                const heart = document.createElement('div');
                heart.className = 'heart';
                heart.innerHTML = ['💖', '💝', '💘', '💕', '💞'][Math.floor(Math.random() * 5)];
                heart.style.cssText = `
                    left: ${Math.random() * 100}%;
                    animation-delay: ${Math.random()}s;
                `;
                document.getElementById('heartsContainer').appendChild(heart);
            }
            
            // Add hugging emoji animation
            const hugEmoji = document.createElement('div');
            hugEmoji.innerHTML = '🤗🤗';
            hugEmoji.style.cssText = `
                position: fixed;
                top: 50%;
                left: 50%;
                transform: translate(-50%, -50%);
                font-size: 8em;
                animation: zoomIn 0.5s ease-in-out;
                z-index: 1001;
            `;
            document.body.appendChild(hugEmoji);
        }
    </script>
</body>
</html>
