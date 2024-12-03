<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Interactive Deck of Cards</title>
    <style>
        .grid {
            display: grid;
            grid-template-columns: repeat(13, 100px);
            grid-template-rows: repeat(4, 150px);
            gap: 5px;
            justify-content: center;
        }

        .card {
            width: 100px;
            height: 150px;
            border: 2px solid black;
            border-radius: 8px;
            cursor: pointer;
            perspective: 1000px; /* For the flip animation */
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
        }

        .card-front {
            background-color: white;
            font-size: 24px;
            font-weight: bold;
            color: black;
            transform: rotateY(180deg); /* Initially hidden */
        }

        .card-back {
            background-color: lightblue;
        }
    </style>
</head>
<body>
    <h1>Interactive Deck of Cards</h1>
    <div class="grid" id="grid">
        <!-- Cards will be dynamically created -->
    </div>

    <script>
        // Suits and card ranks
        const suits = ["♥", "♦", "♣", "♠"];
        const ranks = ["A", "2", "3", "4", "5", "6", "7", "8", "9", "10", "J", "Q", "K"];
        
        // Create a full deck of cards
        const deck = [];
        for (const suit of suits) {
            for (const rank of ranks) {
                deck.push(`${rank}${suit}`);
            }
        }

        // Shuffle the deck randomly
        function shuffle(array) {
            for (let i = array.length - 1; i > 0; i--) {
                const j = Math.floor(Math.random() * (i + 1));
                [array[i], array[j]] = [array[j], array[i]];
            }
        }
        shuffle(deck);

        // Add cards to the grid
        const grid = document.getElementById('grid');
        deck.forEach(card => {
            const cardElement = document.createElement('div');
            cardElement.classList.add('card');

            const cardInner = document.createElement('div');
            cardInner.classList.add('card-inner');

            const cardFront = document.createElement('div');
            cardFront.classList.add('card-front');
            cardFront.textContent = card; // Set rank and suit up front

            const cardBack = document.createElement('div');
            cardBack.classList.add('card-back');
            cardBack.textContent = "🂠"; // Represents a card back (optional emoji)

            cardInner.appendChild(cardFront);
            cardInner.appendChild(cardBack);
            cardElement.appendChild(cardInner);

            // Add click event to flip the card
            cardElement.addEventListener('click', () => {
                cardElement.classList.toggle('flipped');
            });

            grid.appendChild(cardElement);
        });
    </script>
</body>
</html>
