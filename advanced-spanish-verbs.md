<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Advanced Spanish Verb Combinations</title>
    <style>
        :root {
            --primary: #2c3e50;
            --secondary: #34495e;
            --accent: #3498db;
            --background: #fdfbf7;
            --card-bg: #ffffff;
            --text-main: #333333;
            --text-light: #7f8c8d;
            --border-radius: 12px;
        }

        * {
            box-sizing: border-box;
            margin: 0;
            padding: 0;
            font-family: 'Segoe UI', Roboto, Helvetica, Arial, sans-serif;
        }

        body {
            background-color: var(--background);
            color: var(--text-main);
            display: flex;
            flex-direction: column;
            align-items: center;
            min-height: 100vh;
            padding: 2rem 1rem;
        }

        header {
            text-align: center;
            margin-bottom: 2rem;
            max-width: 600px;
        }

        h1 {
            color: var(--primary);
            font-size: 2rem;
            margin-bottom: 0.5rem;
        }

        p.subtitle {
            color: var(--text-light);
            font-size: 1rem;
            line-height: 1.5;
        }

        .controls-container {
            display: flex;
            flex-wrap: wrap;
            gap: 1rem;
            justify-content: center;
            margin-bottom: 2rem;
            width: 100%;
            max-width: 600px;
        }

        select, button {
            padding: 0.75rem 1.25rem;
            font-size: 1rem;
            border: 1px solid #ccc;
            border-radius: 6px;
            background-color: white;
            cursor: pointer;
            outline: none;
            transition: all 0.2s ease;
        }

        select {
            flex: 1;
            min-width: 200px;
            color: var(--primary);
            font-weight: 600;
        }

        button {
            background-color: var(--accent);
            color: white;
            border: none;
            font-weight: 600;
        }

        button:hover {
            background-color: #2980b9;
            transform: translateY(-1px);
        }

        button:active {
            transform: translateY(1px);
        }

        .card-container {
            perspective: 1000px;
            width: 100%;
            max-width: 500px;
            height: 300px;
            margin-bottom: 2rem;
        }

        .card {
            width: 100%;
            height: 100%;
            position: relative;
            transition: transform 0.6s cubic-bezier(0.4, 0.2, 0.2, 1);
            transform-style: preserve-3d;
            cursor: pointer;
            box-shadow: 0 10px 25px rgba(0,0,0,0.05);
            border-radius: var(--border-radius);
        }

        .card.is-flipped {
            transform: rotateY(180deg);
        }

        .card-face {
            position: absolute;
            width: 100%;
            height: 100%;
            backface-visibility: hidden;
            display: flex;
            flex-direction: column;
            justify-content: center;
            align-items: center;
            padding: 2rem;
            text-align: center;
            border-radius: var(--border-radius);
            background-color: var(--card-bg);
            border: 1px solid #eaeaea;
        }

        .card-front {
            /* Front is English */
        }

        .card-back {
            transform: rotateY(180deg);
            background-color: var(--primary);
            color: white;
            border: none;
        }

        .phrase {
            font-size: 1.75rem;
            font-weight: 700;
            margin-bottom: 1rem;
        }

        .category-tag {
            font-size: 0.85rem;
            text-transform: uppercase;
            letter-spacing: 1px;
            padding: 4px 10px;
            border-radius: 20px;
            background-color: #f0f3f4;
            color: var(--text-light);
            position: absolute;
            top: 20px;
        }
        
        .card-back .category-tag {
            background-color: rgba(255,255,255,0.2);
            color: white;
        }

        .verb-base {
            font-size: 1rem;
            color: var(--text-light);
            position: absolute;
            bottom: 20px;
            font-style: italic;
        }
        
        .card-back .verb-base {
            color: rgba(255,255,255,0.7);
        }

        .status {
            font-size: 0.9rem;
            color: var(--text-light);
            margin-bottom: 1rem;
            font-weight: 600;
        }
        
        @media (max-width: 600px) {
            .phrase { font-size: 1.4rem; }
        }
    </style>
</head>
<body>

    <header>
        <h1>Spanish Perífrasis Verbales</h1>
        <p class="subtitle">Master advanced verbal constructions and combinations. Click the card to flip.</p>
    </header>

    <div class="controls-container">
        <select id="categoryFilter" onchange="filterCards()">
            <option value="All">All Categories</option>
            <option value="Perfects">Perfect & Compound Tenses</option>
            <option value="Modals">Modals & Obligations</option>
            <option value="Inchoatives">Inchoatives (Beginning)</option>
            <option value="Progressives">Progressives (Ongoing)</option>
            <option value="Terminatives">Terminatives (Ending/Result)</option>
        </select>
        <button onclick="shuffleCards()">Shuffle</button>
    </div>

    <div class="status" id="counter">Card 1 of 200+</div>

    <div class="card-container" onclick="flipCard()">
        <div class="card" id="flashcard">
            <div class="card-face card-front">
                <span class="category-tag" id="front-category">Category</span>
                <div class="phrase" id="front-phrase">Loading...</div>
                <div class="verb-base" id="front-base">base verb</div>
            </div>
            <div class="card-face card-back">
                <span class="category-tag" id="back-category">Categoría</span>
                <div class="phrase" id="back-phrase">Cargando...</div>
                <div class="verb-base" id="back-base">verbo base</div>
            </div>
        </div>
    </div>

    <div class="controls-container" style="margin-top: 0;">
        <button onclick="prevCard()">&larr; Previous</button>
        <button onclick="nextCard()">Next &rarr;</button>
    </div>

    <script>
        // Data sets
        const verbs = [
            { inf: "leer", ger: "leyendo", part: "leído", en: "read", en_ing: "reading", en_pp: "read" },
            { inf: "escribir", ger: "escribiendo", part: "escrito", en: "write", en_ing: "writing", en_pp: "written" },
            { inf: "investigar", ger: "investigando", part: "investigado", en: "research", en_ing: "researching", en_pp: "researched" },
            { inf: "enseñar", ger: "enseñando", part: "enseñado", en: "teach", en_ing: "teaching", en_pp: "taught" },
            { inf: "entrenar", ger: "entrenando", part: "entrenado", en: "train", en_ing: "training", en_pp: "trained" },
            { inf: "mejorar", ger: "mejorando", part: "mejorado", en: "improve", en_ing: "improving", en_pp: "improved" },
            { inf: "estudiar", ger: "estudiando", part: "estudiado", en: "study", en_ing: "studying", en_pp: "studied" },
            { inf: "preparar", ger: "preparando", part: "preparado", en: "prepare", en_ing: "preparing", en_pp: "prepared" },
            { inf: "practicar", ger: "practicando", part: "practicado", en: "practice", en_ing: "practicing", en_pp: "practiced" },
            { inf: "buscar", ger: "buscando", part: "buscado", en: "search for", en_ing: "searching for", en_pp: "searched for" },
            { inf: "hacer", ger: "haciendo", part: "hecho", en: "do", en_ing: "doing", en_pp: "done" },
            { inf: "decir", ger: "diciendo", part: "dicho", en: "say", en_ing: "saying", en_pp: "said" },
            { inf: "ver", ger: "viendo", part: "visto", en: "see", en_ing: "seeing", en_pp: "seen" },
            { inf: "aprender", ger: "aprendiendo", part: "aprendido", en: "learn", en_ing: "learning", en_pp: "learned" },
            { inf: "planear", ger: "planeando", part: "planeado", en: "plan", en_ing: "planning", en_pp: "planned" }
        ];

        const structures = [
            // Perfects
            { sp: "He {part}", en: "I have {en_pp}", cat: "Perfects" },
            { sp: "Había {part}", en: "I had {en_pp}", cat: "Perfects" },
            { sp: "Habré {part}", en: "I will have {en_pp}", cat: "Perfects" },
            { sp: "Habría {part}", en: "I would have {en_pp}", cat: "Perfects" },
            { sp: "Espero que haya {part}", en: "I hope that I have {en_pp}", cat: "Perfects" },
            { sp: "Si hubiera {part}...", en: "If I had {en_pp}...", cat: "Perfects" },
            // Modals
            { sp: "Tengo que {inf}", en: "I have to {en}", cat: "Modals" },
            { sp: "Debo {inf}", en: "I must {en}", cat: "Modals" },
            { sp: "Hay que {inf}", en: "One must {en}", cat: "Modals" },
            { sp: "Suelo {inf}", en: "I usually {en}", cat: "Modals" },
            { sp: "Voy a tener que {inf}", en: "I am going to have to {en}", cat: "Modals" },
            { sp: "Quisiera {inf}", en: "I would like to {en}", cat: "Modals" },
            // Inchoatives
            { sp: "Empiezo a {inf}", en: "I am starting to {en}", cat: "Inchoatives" },
            { sp: "Me puse a {inf}", en: "I set about {en_ing}", cat: "Inchoatives" },
            { sp: "Paso a {inf}", en: "I am moving on to {en}", cat: "Inchoatives" },
            { sp: "Llegué a {inf}", en: "I managed to {en}", cat: "Inchoatives" },
            // Progressives
            { sp: "Estoy {ger}", en: "I am {en_ing}", cat: "Progressives" },
            { sp: "Sigo {ger}", en: "I am still {en_ing}", cat: "Progressives" },
            { sp: "Llevo meses {ger}", en: "I have spent months {en_ing}", cat: "Progressives" },
            { sp: "Voy {ger} poco a poco", en: "I am gradually {en_ing}", cat: "Progressives" },
            { sp: "Ando {ger} por ahí", en: "I am going around {en_ing}", cat: "Progressives" },
            // Terminatives
            { sp: "Acabo de {inf}", en: "I have just {en_pp}", cat: "Terminatives" },
            { sp: "Terminé de {inf}", en: "I finished {en_ing}", cat: "Terminatives" },
            { sp: "Dejé de {inf}", en: "I stopped {en_ing}", cat: "Terminatives" },
            { sp: "Vuelvo a {inf}", en: "I am {en_ing} again", cat: "Terminatives" },
            { sp: "Acabé por {inf}", en: "I ended up {en_ing}", cat: "Terminatives" }
        ];

        let allCards = [];
        let currentDeck = [];
        let currentIndex = 0;

        // Generate Cards
        function generateCards() {
            structures.forEach(struct => {
                verbs.forEach(verb => {
                    let spPhrase = struct.sp.replace("{inf}", verb.inf).replace("{ger}", verb.ger).replace("{part}", verb.part);
                    let enPhrase = struct.en.replace("{en}", verb.en).replace("{en_ing}", verb.en_ing).replace("{en_pp}", verb.en_pp);
                    
                    allCards.push({
                        sp: spPhrase,
                        en: enPhrase,
                        cat: struct.cat,
                        base_sp: verb.inf,
                        base_en: verb.en
                    });
                });
            });
            currentDeck = [...allCards];
            shuffleCards(); // Initial shuffle
        }

        function updateDisplay() {
            if (currentDeck.length === 0) return;
            
            const card = currentDeck[currentIndex];
            
            document.getElementById("front-phrase").textContent = card.en;
            document.getElementById("front-category").textContent = card.cat;
            document.getElementById("front-base").textContent = `Base: to ${card.base_en}`;
            
            document.getElementById("back-phrase").textContent = card.sp;
            document.getElementById("back-category").textContent = card.cat;
            document.getElementById("back-base").textContent = `Base: ${card.base_sp}`;
            
            document.getElementById("counter").textContent = `Card ${currentIndex + 1} of ${currentDeck.length}`;
            
            // Ensure card shows front when moving to next
            const cardEl = document.getElementById("flashcard");
            if (cardEl.classList.contains("is-flipped")) {
                cardEl.classList.remove("is-flipped");
                // Small delay to let flip animation reset before text changes if we were optimizing, 
                // but instantaneous text replacement is usually fine for flashcards.
            }
        }

        function flipCard() {
            document.getElementById("flashcard").classList.toggle("is-flipped");
        }

        function nextCard() {
            currentIndex = (currentIndex + 1) % currentDeck.length;
            updateDisplay();
        }

        function prevCard() {
            currentIndex = (currentIndex - 1 + currentDeck.length) % currentDeck.length;
            updateDisplay();
        }

        function shuffleCards() {
            for (let i = currentDeck.length - 1; i > 0; i--) {
                const j = Math.floor(Math.random() * (i + 1));
                [currentDeck[i], currentDeck[j]] = [currentDeck[j], currentDeck[i]];
            }
            currentIndex = 0;
            updateDisplay();
        }

        function filterCards() {
            const category = document.getElementById("categoryFilter").value;
            if (category === "All") {
                currentDeck = [...allCards];
            } else {
                currentDeck = allCards.filter(card => card.cat === category);
            }
            currentIndex = 0;
            updateDisplay();
        }

        // Keyboard navigation
        document.addEventListener('keydown', function(event) {
            if (event.key === 'ArrowRight') {
                nextCard();
            } else if (event.key === 'ArrowLeft') {
                prevCard();
            } else if (event.key === ' ' || event.key === 'ArrowUp' || event.key === 'ArrowDown') {
                event.preventDefault();
                flipCard();
            }
        });

        // Initialize
        generateCards();
        
    </script>
</body>
</html>
