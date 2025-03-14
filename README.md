<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Stoner Quiz Game</title>
    <style>
        body { font-family: Arial, sans-serif; text-align: center; background: #222; color: #fff; }
        .quiz-container { max-width: 600px; margin: auto; padding: 20px; background: #333; border-radius: 10px; }
        button { display: block; width: 100%; margin: 10px 0; padding: 10px; border: none; border-radius: 5px; cursor: pointer; }
        .result { font-size: 20px; margin-top: 20px; }
    </style>
</head>
<body>
    <div class="quiz-container">
        <h1>🌿 Stoner Quiz Game 🌿</h1>
        <p id="question"></p>
        <button onclick="answer(0)"></button>
        <button onclick="answer(1)"></button>
        <button onclick="answer(2)"></button>
        <p class="result" id="result"></p>
        <p class="result" id="final-score" style="display:none;"></p>
    </div>

    <script>
        const questions = [
            { q: "What’s your go-to munchies snack?", answers: ["Chips & Dip 🍟", "Candy 🍬", "Pizza 🍕"], types: ["The Classic Stoner", "The Sugar Rush Stoner", "The Gourmet Stoner"] },
            { q: "What’s your favorite activity when you're high?", answers: ["Watching movies 🎥", "Listening to music 🎵", "Deep conversations 🤯"], types: ["The Chill Stoner", "The Musical Stoner", "The Philosopher Stoner"] },
            { q: "If animals could talk, which one would have the best stories?", answers: ["Owls 🦉", "Dolphins 🐬", "Cats 🐱"], types: ["The Wise Stoner", "The Adventurous Stoner", "The Lazy Stoner"] },
            { q: "If time froze for an hour, what would you do?", answers: ["Take the best nap ever 😴", "Sneak into a candy store 🍭", "Rearrange people's stuff 🤪"], types: ["The Sleepy Stoner", "The Mischievous Stoner", "The Prankster Stoner"] },
            { q: "If you had a pet dragon, what would you name it?", answers: ["Smokey 🔥", "Blaze 🌿", "Dracozord 🐉"], types: ["The Fire Stoner", "The Herbal Stoner", "The Fantasy Stoner"] },
            { q: "If the moon was made of cheese, what type would it be?", answers: ["Cheddar 🧀", "Blue cheese 🌕", "Mozzarella 🏀"], types: ["The Classic Stoner", "The Fancy Stoner", "The Fun Stoner"] },
            { q: "Which superpower is best for snack time?", answers: ["Infinite snack pockets 🍫", "Make food appear 🍕", "Teleport to the fridge 🚪"], types: ["The Prepared Stoner", "The Magic Stoner", "The Lazy Stoner"] },
            { q: "If music had flavors, what would jazz taste like?", answers: ["Caramel latte ☕", "Fancy cheese board 🧀", "Mystery jellybean 🎵"], types: ["The Smooth Stoner", "The Classy Stoner", "The Trippy Stoner"] },
            { q: "If you could visit any fictional world, where would you go?", answers: ["Willy Wonka’s Factory 🍫", "Mushroom Kingdom 🍄", "SpongeBob’s Paradise 🌊"], types: ["The Sweet Stoner", "The Gamer Stoner", "The Beach Stoner"] },
            { q: "If the floor turned into lava, how would you survive?", answers: ["Jump on the couch 🛋", "Climb the walls 🕷", "Throw stuff to make a path 🛤"], types: ["The Quick Thinker Stoner", "The Agile Stoner", "The Engineer Stoner"] }
        ];
        
        let currentQuestion = 0;
        let stonerTypes = [];

        function loadQuestion() {
            if (currentQuestion < questions.length) {
                document.getElementById("question").innerText = questions[currentQuestion].q;
                document.querySelectorAll("button").forEach((btn, i) => {
                    btn.innerText = questions[currentQuestion].answers[i];
                });
            } else {
                document.getElementById("question").innerText = "Game Over!";
                document.querySelectorAll("button").forEach(btn => btn.style.display = "none");
                const mostCommonType = stonerTypes.sort((a,b) => stonerTypes.filter(v => v===a).length - stonerTypes.filter(v => v===b).length).pop();
                document.getElementById("final-score").innerText = "You are: " + mostCommonType + "!";
                document.getElementById("final-score").style.display = "block";
            }
        }

        function answer(choice) {
            stonerTypes.push(questions[currentQuestion].types[choice]);
            currentQuestion++;
            loadQuestion();
        }

        loadQuestion();
    </script>
</body>
</html>
