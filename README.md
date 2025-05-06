# WebDev-week-7-Assignment

<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Dynamic Webpage with Local Storage</title>
    <link href="https://fonts.googleapis.com/css2?family=Inter:wght@400;600&display=swap" rel="stylesheet">
    <style>
        body {
            font-family: 'Inter', sans-serif;
            margin: 0;
            padding: 0;
            background-color: #f9f9f9;
            color: #333;
            line-height: 1.6;
        }
        header {
            background-color: #4CAF50;
            padding: 20px;
            text-align: center;
            box-shadow: 0 2px 4px rgba(0,0,0,0.1);
            transition: background-color 0.3s ease; /* Smooth transition */
        }
        header:hover {
            background-color: #45a049; /* Darker shade on hover */
        }
        h1 {
            margin: 0;
            color: white;
        }
        main {
            padding: 20px;
            text-align: center;
        }
        #counter {
            font-size: 2em;
            margin-bottom: 20px;
            color: #555;
            transition: transform 0.2s ease, color 0.3s ease; /* Added transform */
        }
        #counter:hover {
            transform: scale(1.1); /* Slight scale on hover */
            color: #4CAF50;
        }
        button {
            padding: 12px 24px;
            font-size: 16px;
            cursor: pointer;
            border: none;
            border-radius: 5px;
            background-color: #4CAF50;
            color: white;
            margin: 10px;
            transition: background-color 0.3s ease, transform 0.1s ease; /* Smooth transition */
        }
        button:hover {
            background-color: #45a049;
            transform: scale(1.05); /* Slight scale on hover */
        }
        button:disabled {
            background-color: #ccc;
            cursor: not-allowed;
            transform: none;
        }
        #message {
            font-size: 18px;
            margin-top: 20px;
            color: #333;
            opacity: 0;
            transition: opacity 0.3s ease; /* Added opacity transition */
        }
        .show-message {
            opacity: 1;
        }
        @keyframes fadeIn {
            from { opacity: 0; }
            to { opacity: 1; }
        }
        footer {
            background-color: #f0f0f0;
            padding: 10px;
            text-align: center;
            margin-top: 20px;
            color: #777;
            animation: fadeIn 1s ease; /* Apply fadeIn animation */
        }
    </style>
</head>
<body>
    <header>
        <h1>Dynamic Counter Webpage</h1>
    </header>
    <main>
        <div id="counter">0</div>
        <button id="incrementBtn">Increment Counter</button>
        <button id="decrementBtn" disabled>Decrement Counter</button>
        <p id="message"></p>
    </main>
    <footer>
        <p>&copy; 2025 Dynamic Webpage</p>
    </footer>
    <script>
        const counterDisplay = document.getElementById('counter');
        const incrementBtn = document.getElementById('incrementBtn');
        const decrementBtn = document.getElementById('decrementBtn');
        const message = document.getElementById('message');

        let counter = parseInt(localStorage.getItem('counter')) || 0;
        counterDisplay.textContent = counter;

        function updateCounter() {
            counterDisplay.textContent = counter;
            localStorage.setItem('counter', counter);
            message.textContent = `Counter updated: ${counter}`;
            message.classList.add('show-message');
            setTimeout(() => {
                message.classList.remove('show-message');
            }, 300);

            decrementBtn.disabled = counter <= 0;
        }

        incrementBtn.addEventListener('click', () => {
            counter++;
            updateCounter();
        });

        decrementBtn.addEventListener('click', () => {
            if (counter > 0) {
                counter--;
                updateCounter();
            }
        });
    </script>
</body>
</html>
