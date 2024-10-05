< html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Moving Cats with Gradient Background</title>
    <style>
        body {
            margin: 0;
            height: 100vh;
            display: flex;
            justify-content: center;
            align-items: center;
            overflow: hidden;
            background: linear-gradient(to bottom, darkblue, darkred);
            position: relative;
        }

        .message {
            font-size: 24px;
            color: white;
            position: absolute;
            top: 20px;
            text-align: center;
        }

        .cat {
            position: absolute;
            width: 50px;
            height: 50px;
            background: black;
            clip-path: polygon(20% 100%, 50% 0%, 80% 100%, 50% 80%);
            animation: move 4s linear forwards;
        }

        @keyframes move {
            0% {
                transform: translateX(0);
            }
            50% {
                transform: translateX(50vw);
            }
            100% {
                transform: translateX(calc(50vw - 50px));
            }
        }

        .cat2 {
            animation-direction: reverse;
        }
    </style>
</head>
<body>
    <div class="message" id="message">Click anywhere to change this message!</div>
    <div class="cat" id="cat1"></div>
    <div class="cat cat2" id="cat2"></div>

    <script>
        const messages = [
            "Hello, world!",
            "Welcome to my site!",
            "Have a great day!",
            "Keep clicking!",
            "You're doing awesome!",
            "Thanks for visiting!"
        ];

        let messageIndex = 0;

        document.body.addEventListener('click', () => {
            messageIndex = (messageIndex + 1) % messages.length;
            document.getElementById('message').innerText = messages[messageIndex];
            moveCats();
        });

        function moveCats() {
            const cat1 = document.getElementById('cat1');
            const cat2 = document.getElementById('cat2');
            
            // Reset position of cats
            cat1.style.transform = 'translateX(-50px)';
            cat2.style.transform = 'translateX(calc(100vw - 50px))';

            // Trigger reflow to restart animation
            cat1.style.animation = 'none';
            cat2.style.animation = 'none';

            void cat1.offsetWidth; // Trigger reflow
            void cat2.offsetWidth; // Trigger reflow

            // Set the animations to run again
            cat1.style.animation = 'move 4s linear forwards';
            cat2.style.animation = 'move 4s linear forwards';
        }
    </script>
</body>
</html>
