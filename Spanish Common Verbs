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
        const verbsData = [{"inf": "ser", "en": "to be (essential/permanent)", "irreg": true}, {"inf": "estar", "en": "to be (location/state)", "irreg": true}, {"inf": "tener", "en": "to have / possess", "stem": "e-ie", "irreg": true}, {"inf": "hacer", "en": "to do / make", "irreg": true}, {"inf": "ir", "en": "to go", "irreg": true}, {"inf": "poder", "en": "to be able to / can", "stem": "o-ue", "irreg": true}, {"inf": "decir", "en": "to say / tell", "stem": "e-i", "irreg": true}, {"inf": "ver", "en": "to see / watch", "irreg": true}, {"inf": "dar", "en": "to give", "irreg": true}, {"inf": "saber", "en": "to know (facts/skills)", "irreg": true}, {"inf": "querer", "en": "to want / love", "stem": "e-ie", "irreg": true}, {"inf": "llegar", "en": "to arrive", "ortho": "gar"}, {"inf": "pasar", "en": "to pass / spend time / happen"}, {"inf": "deber", "en": "to owe / must"}, {"inf": "poner", "en": "to put / place", "irreg": true}, {"inf": "parecer", "en": "to seem / look like", "ortho": "zco"}, {"inf": "hablar", "en": "to speak / talk"}, {"inf": "quedar", "en": "to stay / remain / meet"}, {"inf": "seguir", "en": "to follow / continue", "stem": "e-i", "ortho": "gu"}, {"inf": "llevar", "en": "to carry / wear / take"}, {"inf": "dejar", "en": "to leave / let / allow"}, {"inf": "encontrar", "en": "to find", "stem": "o-ue"}, {"inf": "llamar", "en": "to call / name"}, {"inf": "venir", "en": "to come", "stem": "e-ie", "irreg": true}, {"inf": "pensar", "en": "to think", "stem": "e-ie"}, {"inf": "salir", "en": "to exit / go out", "irreg": true}, {"inf": "volver", "en": "to return / go back", "stem": "o-ue", "irreg": true}, {"inf": "tomar", "en": "to take / drink"}, {"inf": "conocer", "en": "to know (people/places)", "ortho": "zco"}, {"inf": "vivir", "en": "to live"}, {"inf": "sentir", "en": "to feel / regret", "stem": "e-ie"}, {"inf": "tratar", "en": "to treat / try"}, {"inf": "mirar", "en": "to look at / watch"}, {"inf": "contar", "en": "to count / tell a story", "stem": "o-ue"}, {"inf": "empezar", "en": "to start / begin", "stem": "e-ie", "ortho": "zar"}, {"inf": "esperar", "en": "to wait / hope / expect"}, {"inf": "buscar", "en": "to search / look for", "ortho": "car"}, {"inf": "existir", "en": "to exist"}, {"inf": "entrar", "en": "to enter / go in"}, {"inf": "trabajar", "en": "to work"}, {"inf": "escribir", "en": "to write", "irreg": true}, {"inf": "perder", "en": "to lose / miss", "stem": "e-ie"}, {"inf": "producir", "en": "to produce", "ortho": "zco", "irreg": true}, {"inf": "recordar", "en": "to remember", "stem": "o-ue"}, {"inf": "entender", "en": "to understand", "stem": "e-ie"}, {"inf": "pedir", "en": "to ask for / request", "stem": "e-i"}, {"inf": "recibir", "en": "to receive"}, {"inf": "comenzar", "en": "to commence / start", "stem": "e-ie", "ortho": "zar"}, {"inf": "servir", "en": "to serve", "stem": "e-i"}, {"inf": "sacar", "en": "to take out / remove", "ortho": "car"}, {"inf": "necesitar", "en": "to need"}, {"inf": "mantenerme", "en": "to maintain oneself"}, {"inf": "mantener", "en": "to maintain / keep", "stem": "e-ie", "irreg": true}, {"inf": "leer", "en": "to read", "irreg": true}, {"inf": "caer", "en": "to fall", "irreg": true}, {"inf": "cambiar", "en": "to change"}, {"inf": "presentar", "en": "to present / introduce"}, {"inf": "crear", "en": "to create"}, {"inf": "abrir", "en": "to open", "irreg": true}, {"inf": "considerar", "en": "to consider"}, {"inf": "oír", "en": "to hear", "irreg": true}, {"inf": "acabar", "en": "to finish / end"}, {"inf": "ganar", "en": "to win / earn"}, {"inf": "formar", "en": "to form / shape"}, {"inf": "traer", "en": "to bring", "irreg": true}, {"inf": "partir", "en": "to depart / split"}, {"inf": "aceptar", "en": "to accept"}, {"inf": "realizar", "en": "to carry out / perform", "ortho": "zar"}, {"inf": "suponer", "en": "to suppose / assume", "irreg": true}, {"inf": "comprender", "en": "to comprehend / understand"}, {"inf": "lograr", "en": "to achieve / attain"}, {"inf": "explicar", "en": "to explain", "ortho": "car"}, {"inf": "preguntar", "en": "to ask a question"}, {"inf": "tocar", "en": "to touch / play an instrument", "ortho": "car"}, {"inf": "reconocer", "en": "to recognize", "ortho": "zco"}, {"inf": "estudiar", "en": "to study"}, {"inf": "alcanzar", "en": "to reach / overtake", "ortho": "zar"}, {"inf": "nacer", "en": "to be born", "ortho": "zco"}, {"inf": "dirigir", "en": "to direct / lead", "ortho": "jo"}, {"inf": "correr", "en": "to run"}, {"inf": "utilizar", "en": "to utilize / use", "ortho": "zar"}, {"inf": "pagar", "en": "to pay", "ortho": "gar"}, {"inf": "ayudar", "en": "to help / assist"}, {"inf": "gustar", "en": "to be pleasing / like"}, {"inf": "jugar", "en": "to play (sports/games)", "stem": "u-ue", "ortho": "gar"}, {"inf": "escuchar", "en": "to listen to"}, {"inf": "cumplir", "en": "to fulfill / accomplish"}, {"inf": "ofrecer", "en": "to offer", "ortho": "zco"}, {"inf": "descubrir", "en": "to discover", "irreg": true}, {"inf": "levantar", "en": "to raise / lift"}, {"inf": "intentar", "en": "to try / attempt"}, {"inf": "usar", "en": "to use"}, {"inf": "comprar", "en": "to buy"}, {"inf": "morir", "en": "to die", "stem": "o-ue", "irreg": true}, {"inf": "interesar", "en": "to interest"}, {"inf": "reunir", "en": "to gather / meet"}, {"inf": "permitir", "en": "to allow / permit"}, {"inf": "sugerir", "en": "to suggest", "stem": "e-ie"}, {"inf": "continuar", "en": "to continue"}, {"inf": "aprender", "en": "to learn"}, {"inf": "moverse", "en": "to move oneself"}, {"inf": "mover", "en": "to move (something)", "stem": "o-ue"}, {"inf": "dudar", "en": "to doubt"}, {"inf": "disfrutar", "en": "to enjoy"}, {"inf": "ensenar", "en": "to teach / show"}, {"inf": "enseñar", "en": "to teach / demonstrate"}, {"inf": "vender", "en": "to sell"}, {"inf": "viajar", "en": "to travel"}, {"inf": "caminar", "en": "to walk"}, {"inf": "responder", "en": "to answer / respond"}, {"inf": "construir", "en": "to build / construct", "irreg": true}, {"inf": "destruir", "en": "to destroy", "irreg": true}, {"inf": "diferenciar", "en": "to differentiate"}, {"inf": "analizar", "en": "to analyze", "ortho": "zar"}, {"inf": "desarrollar", "en": "to develop"}, {"inf": "organizar", "en": "to organize", "ortho": "zar"}, {"inf": "publicar", "en": "to publish", "ortho": "car"}, {"inf": "sostener", "en": "to hold / sustain", "stem": "e-ie", "irreg": true}, {"inf": "elegir", "en": "to choose / elect", "stem": "e-i", "ortho": "jo"}, {"inf": "observar", "en": "to observe"}, {"inf": "indicar", "en": "to indicate", "ortho": "car"}, {"inf": "revisar", "en": "to review / check"}, {"inf": "preparar", "en": "to prepare"}, {"inf": "diseñar", "en": "to design"}, {"inf": "evaluar", "en": "to evaluate"}, {"inf": "calificar", "en": "to grade / qualify", "ortho": "car"}, {"inf": "corregir", "en": "to correct", "stem": "e-i", "ortho": "jo"}, {"inf": "solicitar", "en": "to request / apply for"}, {"inf": "catalogar", "en": "to catalog", "ortho": "gar"}, {"inf": "archivar", "en": "to archive / file"}, {"inf": "consultar", "en": "to consult / query"}, {"inf": "preservar", "en": "to preserve"}, {"inf": "citar", "en": "to cite / quote"}, {"inf": "investigar", "en": "to investigate / research", "ortho": "gar"}, {"inf": "programar", "en": "to program / schedule"}, {"inf": "configurar", "en": "to configure / setup"}, {"inf": "instalar", "en": "to install"}, {"inf": "descargar", "en": "to download", "ortho": "gar"}, {"inf": "subir", "en": "to upload / go up"}, {"inf": "borrar", "en": "to delete / erase"}, {"inf": "conectar", "en": "to connect"}, {"inf": "actualizar", "en": "to update", "ortho": "zar"}, {"inf": "desbloquear", "en": "to unlock"}, {"inf": "cargar", "en": "to charge / load", "ortho": "gar"}, {"inf": "desconectar", "en": "to disconnect"}, {"inf": "apagar", "en": "to turn off", "ortho": "gar"}, {"inf": "encender", "en": "to turn on / ignite", "stem": "e-ie"}, {"inf": "filtrar", "en": "to filter"}, {"inf": "navegar", "en": "to navigate / browse", "ortho": "gar"}, {"inf": "indexar", "en": "to index"}, {"inf": "refinar", "en": "to refine"}, {"inf": "recuperar", "en": "to retrieve / recover"}, {"inf": "seleccionar", "en": "to select"}, {"inf": "examinar", "en": "to examine"}, {"inf": "iniciar", "en": "to initiate / start"}, {"inf": "sincronizar", "en": "to synchronize", "ortho": "zar"}, {"inf": "adjuntar", "en": "to attach"}, {"inf": "impartir", "en": "to deliver / impart"}, {"inf": "debatir", "en": "to debate"}, {"inf": "proyectar", "en": "to project"}, {"inf": "colaborar", "en": "to collaborate"}, {"inf": "redactar", "en": "to draft / write"}, {"inf": "entregar", "en": "to submit / turn in", "ortho": "gar"}, {"inf": "resumir", "en": "to summarize"}, {"inf": "fundamentar", "en": "to substantiate"}, {"inf": "matricular", "en": "to enroll / register"}, {"inf": "asistir", "en": "to attend / assist"}, {"inf": "aprobar", "en": "to pass / approve", "stem": "o-ue"}, {"inf": "suspender", "en": "to fail / suspend"}, {"inf": "graduar", "en": "to graduate"}, {"inf": "facilitar", "en": "to facilitate"}, {"inf": "guiar", "en": "to guide"}, {"inf": "motivar", "en": "to motivate"}, {"inf": "memorizar", "en": "to memorize", "ortho": "zar"}, {"inf": "sintetizar", "en": "to synthesize", "ortho": "zar"}, {"inf": "reflexionar", "en": "to reflect"}, {"inf": "aplicar", "en": "to apply", "ortho": "car"}, {"inf": "adquirir", "en": "to acquire", "stem": "i-ie"}, {"inf": "dominar", "en": "to master / dominate"}, {"inf": "comer", "en": "to eat"}, {"inf": "beber", "en": "to drink"}, {"inf": "dormir", "en": "to sleep", "stem": "o-ue", "irreg": true}, {"inf": "despertar", "en": "to wake up", "stem": "e-ie"}, {"inf": "vestir", "en": "to dress", "stem": "e-i"}, {"inf": "duchar", "en": "to shower"}, {"inf": "lavar", "en": "to wash"}, {"inf": "limpiar", "en": "to clean"}, {"inf": "cocinar", "en": "to cook"}, {"inf": "cantar", "en": "to sing"}, {"inf": "bailar", "en": "to dance"}, {"inf": "nadar", "en": "to swim"}, {"inf": "volar", "en": "to fly", "stem": "o-ue"}, {"inf": "manejar", "en": "to drive / handle"}, {"inf": "conducir", "en": "to drive / lead", "ortho": "zco", "irreg": true}, {"inf": "parar", "en": "to stop"}, {"inf": "cruzar", "en": "to cross", "ortho": "zar"}, {"inf": "bajar", "en": "to go down / lower"}, {"inf": "sonreír", "en": "to smile", "stem": "e-i", "irreg": true}, {"inf": "reír", "en": "to laugh", "stem": "e-i", "irreg": true}, {"inf": "llorar", "en": "to cry"}, {"inf": "gritar", "en": "to shout / yell"}, {"inf": "susurrar", "en": "to whisper"}, {"inf": "olvidar", "en": "to forget"}, {"inf": "soñar", "en": "to dream", "stem": "o-ue"}, {"inf": "desear", "en": "to desire / wish"}, {"inf": "amar", "en": "to love"}, {"inf": "adorar", "en": "to adore"}, {"inf": "odiar", "en": "to hate"}, {"inf": "detestar", "en": "to detest"}, {"inf": "soportar", "en": "to endure / tolerate"}, {"inf": "sufrir", "en": "to suffer"}, {"inf": "gozar", "en": "to enjoy / relish", "ortho": "zar"}, {"inf": "celebrar", "en": "to celebrate"}, {"inf": "felicitar", "en": "to congratulate"}, {"inf": "invitar", "en": "to invite"}, {"inf": "visitar", "en": "to visit"}, {"inf": "acompañar", "en": "to accompany"}, {"inf": "proteger", "en": "to protect", "ortho": "jo"}, {"inf": "defender", "en": "to defend", "stem": "e-ie"}, {"inf": "atacar", "en": "to attack", "ortho": "car"}, {"inf": "luchar", "en": "to fight / struggle"}, {"inf": "empatar", "en": "to tie (sports)"}, {"inf": "competir", "en": "to compete", "stem": "e-i"}, {"inf": "entrenar", "en": "to train / practice"}, {"inf": "practicar", "en": "to practice", "ortho": "car"}, {"inf": "mejorar", "en": "to improve"}, {"inf": "empeorar", "en": "to worsen"}, {"inf": "aumentar", "en": "to increase"}, {"inf": "reducir", "en": "to reduce", "ortho": "zco", "irreg": true}, {"inf": "disminuir", "en": "to diminish", "irreg": true}, {"inf": "crecer", "en": "to grow", "ortho": "zco"}, {"inf": "avanzar", "en": "to advance", "ortho": "zar"}, {"inf": "retroceder", "en": "to recede / go back"}, {"inf": "detener", "en": "to stop / detain", "stem": "e-ie", "irreg": true}, {"inf": "terminar", "en": "to terminate / finish"}, {"inf": "concluir", "en": "to conclude", "irreg": true}, {"inf": "finalizar", "en": "to finalize", "ortho": "zar"}, {"inf": "gastar", "en": "to spend (money/energy)"}, {"inf": "ahorrar", "en": "to save (money)"}, {"inf": "invertir", "en": "to invest", "stem": "e-ie"}, {"inf": "costar", "en": "to cost", "stem": "o-ue"}, {"inf": "valer", "en": "to be worth", "irreg": true}, {"inf": "cobrar", "en": "to charge / collect money"}, {"inf": "donar", "en": "to donate"}, {"inf": "prestar", "en": "to lend"}, {"inf": "devolver", "en": "to return (an object)", "stem": "o-ue", "irreg": true}, {"inf": "regalar", "en": "to give a gift"}, {"inf": "alquilar", "en": "to rent"}, {"inf": "firmar", "en": "to sign"}, {"inf": "votar", "en": "to vote"}, {"inf": "gobernar", "en": "to govern", "stem": "e-ie"}, {"inf": "administrar", "en": "to administer / manage"}, {"inf": "gestionar", "en": "to manage / conduct"}, {"inf": "ejecutar", "en": "to execute / perform"}, {"inf": "planear", "en": "to plan"}, {"inf": "presupuestar", "en": "to budget"}, {"inf": "calcular", "en": "to calculate"}, {"inf": "medir", "en": "to measure", "stem": "e-i"}, {"inf": "pesar", "en": "to weigh"}, {"inf": "sumar", "en": "to add / sum"}, {"inf": "restar", "en": "to subtract"}, {"inf": "multiplicar", "en": "to multiply", "ortho": "car"}, {"inf": "dividir", "en": "to divide"}, {"inf": "distribuir", "en": "to distribute", "irreg": true}, {"inf": "compartir", "en": "to share"}, {"inf": "difundir", "en": "to spread / broadcast"}, {"inf": "comunicar", "en": "to communicate", "ortho": "car"}, {"inf": "expresar", "en": "to express"}, {"inf": "manifestar", "en": "to manifest / show", "stem": "e-ie"}, {"inf": "declarar", "en": "to declare"}, {"inf": "afirmar", "en": "to affirm / state"}, {"inf": "negar", "en": "to deny", "stem": "e-ie", "ortho": "gar"}, {"inf": "admitir", "en": "to admit"}, {"inf": "confesar", "en": "to confess", "stem": "e-ie"}, {"inf": "prometer", "en": "to promise"}, {"inf": "jurar", "en": "to swear / vow"}, {"inf": "garantizar", "en": "to guarantee", "ortho": "zar"}, {"inf": "asegurar", "en": "to assure / ensure"}, {"inf": "advertir", "en": "to warn / notice", "stem": "e-ie"}, {"inf": "aconsejar", "en": "to advise"}, {"inf": "recomendar", "en": "to recommend", "stem": "e-ie"}, {"inf": "ordenar", "en": "to order / arrange"}, {"inf": "anunciar", "en": "to announce"}, {"inf": "apoyar", "en": "to support"}, {"inf": "aprovechar", "en": "to take advantage of"}, {"inf": "asumir", "en": "to assume"}, {"inf": "atender", "en": "to attend to"}, {"inf": "atraer", "en": "to attract"}, {"inf": "autorizar", "en": "to authorize"}, {"inf": "averiguar", "en": "to find out"}, {"inf": "bloquear", "en": "to block"}, {"inf": "calmar", "en": "to calm"}, {"inf": "cancelar", "en": "to cancel"}, {"inf": "capturar", "en": "to capture"}, {"inf": "causar", "en": "to cause"}, {"inf": "cerrar", "en": "to close"}, {"inf": "colocar", "en": "to place / position"}, {"inf": "comparar", "en": "to compare"}, {"inf": "comprobar", "en": "to verify / check"}, {"inf": "conceder", "en": "to grant"}, {"inf": "confirmar", "en": "to confirm"}, {"inf": "confundir", "en": "to confuse"}, {"inf": "conseguir", "en": "to obtain / get"}, {"inf": "acusar", "en": "to accuse"}, {"inf": "adaptar", "en": "to adapt"}, {"inf": "admirar", "en": "to admire"}, {"inf": "adoptar", "en": "to adopt"}, {"inf": "afectar", "en": "to affect"}, {"inf": "agradecer", "en": "to thank / be grateful"}, {"inf": "agregar", "en": "to add"}, {"inf": "aguantar", "en": "to endure / stand"}, {"inf": "almorzar", "en": "to eat lunch"}, {"inf": "alterar", "en": "to alter"}, {"inf": "alumbrar", "en": "to illuminate"}, {"inf": "amenazar", "en": "to threaten"}, {"inf": "anotar", "en": "to write down"}, {"inf": "anticipar", "en": "to anticipate"}, {"inf": "aparecer", "en": "to appear"}, {"inf": "aplazar", "en": "to postpone"}, {"inf": "apreciar", "en": "to appreciate"}, {"inf": "arrancar", "en": "to pull out / start (engine)"}, {"inf": "arreglar", "en": "to fix / arrange"}, {"inf": "arriesgar", "en": "to risk"}, {"inf": "atravesar", "en": "to cross through"}, {"inf": "avisar", "en": "to notify / warn"}, {"inf": "banear", "en": "to ban"}, {"inf": "bautizar", "en": "to baptize"}, {"inf": "brillar", "en": "to shine"}, {"inf": "brincar", "en": "to jump / hop"}, {"inf": "brindar", "en": "to offer / toast"}, {"inf": "burlar", "en": "to mock / evade"}, {"inf": "calentar", "en": "to heat up"}, {"inf": "casar", "en": "to marry"}, {"inf": "castigar", "en": "to punish"}, {"inf": "cenar", "en": "to eat dinner"}, {"inf": "cepillar", "en": "to brush"}, {"inf": "chatear", "en": "to chat online"}, {"inf": "chocar", "en": "to crash / collide"}, {"inf": "circular", "en": "to circulate"}, {"inf": "clasificar", "en": "to classify"}, {"inf": "coleccionar", "en": "to collect"}, {"inf": "combinar", "en": "to combine"}, {"inf": "comentar", "en": "to comment"}, {"inf": "comprometer", "en": "to compromise / commit"}, {"inf": "concentrar", "en": "to concentrate"}, {"inf": "condenar", "en": "to condemn"}, {"inf": "congelar", "en": "to freeze"}, {"inf": "conservar", "en": "to conserve"}, {"inf": "consistir", "en": "to consist"}, {"inf": "contestar", "en": "to answer"}, {"inf": "contratar", "en": "to hire"}, {"inf": "controlar", "en": "to control"}, {"inf": "conversar", "en": "to converse"}, {"inf": "convencer", "en": "to convince"}, {"inf": "convocar", "en": "to convene / call"}, {"inf": "copiar", "en": "to copy"}, {"inf": "cortar", "en": "to cut"}, {"inf": "creer", "en": "to believe"}, {"inf": "cubrir", "en": "to cover"}, {"inf": "cuidar", "en": "to take care of"}, {"inf": "culpar", "en": "to blame"}, {"inf": "dañar", "en": "to damage"}, {"inf": "decidir", "en": "to decide"}, {"inf": "decorar", "en": "to decorate"}, {"inf": "dedicar", "en": "to dedicate"}, {"inf": "definir", "en": "to define"}, {"inf": "demostrar", "en": "to demonstrate"}, {"inf": "denunciar", "en": "to report / denounce"}, {"inf": "depender", "en": "to depend"}, {"inf": "depositar", "en": "to deposit"}, {"inf": "derramar", "en": "to spill"}, {"inf": "desaparecer", "en": "to disappear"}, {"inf": "desayunar", "en": "to eat breakfast"}, {"inf": "descansar", "en": "to rest"}, {"inf": "describir", "en": "to describe"}, {"inf": "desempeñar", "en": "to execute / perform"}, {"inf": "disparar", "en": "to shoot"}, {"inf": "durar", "en": "to last / endure"}, {"inf": "ejercer", "en": "to exercise / practice a profession"}, {"inf": "elaborar", "en": "to elaborate / prepare"}, {"inf": "eliminar", "en": "to eliminate"}, {"inf": "empaquetar", "en": "to pack"}, {"inf": "emplear", "en": "to employ / use"}, {"inf": "encargar", "en": "to order / entrust"}, {"inf": "enfrentar", "en": "to face / confront"}, {"inf": "engañar", "en": "to deceive"}, {"inf": "enviar", "en": "to send"}, {"inf": "escapar", "en": "to escape"}, {"inf": "escoger", "en": "to choose"}, {"inf": "esconder", "en": "to hide"}, {"inf": "establecer", "en": "to establish"}, {"inf": "evitar", "en": "to avoid"}, {"inf": "exigir", "en": "to demand"}, {"inf": "fabricar", "en": "to manufacture"}, {"inf": "falta", "en": "to lack"}, {"inf": "fallecer", "en": "to pass away"}, {"inf": "fascinar", "en": "to fascinate"}, {"inf": "fijar", "en": "to fix / set"}, {"inf": "fracasar", "en": "to fail"}, {"inf": "frenar", "en": "to brake / slow down"}, {"inf": "generar", "en": "to generate"}, {"inf": "golpear", "en": "to hit / knock"}, {"inf": "grabar", "en": "to record / engrave"}, {"inf": "hallar", "en": "to find"}, {"inf": "hervir", "en": "to boil"}, {"inf": "huir", "en": "to flee / escape"}, {"inf": "ilustrar", "en": "to illustrate"}, {"inf": "imaginar", "en": "to imagine"}, {"inf": "impedir", "en": "to prevent"}, {"inf": "imprimir", "en": "to print"}, {"inf": "incluir", "en": "to include"}, {"inf": "informar", "en": "to inform"}, {"inf": "insistir", "en": "to insist"}, {"inf": "interrumpir", "en": "to interrupt"}, {"inf": "introducir", "en": "to introduce / insert"}, {"inf": "inventar", "en": "to invent"}, {"inf": "lamentar", "en": "to regret"}, {"inf": "lanzar", "en": "to throw / launch"}, {"inf": "llenar", "en": "to fill"}, {"inf": "mandar", "en": "to command / send"}, {"inf": "marcar", "en": "to mark / dial"}, {"inf": "matar", "en": "to kill"}, {"inf": "mencionar", "en": "to mention"}, {"inf": "mentir", "en": "to lie"}, {"inf": "merecer", "en": "to deserve"}, {"inf": "mezclar", "en": "to mix"}, {"inf": "molestar", "en": "to bother"}, {"inf": "montar", "en": "to ride / mount"}, {"inf": "mostrar", "en": "to show"}, {"inf": "nacimiento", "en": "to be born"}, {"inf": "negociar", "en": "to negotiate"}, {"inf": "notar", "en": "to notice"}, {"inf": "obtener", "en": "to obtain"}, {"inf": "ocultar", "en": "to hide"}, {"inf": "ocupar", "en": "to occupy"}, {"inf": "ocurrir", "en": "to happen"}, {"inf": "operar", "en": "to operate"}, {"inf": "participar", "en": "to participate"}, {"inf": "percibir", "en": "to perceive"}, {"inf": "perdonar", "en": "to forgive"}, {"inf": "perseguir", "en": "to pursue"}, {"inf": "pescar", "en": "to fish"}, {"inf": "plantear", "en": "to pose / suggest"}, {"inf": "posibilitar", "en": "to make possible"}, {"inf": "precisar", "en": "to specify / require"}, {"inf": "preferir", "en": "to prefer"}, {"inf": "probar", "en": "to try / test"}, {"inf": "prohibir", "en": "to prohibit"}, {"inf": "pronunciar", "en": "to pronounce"}, {"inf": "proponer", "en": "to propose"}, {"inf": "quejar", "en": "to complain"}, {"inf": "quitar", "en": "to remove / take off"}, {"inf": "recoger", "en": "to pick up"}, {"inf": "referir", "en": "to refer"}, {"inf": "reflejar", "en": "to reflect"}, {"inf": "regresar", "en": "to return"}, {"inf": "relacionar", "en": "to relate"}, {"inf": "renovar", "en": "to renew"}, {"inf": "reparar", "en": "to repair"}, {"inf": "repetir", "en": "to repeat"}, {"inf": "representar", "en": "to represent"}, {"inf": "resolver", "en": "to resolve"}, {"inf": "restablecer", "en": "to restore"}, {"inf": "romper", "en": "to break"}, {"inf": "sacrificar", "en": "to sacrifice"}, {"inf": "saltar", "en": "to jump"}, {"inf": "saludar", "en": "to greet"}, {"inf": "satisfacer", "en": "to satisfy"}, {"inf": "secar", "en": "to dry"}, {"inf": "sentar", "en": "to sit"}, {"inf": "separar", "en": "to separate"}, {"inf": "significar", "en": "to mean"}, {"inf": "simular", "en": "to simulate"}, {"inf": "solucionar", "en": "to solve"}, {"inf": "sorprender", "en": "to surprise"}, {"inf": "suscibir", "en": "to subscribe"}, {"inf": "suspendes", "en": "to fail / suspend"}, {"inf": "sustituir", "en": "to substitute"}, {"inf": "tardar", "en": "to delay / take time"}, {"inf": "teclear", "en": "to type"}, {"inf": "temer", "en": "to fear"}, {"inf": "tirar", "en": "to throw / pull"}, {"inf": "traducir", "en": "to translate"}, {"inf": "transformar", "en": "to transform"}, {"inf": "transmitir", "en": "to transmit"}, {"inf": "triunfar", "en": "to triumph"}, {"inf": "ubicar", "en": "to locate"}, {"inf": "unir", "en": "to join / unite"}, {"inf": "vaciar", "en": "to empty"}, {"inf": "variar", "en": "to vary"}, {"inf": "vencer", "en": "to defeat / overcome"}, {"inf": "verificar", "en": "to verify"}, {"inf": "acostarse", "en": "to go to bed"}, {"inf": "despertarse", "en": "to wake up"}, {"inf": "afeitarse", "en": "to shave"}, {"inf": "divertirse", "en": "to have fun"}, {"inf": "preocuparse", "en": "to worry"}, {"inf": "quejarse", "en": "to complain"}, {"inf": "acostumbrar", "en": "to accustom"}, {"inf": "acontecer", "en": "to happen"}];

        const pronouns = [
            "yo",
            "tú",
            "él / ella / usted",
            "nosotros / nosotras",
            "vosotros / vosotras",
            "ellos / ellas / ustedes"
        ];

        const tenses = [
            "Presente",
            "Pretérito Indefinido",
            "Pretérito Imperfecto",
            "Futuro Simple",
            "Futuro Informal",
            "Presente de Subjuntivo"
        ];

        // Specific irregular tables for major irregular verbs
        const irregulars = {
            "ser": {
                "Presente": ["soy", "eres", "es", "somos", "sois", "son"],
                "Pretérito Indefinido": ["fui", "fuiste", "fue", "fuimos", "fuisteis", "fueron"],
                "Pretérito Imperfecto": ["era", "eras", "era", "éramos", "erais", "eran"],
                "Futuro Simple": ["seré", "serás", "será", "seremos", "seréis", "serán"],
                "Presente de Subjuntivo": ["sea", "seas", "sea", "seamos", "seáis", "sean"]
            },
            "estar": {
                "Presente": ["estoy", "estás", "está", "estamos", "estáis", "están"],
                "Pretérito Indefinido": ["estuve", "estuviste", "estuvo", "estuvimos", "estuvisteis", "estuvieron"],
                "Pretérito Imperfecto": ["estaba", "estabas", "estaba", "estábamos", "estabais", "estaban"],
                "Futuro Simple": ["estaré", "estarás", "estará", "estaremos", "estaréis", "estarán"],
                "Presente de Subjuntivo": ["esté", "estés", "esté", "estemos", "estéis", "estén"]
            },
            "ir": {
                "Presente": ["voy", "vas", "va", "vamos", "vais", "van"],
                "Pretérito Indefinido": ["fui", "fuiste", "fue", "fuimos", "fuisteis", "fueron"],
                "Pretérito Imperfecto": ["iba", "ibas", "iba", "íbamos", "ibais", "iban"],
                "Futuro Simple": ["iré", "irás", "irá", "iremos", "iréis", "irán"],
                "Presente de Subjuntivo": ["vaya", "vayas", "vaya", "vayamos", "vayáis", "vayan"]
            },
            "tener": {
                "Presente": ["tengo", "tienes", "tiene", "tenemos", "tenéis", "tienen"],
                "Pretérito Indefinido": ["tuve", "tuviste", "tuvo", "tuvimos", "tuvisteis", "tuvieron"],
                "Futuro Simple": ["tendré", "tendrás", "tendrá", "tendremos", "tendréis", "tendrán"],
                "Presente de Subjuntivo": ["tenga", "tengas", "tenga", "tengamos", "tengáis", "tengan"]
            },
            "hacer": {
                "Presente": ["hago", "haces", "hace", "hacemos", "hacéis", "hacen"],
                "Pretérito Indefinido": ["hice", "hiciste", "hizo", "hicimos", "hicisteis", "hicieron"],
                "Futuro Simple": ["haré", "harás", "hará", "haremos", "haréis", "harán"],
                "Presente de Subjuntivo": ["haga", "hagas", "haga", "hagamos", "hagáis", "hagan"]
            },
            "poder": {
                "Presente": ["puedo", "puedes", "puede", "podemos", "podéis", "pueden"],
                "Pretérito Indefinido": ["pude", "pudiste", "pudo", "pudimos", "pudisteis", "pudieron"],
                "Futuro Simple": ["podré", "podrás", "podrá", "podremos", "podréis", "podrán"],
                "Presente de Subjuntivo": ["pueda", "puedas", "pueda", "podamos", "podáis", "puedan"]
            },
            "saber": {
                "Presente": ["sé", "sabes", "sabe", "sabemos", "sabéis", "saben"],
                "Pretérito Indefinido": ["supe", "supiste", "supo", "supimos", "supisteis", "supieron"],
                "Futuro Simple": ["sabré", "sabrás", "sabrá", "sabremos", "sabréis", "sabrán"],
                "Presente de Subjuntivo": ["sepa", "sepas", "sepa", "sepamos", "sepáis", "sepan"]
            },
            "decir": {
                "Presente": ["digo", "dices", "dice", "decimos", "decís", "dicen"],
                "Pretérito Indefinido": ["dije", "dijiste", "dijo", "dijimos", "dijisteis", "dijeron"],
                "Futuro Simple": ["diré", "dirás", "dirá", "diremos", "diréis", "dirán"],
                "Presente de Subjuntivo": ["diga", "digas", "diga", "digamos", "digáis", "digan"]
            },
            "querer": {
                "Presente": ["quiero", "quieres", "quiere", "queremos", "queréis", "quieren"],
                "Pretérito Indefinido": ["quise", "quisiste", "quiso", "quisimos", "quisisteis", "quisieron"],
                "Futuro Simple": ["querré", "querrás", "querrá", "querremos", "querréis", "querrán"],
                "Presente de Subjuntivo": ["quiera", "quieras", "quiera", "queramos", "queráis", "quieran"]
            },
            "poner": {
                "Presente": ["pongo", "pones", "pone", "ponemos", "ponéis", "ponen"],
                "Pretérito Indefinido": ["puse", "pusiste", "puso", "pusimos", "pusisteis", "pusieron"],
                "Futuro Simple": ["pondré", "pondrás", "pondrá", "pondremos", "pondréis", "pondrán"],
                "Presente de Subjuntivo": ["ponga", "pongas", "ponga", "pongamos", "pongáis", "pongan"]
            },
            "ver": {
                "Presente": ["veo", "ves", "ve", "vemos", "veis", "ven"],
                "Pretérito Indefinido": ["vi", "viste", "vio", "vimos", "visteis", "vieron"],
                "Pretérito Imperfecto": ["veía", "veías", "veía", "veíamos", "veíais", "veían"],
                "Presente de Subjuntivo": ["vea", "veas", "vea", "veamos", "veáis", "vean"]
            },
            "dar": {
                "Presente": ["doy", "das", "da", "damos", "dais", "dan"],
                "Pretérito Indefinido": ["di", "diste", "dio", "dimos", "disteis", "dieron"],
                "Presente de Subjuntivo": ["dé", "des", "dé", "demos", "deis", "den"]
            },
            "venir": {
                "Presente": ["vengo", "vienes", "viene", "venimos", "venís", "vienen"],
                "Pretérito Indefinido": ["vine", "viniste", "vino", "vinimos", "vinisteis", "vinieron"],
                "Futuro Simple": ["vendré", "vendrás", "vendrá", "vendremos", "vendréis", "vendrán"],
                "Presente de Subjuntivo": ["venga", "vengas", "venga", "vengamos", "vengáis", "vengan"]
            },
            "salir": {
                "Presente": ["salgo", "sales", "sale", "salimos", "salís", "salen"],
                "Futuro Simple": ["saldré", "saldrás", "saldrá", "saldremos", "saldréis", "saldrán"],
                "Presente de Subjuntivo": ["salga", "salgas", "salga", "salgamos", "salgáis", "salgan"]
            }
        };

        // Algorithmic Conjugator Engine
        function conjugate(verbObj, personIdx, tense) {
            const inf = verbObj.inf;
            const stemType = verbObj.stem; // e-ie, o-ue, e-i, etc.
            
            // 1. Check direct irregular override
            if (irregulars[inf] && irregulars[inf][tense]) {
                return irregulars[inf][tense][personIdx];
            }

            // Helper: Extract stem and ending
            let ending = inf.slice(-2);
            let stem = inf.slice(0, -2);

            // 2. Futuro Informal (Ir a + infinitivo)
            if (tense === "Futuro Informal") {
                const irPres = ["voy a", "vas a", "va a", "vamos a", "vais a", "van a"];
                return `${irPres[personIdx]} ${inf}`;
            }

            // 3. Futuro Simple
            if (tense === "Futuro Simple") {
                const futEndings = ["é", "ás", "á", "emos", "éis", "án"];
                let futStem = inf;
                if (inf.endsWith("ner") || inf.endsWith("lir") || inf.endsWith("nir")) {
                    futStem = inf.slice(0, -2) + "dr";
                }
                return futStem + futEndings[personIdx];
            }

            // 4. Pretérito Imperfecto
            if (tense === "Pretérito Imperfecto") {
                if (ending === "ar") {
                    const impAr = ["aba", "abas", "aba", "ábamos", "abais", "aban"];
                    return stem + impAr[personIdx];
                } else {
                    const impErIr = ["ía", "ías", "ía", "íamos", "íais", "ían"];
                    return stem + impErIr[personIdx];
                }
            }

            // 5. Pretérito Indefinido
            if (tense === "Pretérito Indefinido") {
                if (ending === "ar") {
                    const pretAr = ["é", "aste", "ó", "amos", "asteis", "aron"];
                    // Orthographic tweaks for 1st person
                    if (personIdx === 0) {
                        if (stem.endsWith("c")) return stem.slice(0,-1) + "qué";
                        if (stem.endsWith("g")) return stem.slice(0,-1) + "gué";
                        if (stem.endsWith("z")) return stem.slice(0,-1) + "cé";
                    }
                    return stem + pretAr[personIdx];
                } else {
                    const pretErIr = ["í", "iste", "ió", "imos", "isteis", "ieron"];
                    return stem + pretErIr[personIdx];
                }
            }

            // Apply stem-change logic for Presente & Presente de Subjuntivo
            let presStem = stem;
            if (stemType && (personIdx < 3 || personIdx === 5)) {
                if (stemType === "e-ie") {
                    let lastE = stem.lastIndexOf("e");
                    if (lastE !== -1) presStem = stem.slice(0, lastE) + "ie" + stem.slice(lastE + 1);
                } else if (stemType === "o-ue") {
                    let lastO = stem.lastIndexOf("o");
                    if (lastO !== -1) presStem = stem.slice(0, lastO) + "ue" + stem.slice(lastO + 1);
                } else if (stemType === "e-i") {
                    let lastE = stem.lastIndexOf("e");
                    if (lastE !== -1) presStem = stem.slice(0, lastE) + "i" + stem.slice(lastE + 1);
                } else if (stemType === "u-ue") {
                    let lastU = stem.lastIndexOf("u");
                    if (lastU !== -1) presStem = stem.slice(0, lastU) + "ue" + stem.slice(lastU + 1);
                }
            }

            // 6. Presente
            if (tense === "Presente") {
                if (ending === "ar") {
                    const arEnd = ["o", "as", "a", "amos", "áis", "an"];
                    return presStem + arEnd[personIdx];
                } else if (ending === "er") {
                    const erEnd = ["o", "es", "e", "emos", "éis", "en"];
                    return presStem + erEnd[personIdx];
                } else {
                    const irEnd = ["o", "es", "e", "imos", "ís", "en"];
                    return presStem + irEnd[personIdx];
                }
            }

            // 7. Presente de Subjuntivo
            if (tense === "Presente de Subjuntivo") {
                if (ending === "ar") {
                    const subjAr = ["e", "es", "e", "emos", "éis", "en"];
                    return presStem + subjAr[personIdx];
                } else {
                    const subjErIr = ["a", "as", "a", "amos", "áis", "an"];
                    return presStem + subjErIr[personIdx];
                }
            }

            return `${presStem}${ending}`;
        }

        // Generate Flashcards Database dynamically
        let allCards = [];
        let filteredDeck = [];
        let currentIndex = 0;

        function buildDatabase() {
            allCards = [];
            verbsData.forEach(v => {
                tenses.forEach(tense => {
                    for (let pIdx = 0; pIdx < 6; pIdx++) {
                        const conj = conjugate(v, pIdx, tense);
                        allCards.push({
                            verb: v.inf,
                            en: v.en,
                            tense: tense,
                            personIdx: pIdx,
                            pronoun: pronouns[pIdx],
                            conj: conj
                        });
                    }
                });
            });
            filteredDeck = [...allCards];
            shuffleDeck();
        }

        function updateDisplay() {
            if (filteredDeck.length === 0) {
                document.getElementById("front-verb").textContent = "No matches";
                document.getElementById("front-prompt-details").textContent = "Adjust filter parameters";
                document.getElementById("front-meaning").textContent = "";
                document.getElementById("counter").textContent = "0 of 0";
                return;
            }

            const card = filteredDeck[currentIndex];

            document.getElementById("front-verb").textContent = card.verb;
            document.getElementById("front-prompt-details").textContent = card.pronoun;
            document.getElementById("front-meaning").textContent = `(${card.en})`;
            document.getElementById("front-tense").textContent = card.tense;
            document.getElementById("front-person").textContent = `Person #${card.personIdx + 1}`;

            document.getElementById("back-conjugation").textContent = card.conj;
            document.getElementById("back-translation").textContent = `${card.pronoun} + ${card.verb} (${card.tense})`;
            document.getElementById("back-tense").textContent = card.tense;
            document.getElementById("back-person").textContent = card.pronoun;
            document.getElementById("back-hint").textContent = `Base Infinitive: ${card.verb} | English: ${card.en}`;

            document.getElementById("counter").textContent = `Combination ${currentIndex + 1} of ${filteredDeck.length}`;

            const cardEl = document.getElementById("flashcard");
            if (cardEl.classList.contains("is-flipped")) {
                cardEl.classList.remove("is-flipped");
            }
        }

        function flipCard() {
            if (filteredDeck.length > 0) {
                document.getElementById("flashcard").classList.toggle("is-flipped");
            }
        }

        function nextCard() {
            if (filteredDeck.length === 0) return;
            currentIndex = (currentIndex + 1) % filteredDeck.length;
            updateDisplay();
        }

        function prevCard() {
            if (filteredDeck.length === 0) return;
            currentIndex = (currentIndex - 1 + filteredDeck.length) % filteredDeck.length;
            updateDisplay();
        }

        function shuffleDeck() {
            for (let i = filteredDeck.length - 1; i > 0; i--) {
                const j = Math.floor(Math.random() * (i + 1));
                [filteredDeck[i], filteredDeck[j]] = [filteredDeck[j], filteredDeck[i]];
            }
            currentIndex = 0;
            updateDisplay();
        }

        function applyFilters() {
            const selectedTense = document.getElementById("tenseFilter").value;
            const selectedPerson = document.getElementById("personFilter").value;
            const searchTerm = document.getElementById("verbSearch").value.trim().toLowerCase();

            filteredDeck = allCards.filter(c => {
                const tenseMatch = (selectedTense === "All" || c.tense === selectedTense);
                const personMatch = (selectedPerson === "All" || c.personIdx.toString() === selectedPerson);
                const verbMatch = (searchTerm === "" || c.verb.toLowerCase().includes(searchTerm) || c.en.toLowerCase().includes(searchTerm));
                return tenseMatch && personMatch && verbMatch;
            });

            currentIndex = 0;
            updateDisplay();
        }

        document.addEventListener('keydown', function(e) {
            if (e.key === 'ArrowRight') {
                nextCard();
            } else if (e.key === 'ArrowLeft') {
                prevCard();
            } else if (e.key === ' ' || e.key === 'ArrowUp' || e.key === 'ArrowDown') {
                e.preventDefault();
                flipCard();
            }
        });

        buildDatabase();
    </script>
</body>
</html>
