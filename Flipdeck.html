<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Memory Card Game</title>
    <link href="https://fonts.googleapis.com/css2?family=Press+Start+2P&display=swap" rel="stylesheet">
    <style>
        body {
            margin: 0;
            padding: 0;
            font-family: Arial, sans-serif;
            text-align: center;
        }

        h1 {
            margin: 10px 0;
        }

        .grid {
            display: grid;
            grid-template-columns: repeat(8, 100px); /* 8 columns for standard 52-card deck */
            gap: 10px;
            justify-content: center;
            margin: 20px auto;
        }

        .card {
            width: 100px;
            height: 150px;
            border: 2px solid black;
            border-radius: 8px;
            cursor: pointer;
            perspective: 1000px;
        }

        .card-inner {
            width: 100%;
            height: 100%;
            position: relative;
            transform-style: preserve-3d;
            transition: transform 0.6s;
        }

        .card.flipped .card-inner {
            transform: rotateY(180deg);
        }

        .card-front, .card-back {
            width: 100%;
            height: 100%;
            position: absolute;
            backface-visibility: hidden;
            display: flex;
            justify-content: center;
            align-items: center;
            border-radius: 8px;
            font-size: 24px;
            font-weight: bold;
        }

        .card-front {
            background-color: white;
            transform: rotateY(180deg); /* Initially hidden */
        }

        .card-back {
            background-color: lightblue;
        }

        .red-card {
            color: red;
        }

        .black-card {
            color: black;
        }

        .hidden {
            visibility: hidden;
        }

        #timer {
            margin: 20px;
            font-size: 24px;
        }

        #well-done {
            font-family: 'Press Start 2P', cursive;
            font-size: 32px;
            visibility: hidden;
            font-weight: bold;
            opacity: 0;
            animation: fadeIn 1s forwards;
        }

        .well-done-letter {
            display: inline-block;
            font-weight: bold;
            text-shadow: 2px 2px 5px black; /* Black outline effect */
            animation: bounce 0.5s ease forwards;
        }

        /* Animation for Well Done fade-in */
        @keyframes fadeIn {
            0% { opacity: 0; }
            100% { opacity: 1; }
        }

        /* Animation for letter bounce */
        @keyframes bounce {
            0% { transform: translateY(0); }
            50% { transform: translateY(-10px); }
            100% { transform: translateY(0); }
        }
    </style>
</head>
<body>
    <h1>Memory Card Game</h1>
    <p>Matches Found: <span id="match-counter">0</span></p>
    <p>Time: <span id="timer">0</span> seconds</p>
    <div class="grid" id="grid">
        <!-- Cards will be dynamically created -->
    </div>
    <p id="well-done"></p>

    <script>
        const suits = ["♥", "♦", "♣", "♠"];
        const ranks = ["A", "2", "3", "4", "5", "6", "7", "8", "9", "10", "J", "Q", "K"];
        const deck = [];

        // Create a full deck (single set, shuffled)
        for (const suit of suits) {
            for (const rank of ranks) {
                deck.push({ rank, suit });
            }
        }

        // Shuffle the deck
        function shuffle(array) {
            for (let i = array.length - 1; i > 0; i--) {
                const j = Math.floor(Math.random() * (i + 1));
                [array[i], array[j]] = [array[j], array[i]];
            }
        }
        shuffle(deck);

        const grid = document.getElementById('grid');
        const matchCounter = document.getElementById('match-counter');
        const timerDisplay = document.getElementById('timer');
        const wellDoneDisplay = document.getElementById('well-done');
        let firstCard = null;
        let secondCard = null;
        let matches = 0;
        let startTime = null;
        let timerInterval = null;

        // Create cards
        deck.forEach(card => {
            const cardElement = document.createElement('div');
            cardElement.classList.add('card');

            const cardInner = document.createElement('div');
            cardInner.classList.add('card-inner');

            const cardFront = document.createElement('div');
            cardFront.classList.add('card-front');
            cardFront.textContent = `${card.rank}${card.suit}`;
            if (card.suit === "♥" || card.suit === "♦") {
                cardFront.classList.add('red-card');
            } else {
                cardFront.classList.add('black-card');
            }

            const cardBack = document.createElement('div');
            cardBack.classList.add('card-back');
            cardBack.textContent = "🂠";

            cardInner.appendChild(cardFront);
            cardInner.appendChild(cardBack);
            cardElement.appendChild(cardInner);

            // Attach click event
            cardElement.addEventListener('click', () => {
                if (cardElement.classList.contains('flipped') || secondCard) {
                    return; // Ignore clicks on flipped or processing cards
                }
                cardElement.classList.add('flipped');
                if (!firstCard) {
                    firstCard = { element: cardElement, card };
                    if (!startTime) startTimer(); // Start timer when the first card is clicked
                } else {
                    secondCard = { element: cardElement, card };
                    // Check for a match (only rank matters)
                    if (firstCard.card.rank === secondCard.card.rank) {
                        setTimeout(() => {
                            firstCard.element.classList.add('hidden');
                            secondCard.element.classList.add('hidden');
                            matches++;
                            matchCounter.textContent = matches;
                            firstCard = null;
                            secondCard = null;

                            // Show "Well Done!" after 26 matches
                            if (matches === 26) {
                                showWellDone();
                                stopTimer(); // Freeze timer
                            }
                        }, 500);
                    } else {
                        setTimeout(() => {
                            firstCard.element.classList.remove('flipped');
                            secondCard.element.classList.remove('flipped');
                            firstCard = null;
                            secondCard = null;
                        }, 1000);
                    }
                }
            });

            grid.appendChild(cardElement);
        });

        // Timer function
        function startTimer() {
            startTime = Date.now();
            timerInterval = setInterval(() => {
                const elapsedTime = Math.floor((Date.now() - startTime) / 1000);
                timerDisplay.textContent = elapsedTime;
            }, 1000);
        }

        // Stop the timer
        function stopTimer() {
            clearInterval(timerInterval);
        }

        // Show "Well Done!" with colored letters and animations
        function showWellDone() {
            const message = "Well Done!";
            const colors = ['red', 'blue', 'green', 'purple'];
            wellDoneDisplay.innerHTML = ''; // Clear previous message

            for (let i = 0; i < message.length; i++) {
                const letter = document.createElement('span');
                letter.textContent = message[i];
                letter.classList.add('well-done-letter');
                letter.style.color = colors[i % colors.length]; // Cycle through colors
                wellDoneDisplay.appendChild(letter);
            }

            wellDoneDisplay.style.visibility = 'visible';
        }
    </script>
</body>
</html>
