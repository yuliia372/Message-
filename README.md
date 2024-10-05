<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Gradient Background with Click Messages</title>
    <style>
        body {
            margin: 0;
            height: 100vh;
            display: flex;
            justify-content: center;
            align-items: center;
            font-family: Arial, sans-serif;
            color: white;
            background: linear-gradient(to bottom, darkblue, darkred);
            overflow: hidden;
        }

        .message {
            font-size: 24px;
            text-align: center;
            position: absolute;
        }
    </style>
</head>
<body>
    <div class="message" id="message">Click anywhere to change this message!</div>

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
        });
    </script>
</body>
</html>
