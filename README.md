<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Playful Valentine's Day</title>
    <style>
        body {
            font-family: 'Comic Sans MS', cursive, sans-serif;
            text-align: center;
            margin: 0;
            overflow: hidden; /* Hide overflow to prevent scrollbars */
            background-color: #000000; /* Black background color */
            color: #ff69b4; /* Pink text color */
            font-weight: bold; /* Bold text */
            transition: background-color 1s ease-in-out; /* Transition for background color change */
        }

        #invitation-text {
            font-size: 28px;
            margin: 20px 0;
        }

        #invitation-button {
            padding: 15px 30px;
            font-size: 20px;
            cursor: pointer;
            background-color: #ff69b4;
            border: 2px solid #fff;
            border-radius: 10px;
            transition: background-color 0.3s ease-in-out;
        }

        #invitation-button:hover {
            background-color: #ff3385;
        }

        #response-input {
            padding: 10px;
            font-size: 16px;
            margin-top: 20px;
            border: 2px solid #ff69b4;
            border-radius: 5px;
            width: 250px;
        }

        #response-button {
            padding: 10px 20px;
            font-size: 16px;
            cursor: pointer;
            background-color: #4caf50;
            color: #fff;
            border: none;
            border-radius: 5px;
            margin-top: 10px;
            transition: background-color 0.3s ease-in-out;
        }

        #response-button:hover {
            background-color: #45a049;
        }

        #heart-animation-container {
            position: fixed;
            top: 0;
            left: 0;
            width: 100%;
            height: 100%;
            pointer-events: none; /* Allow interaction with elements behind */
            z-index: 9999; /* Ensure the hearts appear above other elements */
        }

        .heart {
            position: absolute;
            width: 20px;
            height: 20px;
            background-color: #ff0000; /* Red heart color */
            clip-path: polygon(
                50% 0%, 61% 35%, 98% 35%, 68% 57%,
                79% 91%, 50% 70%, 21% 91%, 32% 57%,
                2% 35%, 39% 35%
            );
            animation: heartFloat 3s ease-out infinite;
        }

        @keyframes heartFloat {
            0%, 20%, 40%, 60%, 80%, 100% {
                transform: translateY(0) rotate(0deg);
            }
            10%, 30%, 50%, 70%, 90% {
                transform: translateY(calc(-100vh + 20px)) rotate(360deg);
            }
        }

        @keyframes screenAnimation {
            0% {
                background-color: #000000;
            }
            50% {
                background-color: #ff69b4;
            }
            100% {
                background-color: #000000;
            }
        }
    </style>
</head>
<body>
    <h1>My forever</h1>
    <p id="invitation-text">Njuafac Gustave Tendongzi, my love, best friend, and soulmate. Will you be my valentine? <span id="heart-animation">❤️</span></p>
    <button id="invitation-button" onclick="showResponseInput()">Send Invitation</button>

    <div id="response-container" style="display: none;">
        <p>What's your response?</p>
        <input type="text" id="response-input" placeholder="Type yes! or no! ">
        <button id="response-button" onclick="handleResponse()">Submit</button>
    </div>

    <!-- Container for heart animation -->
    <div id="heart-animation-container"></div>

    <script>
        function showResponseInput() {
            document.getElementById('response-container').style.display = 'block';
        }

        function handleResponse() {
            var response = document.getElementById('response-input').value;
            if (response.toLowerCase().includes('yes')) {
                animateScreen(); // Call the animation function
                alert("Yay! I love you! Can't wait for our Valentine's Day together! ❤️");
            } else {
                alert("Oh no! I hate you! But, let's make it a special day anyway. ❤️");
            }
        }

        // Function to create a floating heart
        function createHeart() {
            const heart = document.createElement('div');
            heart.className = 'heart';
            heart.style.left = Math.random() * 100 + 'vw';
            heart.style.animationDuration = Math.random() * 2 + 1 + 's'; // Vary animation duration for a more natural look
            document.getElementById('heart-animation-container').appendChild(heart);

            // Remove the heart after animation completes
            heart.addEventListener('animationend', () => {
                heart.remove();
            });
        }

        // Create hearts at regular intervals
        setInterval(createHeart, 1000);

        // Function to animate the screen
        function animateScreen() {
            document.body.style.animation = 'screenAnimation 2s ease-in-out';
        }
    </script>
</body>
</html>
