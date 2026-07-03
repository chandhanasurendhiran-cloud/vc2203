<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>For Venkat</title>
    <style>
        /* Reset and background setup */
        body {
            margin: 0;
            padding: 0;
            background: linear-gradient(135deg, #ffe6e6, #ffb3b3);
            height: 100vh;
            overflow: hidden;
            display: flex;
            justify-content: center;
            align-items: center;
            font-family: 'Segoe UI', Tahoma, Geneva, Verdana, sans-serif;
        }

        /* Central message box styling */
        .message-container {
            text-align: center;
            background: rgba(255, 255, 255, 0.85);
            padding: 40px 60px;
            border-radius: 20px;
            box-shadow: 0 10px 30px rgba(0, 0, 0, 0.1);
            backdrop-filter: blur(8px);
            z-index: 10;
            border: 2px solid #ff4d6d;
            animation: pulse 2s infinite alternate;
        }

        h1 {
            color: #ff4d6d;
            font-size: 3rem;
            margin: 0;
            text-shadow: 1px 1px 2px rgba(0, 0, 0, 0.1);
        }

        @keyframes pulse {
            0% { transform: scale(1); }
            100% { transform: scale(1.03); }
        }

        /* Falling elements styling */
        .falling-element {
            position: absolute;
            top: -50px;
            user-select: none;
            pointer-events: none;
            animation: fall linear forwards;
        }

        @keyframes fall {
            0% {
                top: -50px;
                transform: translateX(0) rotate(0deg);
                opacity: 1;
            }
            100% {
                top: 105vh;
                transform: translateX(100px) rotate(360deg);
                opacity: 0.3;
            }
        }
    </style>
</head>
<body>

    <div class="message-container">
        <h1>chandu loves u more venkat</h1>
    </div>

    <script>
        // Arrays holding the emojis and colors to use
        const hearts = ['❤️', '💖', '💝', '💕', '💗'];
        const balloons = ['🎈', '🎈', '🎈']; // Kept simple, you can add more shapes

        function createFallingElement() {
            const element = document.createElement('div');
            element.classList.add('falling-element');
            
            // Randomly choose between a heart and a balloon
            const isHeart = Math.random() > 0.5;
            if (isHeart) {
                element.innerText = hearts[Math.floor(Math.random() * hearts.length)];
                element.style.fontSize = Math.random() * 20 + 20 + 'px'; // 20px to 40px
            } else {
                element.innerText = balloons[Math.floor(Math.random() * balloons.length)];
                element.style.fontSize = Math.random() * 30 + 30 + 'px'; // 30px to 60px
            }

            // Random horizontal starting position across the screen width
            element.style.left = Math.random() * 100 + 'vw';
            
            // Random speed for falling (between 4 and 8 seconds)
            const duration = Math.random() * 4 + 4;
            element.style.animationDuration = duration + 's';
            
            // Slight random horizontal sway delay
            element.style.animationDelay = Math.random() * 2 + 's';

            document.body.appendChild(element);

            // Remove the element from the DOM after its animation finishes
            setTimeout(() => {
                element.remove();
            }, (duration + 2) * 1000);
        }

        // Generate a new falling item every 300 milliseconds
        setInterval(createFallingElement, 300);
    </script>
</body>
</html>
