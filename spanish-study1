<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>500 Spanish Verbs Conjugation Flashcards</title>
    <style>
        :root {
            --primary: #0f172a;
            --secondary: #2563eb;
            --accent: #d97706;
            --background: #f8fafc;
            --card-bg: #ffffff;
            --text-main: #0f172a;
            --text-light: #64748b;
            --border-radius: 16px;
        }

        * {
            box-sizing: border-box;
            margin: 0;
            padding: 0;
            font-family: 'Segoe UI', system-ui, -apple-system, BlinkMacSystemFont, Roboto, sans-serif;
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
            margin-bottom: 1.5rem;
            max-width: 760px;
        }

        h1 {
            color: var(--primary);
            font-size: 2.2rem;
            margin-bottom: 0.5rem;
            font-weight: 800;
        }

        p.subtitle {
            color: var(--text-light);
            font-size: 1.05rem;
            line-height: 1.5;
        }

        .controls-container {
            display: flex;
            flex-wrap: wrap;
            gap: 0.75rem;
            justify-content: center;
            margin-bottom: 1.5rem;
            width: 100%;
            max-width: 760px;
        }

        select, button, input {
            padding: 0.75rem 1rem;
            font-size: 0.95rem;
            border: 1px solid #cbd5e1;
            border-radius: 10px;
            background-color: white;
            cursor: pointer;
            outline: none;
            transition: all 0.2s ease;
        }

        select {
            flex: 1;
            min-width: 180px;
            color: var(--primary);
            font-weight: 600;
        }

        input[type="text"] {
            flex: 1;
            min-width: 180px;
            cursor: text;
        }

        button {
            background-color: var(--secondary);
            color: white;
            border: none;
            font-weight: 600;
        }

        button:hover {
            background-color: #1d4ed8;
            transform: translateY(-1px);
        }

        button:active {
            transform: translateY(1px);
        }

        .card-container {
            perspective: 1000px;
            width: 100%;
            max-width: 620px;
            height: 380px;
            margin-bottom: 1.5rem;
        }

        .card {
            width: 100%;
            height: 100%;
            position: relative;
            transition: transform 0.6s cubic-bezier(0.4, 0.2, 0.2, 1);
            transform-style: preserve-3d;
            cursor: pointer;
            box-shadow: 0 14px 32px rgba(0,0,0,0.08);
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
            padding: 2.5rem;
            text-align: center;
            border-radius: var(--border-radius);
            background-color: var(--card-bg);
            border: 1px solid #e2e8f0;
        }

        .card-back {
            transform: rotateY(180deg);
            background-color: var(--primary);
            color: white;
            border: none;
        }

        .prompt-verb {
            font-size: 2.2rem;
            font-weight: 800;
            color: var(--secondary);
            margin-bottom: 0.5rem;
        }

        .prompt-details {
            font-size: 1.25rem;
            font-weight: 600;
            color: var(--text-main);
            margin-bottom: 0.5rem;
        }

        .prompt-meaning {
            font-size: 1rem;
            color: var(--text-light);
            font-style: italic;
        }

        .answer-conjugation {
            font-size: 2.5rem;
            font-weight: 800;
            color: #38bdf8;
            margin-bottom: 0.75rem;
        }

        .answer-translation {
            font-size: 1.2rem;
            font-weight: 500;
            color: #f1f5f9;
            margin-bottom: 1rem;
        }

        .badge {
            font-size: 0.8rem;
            text-transform: uppercase;
            letter-spacing: 0.8px;
            padding: 5px 12px;
            border-radius: 20px;
            position: absolute;
            top: 20px;
            font-weight: 700;
        }

        .badge-tense {
            background-color: #fef3c7;
            color: #b45309;
            left: 20px;
        }

        .badge-person {
            background-color: #e0f2fe;
            color: #0369a1;
            right: 20px;
        }

        .card-back .badge-tense {
            background-color: rgba(255,255,255,0.18);
            color: #fef3c7;
        }

        .card-back .badge-person {
            background-color: rgba(255,255,255,0.18);
            color: #38bdf8;
        }

        .grammar-hint {
            font-size: 0.85rem;
            color: rgba(255,255,255,0.7);
            position: absolute;
            bottom: 20px;
        }

        .status {
            font-size: 0.95rem;
            color: var(--text-light);
            margin-bottom: 1rem;
            font-weight: 600;
        }

        .key-hint {
            font-size: 0.85rem;
            color: var(--text-light);
            text-align: center;
        }
    </style>
</head>
<body>

    <header>
        <h1>Spanish 500 Verb Conjugator</h1>
        <p class="subtitle">Master all 6 person forms across Present, Preterite, Imperfect, Future, Informal Future, and Present Subjunctive (18,000 flashcard combinations).</p>
    </header>

    <div class="controls-container">
        <select id="tenseFilter" onchange="applyFilters()">
            <option value="All">All Tenses (6 Tenses)</option>
            <option value="Presente">Presente (Present)</option>
            <option value="Pretérito Indefinido">Pretérito Indefinido (Preterite)</option>
            <option value="Pretérito Imperfecto">Pretérito Imperfecto (Imperfect)</option>
            <option value="Futuro Simple">Futuro Simple (Simple Future)</option>
            <option value="Futuro Informal">Futuro Informal (Ir a + inf)</option>
            <option value="Presente de Subjuntivo">Presente de Subjuntivo (Subjunctive)</option>
        </select>

        <select id="personFilter" onchange="applyFilters()">
            <option value="All">All Persons (6 Forms)</option>
            <option value="0">yo (1st Person Sing.)</option>
            <option value="1">tú (2nd Person Sing.)</option>
            <option value="2">él / ella / usted (3rd Person Sing.)</option>
            <option value="3">nosotros / nosotras (1st Person Plur.)</option>
            <option value="4">vosotros / vosotras (2nd Person Plur.)</option>
            <option value="5">ellos / ellas / ustedes (3rd Person Plur.)</option>
        </select>

        <input type="text" id="verbSearch" placeholder="Search verb (e.g. hablar)" oninput="applyFilters()" />
        
        <button onclick="shuffleDeck()">Shuffle</button>
    </div>

    <div class="status" id="counter">Loading flashcards...</div>

    <div class="card-container" onclick="flipCard()">
        <div class="card" id="flashcard">
            <div class="card-face card-front">
                <span class="badge badge-tense" id="front-tense">Tense</span>
                <span class="badge badge-person" id="front-person">Person</span>
                <div class="prompt-verb" id="front-verb">verb</div>
                <div class="prompt-details" id="front-prompt-details">Pronoun</div>
                <div class="prompt-meaning" id="front-meaning">meaning</div>
            </div>
            <div class="card-face card-back">
                <span class="badge badge-tense" id="back-tense">Tense</span>
                <span class="badge badge-person" id="back-person">Person</span>
                <div class="answer-conjugation" id="back-conjugation">Conjugation</div>
                <div class="answer-translation" id="back-translation">Translation</div>
                <div class="grammar-hint" id="back-hint">Rule</div>
            </div>
        </div>
    </div>

    <div class="controls-container" style="margin-top: 0;">
        <button onclick="prevCard()">&larr; Previous</button>
        <button onclick="nextCard()">Next &rarr;</button>
    </div>

    <div class="key-hint">
        Press <strong>Spacebar</strong> to flip | <strong>Left/Right Arrows</strong> to navigate
    </div>

    <script>
        const verbsData = [{"inf": "ser", "en": "to be (essential/permanent)", "irreg": true}, {"inf": "estar", "en": "to be (location/state)", "irreg": true}, {"inf": "tener", "en": "to have / possess", "stem": "e-ie", "irreg": true}, {"inf": "hacer", "en": "to do / make", "irreg": true}, {"inf": "ir", "en": "to go", "irreg": true}, {"inf": "poder", "en": "to be able to / can", "stem": "o-ue", "irreg": true}, {"inf": "decir", "en": "to say / tell", "stem": "e-i", "irreg": true}, {"inf": "ver", "en": "to see / watch", "irreg": true}, {"inf": "dar", "en": "to give", "irreg": true}, {"inf": "saber", "en": "to know (facts/skills)", "irreg": true}, {"inf": "querer", "en": "to want / love", "stem": "e-ie", "irreg": true}, {"inf": "llegar", "en": "to arrive", "ortho": "gar"}, {"inf": "pasar", "en": "to pass / spend time / happen"}, {"inf": "deber", "en": "to owe / must"}, {"inf": "poner", "en": "to put / place", "irreg": true}, {"inf": "parecer", "en": "to seem / look like", "ortho": "zco"}, {"inf": "hablar", "en": "to speak / talk"}, {"inf": "quedar", "en": "to stay / remain / meet"}, {"inf": "seguir", "en": "to follow / continue", "stem": "e-i", "ortho": "gu"}, {"inf": "llevar", "en": "to carry / wear / take"}, {"inf": "dejar", "en": "to leave / let / allow"}, {"inf": "encontrar", "en": "to find", "stem": "o-ue"}, {"inf": "llamar", "en": "to call / name"}, {"inf": "venir", "en": "to come", "stem": "e-ie", "irreg": true}, {"inf": "pensar", "en": "to think", "stem": "e-ie"}, {"inf": "salir", "en": "to exit / go out", "irreg": true}, {"inf": "volver", "en": "to return / go back", "stem": "o-ue", "irreg": true}, {"inf": "tomar", "en": "to take / drink"}, {"inf": "conocer", "en": "to know (people/places)", "ortho": "zco"}, {"inf": "vivir", "en": "to live"}, {"inf": "sentir", "en": "to feel / regret", "stem": "e-ie"}, {"inf": "tratar", "en": "to treat / try"}, {"inf": "mirar", "en": "to look at / watch"}, {"inf": "contar", "en": "to count / tell a story", "stem": "o-ue"}, {"inf": "empezar", "en": "to start / begin", "stem": "e-ie", "ortho": "zar"}, {"inf": "esperar", "en": "to wait / hope / expect"}, {"inf": "buscar", "en": "to search / look for", "ortho": "car"}, {"inf": "existir", "en": "to exist"}, {"inf": "entrar", "en": "to enter / go in"}, {"inf": "trabajar", "en": "to work"}, {"inf": "escribir", "en": "to write", "irreg": true}, {"inf": "perder", "en": "to lose / miss", "stem": "e-ie"}, {"inf": "producir", "en": "to produce", "ortho": "zco", "irreg": true}, {"inf": "recordar", "en": "to remember", "stem": "o-ue"}, {"inf": "entender", "en": "to understand", "stem": "e-ie"}, {"inf": "pedir", "en": "to ask for / request", "stem": "e-i"}, {"inf": "recibir", "en": "to receive"}, {"inf": "comenzar", "en": "to commence / start", "stem": "e-ie", "ortho": "zar"}, {"inf": "servir", "en": "to serve", "stem": "e-i"}, {"inf": "sacar", "en": "to take out / remove", "ortho": "car"}, {"inf": "necesitar", "en": "to need"}, {"inf": "mantenerme", "en": "to maintain oneself"}, {"inf": "mantener", "en": "to maintain / keep", "stem": "e-ie", "irreg": true}, {"inf": "leer", "en": "to read", "irreg": true}, {"inf": "caer", "en": "to fall", "irreg": true}, {"inf": "cambiar", "en": "to change"}, {"inf": "presentar", "en": "to present / introduce"}, {"inf": "crear", "en": "to create"}, {"inf": "abrir", "en": "to open", "irreg": true}, {"inf": "considerar", "en": "to consider"}, {"inf": "oír", "en": "to hear", "irreg": true}, {"inf": "acabar", "en": "to finish / end"}, {"inf": "ganar", "en": "to win / earn"}, {"inf": "formar", "en": "to form / shape"}, {"inf": "traer", "en": "to bring", "irreg": true}, {"inf": "partir", "en": "to depart / split"}, {"inf": "aceptar", "en": "to accept"}, {"inf": "realizar", "en": "to carry out / perform", "ortho": "zar"}, {"inf": "suponer", "en": "to suppose / assume", "irreg": true}, {"inf": "comprender", "en": "to comprehend / understand"}, {"inf": "lograr", "en": "to achieve / attain"}, {"inf": "explicar", "en": "to explain", "ortho": "car"}, {"inf": "preguntar", "en": "to ask a question"}, {"inf": "tocar", "en": "to touch / play an instrument", "ortho": "car"}, {"inf": "reconocer", "en": "to recognize", "ortho": "zco"}, {"inf": "estudiar", "en": "to study"}, {"inf": "alcanzar", "en": "to reach / overtake", "ortho": "zar"}, {"inf": "nacer", "en": "to be born", "ortho": "zco"}, {"inf": "dirigir", "en": "to direct / lead", "ortho": "jo"}, {"inf": "correr", "en": "to run"}, {"inf": "utilizar", "en": "to utilize / use", "ortho": "zar"}, {"inf": "pagar", "en": "to pay", "ortho": "gar"}, {"inf": "ayudar", "en": "to help / assist"}, {"inf": "gustar", "en": "to be pleasing / like"}, {"inf": "jugar", "en": "to play (sports/games)", "stem": "u-ue", "ortho": "gar"}, {"inf": "escuchar", "en": "to listen to"}, {"inf": "cumplir", "en": "to fulfill / accomplish"}, {"inf": "ofrecer", "en": "to offer", "ortho": "zco"}, {"inf": "descubrir", "en": "to discover", "irreg": true}, {"inf": "levantar", "en": "to raise / lift"}, {"inf": "intentar", "en": "to try / attempt"}, {"inf": "usar", "en": "to use"}, {"inf": "comprar", "en": "to buy"}, {"inf": "morir", "en": "to die", "stem": "o-ue", "irreg": true}, {"inf": "interesar", "en": "to interest"}, {"inf": "reunir", "en": "to gather / meet"}, {"inf": "permitir", "en": "to allow / permit"}, {"inf": "sugerir", "en": "to suggest", "stem": "e-ie"}, {"inf": "continuar", "en": "to continue"}, {"inf": "aprender", "en": "to learn"}, {"inf": "moverse", "en": "to move oneself"}, {"inf": "mover", "en": "to move (something)", "stem": "o-ue"}, {"inf": "dudar", "en": "to doubt"}, {"inf": "disfrutar", "en": "to enjoy"}, {"inf": "ensenar", "en": "to teach / show"}, {"inf": "enseñar", "en": "to teach / demonstrate"}, {"inf": "vender", "en": "to sell"}, {"inf": "viajar", "en": "to travel"}, {"inf": "caminar", "en": "to walk"}, {"inf": "responder", "en": "to answer / respond"}, {"inf": "construir", "en": "to build / construct", "irreg": true}, {"inf": "destruir", "en": "to destroy", "irreg": true}, {"inf": "diferenciar", "en": "to differentiate"}, {"inf": "analizar", "en": "to analyze", "ortho": "zar"}, {"inf": "desarrollar", "en": "to develop"}, {"inf": "organizar", "en": "to organize", "ortho": "zar"}, {"inf": "publicar", "en": "to publish", "ortho": "car"}, {"inf": "sostener", "en": "to hold / sustain", "stem": "e-ie", "irreg": true}, {"inf": "elegir", "en": "to choose / elect", "stem": "e-i", "ortho": "jo"}, {"inf": "observar", "en": "to observe"}, {"inf": "indicar", "en": "to indicate", "ortho": "car"}, {"inf": "revisar", "en": "to review / check"}, {"inf": "preparar", "en": "to prepare"}, {"inf": "diseñar", "en": "to design"}, {"inf": "evaluar", "en": "to evaluate"}, {"inf": "calificar", "en": "to grade / qualify", "ortho": "car"}, {"inf": "corregir", "en": "to correct", "stem": "e-i", "ortho": "jo"}, {"inf": "solicitar", "en": "to request / apply for"}, {"inf": "catalogar", "en": "to catalog", "ortho": "gar"}, {"inf": "archivar", "en": "to archive / file"}, {"inf": "consultar", "en": "to consult / query"}, {"inf": "preservar", "en": "to preserve"}, {"inf": "citar", "en": "to cite / quote"}, {"inf": "investigar", "en": "to investigate / research", "ortho": "gar"}, {"inf": "programar", "en": "to program / schedule"}, {"inf": "configurar", "en": "to configure / setup"}, {"inf": "instalar", "en": "to install"}, {"inf": "descargar", "en": "to download", "ortho": "gar"}, {"inf": "subir", "en": "to upload / go up"}, {"inf": "borrar", "en": "to delete / erase"}, {"inf": "conectar", "en": "to connect"}, {"inf": "actualizar", "en": "to update", "ortho": "zar"}, {"inf": "desbloquear", "en": "to unlock"}, {"inf": "cargar", "en": "to charge / load", "ortho": "gar"}, {"inf": "desconectar", "en": "to disconnect"}, {"inf": "apagar", "en": "to turn off", "ortho": "gar"}, {"inf": "encender", "en": "to turn on / ignite", "stem": "e-ie"}, {"inf": "filtrar", "en": "to filter"}, {"inf": "navegar", "en": "to navigate / browse", "ortho": "gar"}, {"inf": "indexar", "en": "to index"}, {"inf": "refinar", "en": "to refine"}, {"inf": "recuperar", "en": "to retrieve / recover"}, {"inf": "seleccionar", "en": "to select"}, {"inf": "examinar", "en": "to examine"}, {"inf": "iniciar", "en": "to initiate / start"}, {"inf": "sincronizar", "en": "to synchronize", "ortho": "zar"}, {"inf": "adjuntar", "en": "to attach"}, {"inf": "impartir", "en": "to deliver / impart"}, {"inf": "debatir", "en": "to debate"}, {"inf": "proyectar", "en": "to project"}, {"inf": "colaborar", "en": "to collaborate"}, {"inf": "redactar", "en": "to draft / write"}, {"inf": "entregar", "en": "to submit / turn in", "ortho": "gar"}, {"inf": "resumir", "en": "to summarize"}, {"inf": "fundamentar", "en": "to substantiate"}, {"inf": "matricular", "en": "to enroll / register"}, {"inf": "asistir", "en": "to attend / assist"}, {"inf": "aprobar", "en": "to pass / approve", "stem": "o-ue"}, {"inf": "suspender", "en": "to fail / suspend"}, {"inf": "graduar", "en": "to graduate"}, {"inf": "facilitar", "en": "to facilitate"}, {"inf": "guiar", "en": "to guide"}, {"inf": "motivar", "en": "to motivate"}, {"inf": "memorizar", "en": "to memorize", "ortho": "zar"}, {"inf": "sintetizar", "en": "to synthesize", "ortho": "zar"}, {"inf": "reflexionar", "en": "to reflect"}, {"inf": "aplicar", "en": "to apply", "ortho": "car"}, {"inf": "adquirir", "en": "to acquire", "stem": "i-ie"}, {"inf": "dominar", "en": "to master / dominate"}, {"inf": "comer", "en": "to eat"}, {"inf": "beber", "en": "to drink"}, {"inf": "dormir", "en": "to sleep", "stem": "o-ue", "irreg": true}, {"inf": "despertar", "en": "to wake up", "stem": "e-ie"}, {"inf": "vestir", "en": "to dress", "stem": "e-i"}, {"inf": "duchar", "en": "to shower"}, {"inf": "lavar", "en": "to wash"}, {"inf": "limpiar", "en": "to clean"}, {"inf": "cocinar", "en": "to cook"}, {"inf": "cantar", "en": "to sing"}, {"inf": "bailar", "en": "to dance"}, {"inf": "nadar", "en": "to swim"}, {"inf": "volar", "en": "to fly", "stem": "o-ue"}, {"inf": "manejar", "en": "to drive / handle"}, {"inf": "conducir", "en": "to drive / lead", "ortho": "zco", "irreg": true}, {"inf": "parar", "en": "to stop"}, {"inf": "cruzar", "en": "to cross", "ortho": "zar"}, {"inf": "bajar", "en": "to go down / lower"}, {"inf": "sonreír", "en": "to smile", "stem": "e-i", "irreg": true}, {"inf": "reír", "en": "to laugh", "stem": "e-i", "irreg": true}, {"inf": "llorar", "en": "to cry"}, {"inf": "gritar", "en": "to shout / yell"}, {"inf": "susurrar", "en": "to whisper"}, {"inf": "olvidar", "en": "to forget"}, {"inf": "soñar", "en": "to dream", "stem": "o-ue"}, {"inf": "desear", "en": "to desire / wish"}, {"inf": "amar", "en": "to love"}, {"inf": "adorar", "en": "to adore"}, {"inf": "odiar", "en": "to hate"}, {"inf": "detestar", "en": "to detest"}, {"inf": "soportar", "en": "to endure / tolerate"}, {"inf": "sufrir", "en": "to suffer"}, {"inf": "gozar", "en": "to enjoy / rel