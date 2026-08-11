<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Academic & IT Spanish Vocabulary</title>
    <style>
        :root {
            --primary: #2c3e50;
            --secondary: #34495e;
            --accent: #3498db;
            --light: #ecf0f1;
            --white: #ffffff;
        }
        body {
            font-family: 'Segoe UI', Tahoma, Geneva, Verdana, sans-serif;
            background-color: var(--light);
            color: var(--primary);
            display: flex;
            flex-direction: column;
            align-items: center;
            padding: 2rem;
            margin: 0;
        }
        h1 {
            text-align: center;
            color: var(--primary);
            margin-bottom: 0.5rem;
        }
        .controls {
            margin-bottom: 2rem;
            display: flex;
            gap: 1rem;
        }
        button, select {
            padding: 0.5rem 1rem;
            font-size: 1rem;
            border: none;
            border-radius: 4px;
            cursor: pointer;
            background-color: var(--accent);
            color: var(--white);
            transition: background-color 0.3s ease;
        }
        button:hover, select:hover {
            background-color: #2980b9;
        }
        .flashcard-container {
            width: 100%;
            max-width: 500px;
            height: 300px;
            perspective: 1000px;
            margin-bottom: 2rem;
        }
        .flashcard {
            width: 100%;
            height: 100%;
            position: relative;
            transition: transform 0.6s;
            transform-style: preserve-3d;
            cursor: pointer;
            box-shadow: 0 4px 8px rgba(0,0,0,0.1);
            border-radius: 12px;
        }
        .flashcard.is-flipped {
            transform: rotateY(180deg);
        }
        .flashcard-face {
            position: absolute;
            width: 100%;
            height: 100%;
            -webkit-backface-visibility: hidden;
            backface-visibility: hidden;
            display: flex;
            flex-direction: column;
            justify-content: center;
            align-items: center;
            background-color: var(--white);
            border-radius: 12px;
            padding: 2rem;
            box-sizing: border-box;
            text-align: center;
        }
        .flashcard-back {
            transform: rotateY(180deg);
            background-color: var(--secondary);
            color: var(--white);
        }
        .word {
            font-size: 2.5rem;
            font-weight: bold;
            margin-bottom: 1rem;
        }
        .type-badge {
            font-size: 0.9rem;
            text-transform: uppercase;
            letter-spacing: 1px;
            background: rgba(0,0,0,0.1);
            padding: 4px 8px;
            border-radius: 4px;
        }
        .flashcard-back .type-badge {
            background: rgba(255,255,255,0.2);
        }
        .navigation {
            display: flex;
            gap: 1rem;
            align-items: center;
        }
        .counter {
            font-size: 1.2rem;
            font-weight: bold;
            min-width: 80px;
            text-align: center;
        }
    </style>
</head>
<body>

    <h1>Spanish for Educators & Librarians</h1>
    
    <div class="controls">
        <select id="typeFilter" onchange="filterCards()">
            <option value="all">All Words</option>
            <option value="noun">Nouns Only</option>
            <option value="verb">Verbs Only</option>
        </select>
        <button onclick="shuffleCards()">Shuffle Deck</button>
    </div>

    <div class="flashcard-container" onclick="flipCard()">
        <div class="flashcard" id="flashcard">
            <div class="flashcard-face flashcard-front">
                <div class="word" id="es-word">Cargando...</div>
                <div class="type-badge" id="es-type">...</div>
            </div>
            <div class="flashcard-face flashcard-back">
                <div class="word" id="en-word">Loading...</div>
                <div class="type-badge" id="en-type">...</div>
            </div>
        </div>
    </div>

    <div class="navigation">
        <button onclick="prevCard()">&#8592; Previous</button>
        <div class="counter" id="counter">0 / 0</div>
        <button onclick="nextCard()">Next &#8594;</button>
    </div>

    <script>
        // Vocabulary Database (Sample Set for Higher Ed, Library, and IT)
        // You can continually add to this array to reach your 1,000 word goal.
        const allVocab = [
            // --- NOUNS (Higher Ed & Library) ---
            { es: "la biblioteca", en: "library", type: "noun" },
            { es: "el bibliotecario", en: "librarian (male)", type: "noun" },
            { es: "la bibliotecaria", en: "librarian (female)", type: "noun" },
            { es: "la universidad", en: "university", type: "noun" },
            { es: "el profesor", en: "professor (male)", type: "noun" },
            { es: "la profesora", en: "professor (female)", type: "noun" },
            { es: "el estudiante", en: "student", type: "noun" },
            { es: "el aula", en: "classroom", type: "noun" },
            { es: "la conferencia", en: "lecture", type: "noun" },
            { es: "el plan de estudios", en: "syllabus / curriculum", type: "noun" },
            { es: "la calificación", en: "grade", type: "noun" },
            { es: "la beca", en: "scholarship / grant", type: "noun" },
            { es: "el catálogo", en: "catalog", type: "noun" },
            { es: "la base de datos", en: "database", type: "noun" },
            { es: "el artículo", en: "article", type: "noun" },
            { es: "la revista académica", en: "academic journal", type: "noun" },
            { es: "la investigación", en: "research", type: "noun" },
            { es: "la cita", en: "citation", type: "noun" },
            { es: "el plagio", en: "plagiarism", type: "noun" },
            { es: "el archivo", en: "archive / file", type: "noun" },
            { es: "el decano", en: "dean (male)", type: "noun" },
    { es: "la decana", en: "dean (female)", type: "noun" },
    { es: "el rector", en: "university president / chancellor", type: "noun" },
    { es: "el departamento", en: "department", type: "noun" },
    { es: "la facultad", en: "faculty / school (within a university)", type: "noun" },
    { es: "el recinto", en: "campus / precinct", type: "noun" },
    { es: "el campus", en: "campus", type: "noun" },
    { es: "la matrícula", en: "enrollment / registration fee", type: "noun" },
    { es: "la colegiatura", en: "tuition", type: "noun" },
    { es: "el crédito", en: "academic credit", type: "noun" },
    { es: "el requisito", en: "requirement", type: "noun" },
    { es: "el prerrequisito", en: "prerequisite", type: "noun" },
    { es: "el bachillerato", en: "bachelor's degree / high school diploma (varies by region)", type: "noun" },
    { es: "la licenciatura", en: "bachelor's degree (LatAm)", type: "noun" },
    { es: "la maestría", en: "master's degree", type: "noun" },
    { es: "el doctorado", en: "doctorate / PhD", type: "noun" },
    { es: "el posgrado", en: "postgraduate studies", type: "noun" },
    { es: "el título", en: "degree / title", type: "noun" },
    { es: "el diploma", en: "diploma", type: "noun" },
    { es: "el certificado", en: "certificate", type: "noun" },
    { es: "la ceremonia", en: "ceremony", type: "noun" },
    { es: "la graduación", en: "graduation", type: "noun" },
    { es: "el egresado", en: "graduate / alumnus", type: "noun" },
    { es: "el exalumno", en: "alumnus / former student", type: "noun" },
    { es: "el novato", en: "freshman / beginner", type: "noun" },
    { es: "el decanato", en: "dean's office", type: "noun" },
    { es: "el comité", en: "committee", type: "noun" },
    { es: "la junta", en: "board / meeting", type: "noun" },
    { es: "el estatuto", en: "statute", type: "noun" },
    { es: "el reglamento", en: "regulations / rules", type: "noun" },
    { es: "la política", en: "policy", type: "noun" },
    { es: "la sanción", en: "sanction / penalty", type: "noun" },
    { es: "la apelación", en: "appeal", type: "noun" },
    { es: "el préstamo estudiantil", en: "student loan", type: "noun" },
    { es: "la subvención", en: "grant / subsidy", type: "noun" },
    { es: "el ensayo", en: "essay", type: "noun" },
    { es: "la tesis", en: "thesis", type: "noun" },
    { es: "la disertación", en: "dissertation", type: "noun" },
    { es: "la monografía", en: "monograph", type: "noun" },
    { es: "el borrador (texto)", en: "rough draft", type: "noun" },
    { es: "el esquema", en: "outline / diagram", type: "noun" },
    { es: "la revisión", en: "review / revision", type: "noun" },
    { es: "la edición", en: "edition / editing", type: "noun" },
    { es: "la rúbrica", en: "grading rubric", type: "noun" },
    { es: "la evaluación", en: "assessment / evaluation", type: "noun" },
    { es: "el examen", en: "exam", type: "noun" },
    { es: "la prueba", en: "quiz / test", type: "noun" },
    { es: "el parcial", en: "midterm exam", type: "noun" },
    { es: "el examen final", en: "final exam", type: "noun" },
    { es: "el cuestionario", en: "questionnaire", type: "noun" },
    { es: "la pizarra", en: "whiteboard / chalkboard", type: "noun" },
    { es: "el rotulador", en: "marker", type: "noun" },
    { es: "el borrador (pizarra)", en: "eraser (for board)", type: "noun" },
    { es: "el proyector", en: "projector", type: "noun" },
    { es: "la diapositiva", en: "slide (presentation)", type: "noun" },
    { es: "el podio", en: "podium", type: "noun" },
    { es: "el atril", en: "lectern / stand", type: "noun" },
    { es: "el pupitre", en: "student desk", type: "noun" },
    { es: "el escritorio", en: "teacher's desk / office desk", type: "noun" },
    { es: "la tiza", en: "chalk", type: "noun" },
    { es: "el laboratorio", en: "laboratory", type: "noun" },
    { es: "el equipo", en: "equipment / team", type: "noun" },
    { es: "el experimento", en: "experiment", type: "noun" },
    { es: "el informe", en: "report", type: "noun" },
    { es: "el análisis", en: "analysis", type: "noun" },
    { es: "el método", en: "method", type: "noun" },
    { es: "la teoría", en: "theory", type: "noun" },
    { es: "la hipótesis", en: "hypothesis", type: "noun" },
    { es: "el resultado", en: "result", type: "noun" },
    { es: "la conclusión", en: "conclusion", type: "noun" },
    { es: "el debate", en: "debate", type: "noun" },
    { es: "el seminario", en: "seminar", type: "noun" },
    { es: "el simposio", en: "symposium", type: "noun" },
    { es: "el taller", en: "workshop", type: "noun" },
    { es: "el congreso", en: "conference / congress", type: "noun" },
            // --- NOUNS (IT & Productivity) ---
            { es: "el ordenador", en: "computer (Spain)", type: "noun" },
            { es: "la computadora", en: "computer (LatAm)", type: "noun" },
            { es: "el teclado", en: "keyboard", type: "noun" },
            { es: "la pantalla", en: "screen / monitor", type: "noun" },
            { es: "el ratón", en: "mouse", type: "noun" },
            { es: "el software", en: "software", type: "noun" },
            { es: "la red", en: "network", type: "noun" },
            { es: "el enlace", en: "link", type: "noun" },
            { es: "el navegador", en: "web browser", type: "noun" },
            { es: "la contraseña", en: "password", type: "noun" },
            { es: "el usuario", en: "user", type: "noun" },
            { es: "el documento", en: "document", type: "noun" },
            { es: "la hoja de cálculo", en: "spreadsheet", type: "noun" },
            { es: "la presentación", en: "presentation", type: "noun" },
            { es: "la carpeta", en: "folder", type: "noun" },
            { es: "el correo electrónico", en: "email", type: "noun" },
            { es: "el archivo adjunto", en: "attachment", type: "noun" },
            { es: "la nube", en: "the cloud", type: "noun" },
            { es: "el servidor", en: "server", type: "noun" },
            { es: "la configuración", en: "settings / configuration", type: "noun" },
{ es: "el mostrador", en: "circulation desk / counter", type: "noun" },
    { es: "la renovación", en: "renewal", type: "noun" },
    { es: "la devolución", en: "return (of a book)", type: "noun" },
    { es: "la multa", en: "fine (penalty)", type: "noun" },
    { es: "el estante", en: "shelf", type: "noun" },
    { es: "la estantería", en: "bookcase / shelving", type: "noun" },
    { es: "el pasillo", en: "aisle", type: "noun" },
    { es: "el índice", en: "index", type: "noun" },
    { es: "el glosario", en: "glossary", type: "noun" },
    { es: "el apéndice", en: "appendix", type: "noun" },
    { es: "la bibliografía", en: "bibliography", type: "noun" },
    { es: "la referencia", en: "reference", type: "noun" },
    { es: "la circulación", en: "circulation", type: "noun" },
    { es: "la colección", en: "collection", type: "noun" },
    { es: "el manuscrito", en: "manuscript", type: "noun" },
    { es: "el pergamino", en: "parchment", type: "noun" },
    { es: "la hemeroteca", en: "periodicals section / newspaper archive", type: "noun" },
    { es: "la revista", en: "magazine", type: "noun" },
    { es: "el periódico", en: "newspaper", type: "noun" },
    { es: "el diario", en: "daily newspaper / journal", type: "noun" },
    { es: "el boletín", en: "bulletin / newsletter", type: "noun" },
    { es: "la enciclopedia", en: "encyclopedia", type: "noun" },
    { es: "el diccionario", en: "dictionary", type: "noun" },
    { es: "el atlas", en: "atlas", type: "noun" },
    { es: "el mapa", en: "map", type: "noun" },
    { es: "el manual", en: "manual", type: "noun" },
    { es: "la guía", en: "guide", type: "noun" },
    { es: "el directorio", en: "directory", type: "noun" },
    { es: "el volumen", en: "volume (book)", type: "noun" },
    { es: "el tomo", en: "tome / volume", type: "noun" },
{ es: "el hardware", en: "hardware", type: "noun" },
    { es: "el procesador", en: "processor", type: "noun" },
    { es: "la memoria", en: "memory", type: "noun" },
    { es: "el disco duro", en: "hard drive", type: "noun" },
    { es: "la unidad", en: "drive (e.g., USB drive)", type: "noun" },
    { es: "el puerto", en: "port (e.g., USB port)", type: "noun" },
    { es: "el cable", en: "cable", type: "noun" },
    { es: "el adaptador", en: "adapter", type: "noun" },
    { es: "el cargador", en: "charger", type: "noun" },
    { es: "el enchufe", en: "plug / outlet", type: "noun" },
    { es: "el interruptor", en: "switch", type: "noun" },
    { es: "la batería", en: "battery", type: "noun" },
    { es: "el icono", en: "icon", type: "noun" },
    { es: "la ventana", en: "window", type: "noun" },
    { es: "el menú", en: "menu", type: "noun" },
    { es: "la pestaña", en: "tab", type: "noun" },
    { es: "la herramienta", en: "tool", type: "noun" },
    { es: "la barra", en: "bar (e.g., toolbar)", type: "noun" },
    { es: "el historial", en: "browser history", type: "noun" },
    { es: "el marcador", en: "bookmark (browser)", type: "noun" },
    { es: "el favorito", en: "favorite (bookmark)", type: "noun" },
    { es: "el cursor", en: "cursor", type: "noun" },
    { es: "el puntero", en: "pointer", type: "noun" },
    { es: "el acceso directo", en: "shortcut", type: "noun" },
    { es: "la papelera", en: "trash / recycle bin", type: "noun" },
    { es: "el virus", en: "virus", type: "noun" },
    { es: "el antivirus", en: "antivirus", type: "noun" },
    { es: "el cortafuegos", en: "firewall", type: "noun" },
    { es: "el perfil", en: "profile", type: "noun" },
    { es: "la cuenta", en: "account", type: "noun" },
    { es: "la sesión", en: "session", type: "noun" },
    { es: "la clave", en: "key / password", type: "noun" },
    { es: "el formato", en: "format", type: "noun" },
    { es: "la fuente", en: "font / typeface", type: "noun" },
    { es: "la plantilla", en: "template", type: "noun" },
    { es: "el gráfico", en: "chart / graph", type: "noun" },
    { es: "la tabla", en: "table (data)", type: "noun" },
    { es: "la fila", en: "row", type: "noun" },
    { es: "la columna", en: "column", type: "noun" },
    { es: "la celda", en: "cell (spreadsheet)", type: "noun" },
    { es: "el hipervínculo", en: "hyperlink", type: "noun" },
    { es: "el enrutador", en: "router", type: "noun" },
    { es: "el módem", en: "modem", type: "noun" },
    { es: "el ancho de banda", en: "bandwidth", type: "noun" },
    { es: "el correo no deseado", en: "spam", type: "noun" },
{ es: "el asesor", en: "advisor (male)", type: "noun" },
    { es: "la asesora", en: "advisor (female)", type: "noun" },
    { es: "el consejero", en: "counselor (male)", type: "noun" },
    { es: "la consejera", en: "counselor (female)", type: "noun" },
    { es: "el mentor", en: "mentor", type: "noun" },
    { es: "la tutora", en: "tutor (female)", type: "noun" },
    { es: "la tutoría", en: "tutoring session", type: "noun" },
    { es: "el rectorado", en: "chancellor's office", type: "noun" },
    { es: "el claustro", en: "faculty / cloister", type: "noun" },
    { es: "la pensión", en: "boarding house / stipend", type: "noun" },
    { es: "el patrocinador", en: "sponsor", type: "noun" },
    { es: "la residencia", en: "residence hall", type: "noun" },
    { es: "el dormitorio", en: "dorm room", type: "noun" },
    { es: "el comedor", en: "dining hall", type: "noun" },
    { es: "el polideportivo", en: "sports center", type: "noun" },
    { es: "el gimnasio", en: "gymnasium", type: "noun" },
    { es: "el estadio", en: "stadium", type: "noun" },
    { es: "el auditorio", en: "auditorium", type: "noun" },
    { es: "el teatro", en: "theater", type: "noun" },
    { es: "el centro estudiantil", en: "student center", type: "noun" },
    { es: "la fraternidad", en: "fraternity", type: "noun" },
    { es: "la hermandad", en: "sorority / brotherhood", type: "noun" },
    { es: "el club", en: "club", type: "noun" },
    { es: "la asociación", en: "association", type: "noun" },
    { es: "el alumnado", en: "student body", type: "noun" },
    { es: "el profesorado", en: "teaching staff", type: "noun" },
    { es: "el personal", en: "staff", type: "noun" },
    { es: "el sindicato", en: "union", type: "noun" },
    { es: "la asistencia", en: "attendance", type: "noun" },
    { es: "la inasistencia", en: "absence", type: "noun" },
    { es: "la tardanza", en: "tardiness", type: "noun" },
    { es: "el retraso", en: "delay", type: "noun" },
    { es: "el justificante", en: "doctor's note / written excuse", type: "noun" },
    { es: "la expulsión", en: "expulsion", type: "noun" },
    { es: "la suspensión", en: "suspension", type: "noun" },
    { es: "la amonestación", en: "warning / reprimand", type: "noun" },
    { es: "el mérito", en: "merit", type: "noun" },
    { es: "la distinción", en: "distinction", type: "noun" },
    { es: "el honor", en: "honor", type: "noun" },
    { es: "el premio", en: "award / prize", type: "noun" },
    { es: "el semestre", en: "semester", type: "noun" },
    { es: "el trimestre", en: "trimester / quarter", type: "noun" },
    { es: "el cuatrimestre", en: "four-month term", type: "noun" },
    { es: "el período", en: "period / term", type: "noun" },
    { es: "el ciclo", en: "cycle", type: "noun" },
    { es: "el horario", en: "schedule", type: "noun" },
    { es: "el calendario", en: "calendar", type: "noun" },
    { es: "la agenda", en: "agenda / planner", type: "noun" },
    { es: "el almanaque", en: "almanac", type: "noun" },
    { es: "el compañero de clase", en: "classmate", type: "noun" },
{ es: "el repositorio", en: "repository", type: "noun" },
    { es: "el archivo digital", en: "digital archive", type: "noun" },
    { es: "el microfilm", en: "microfilm", type: "noun" },
    { es: "la microficha", en: "microfiche", type: "noun" },
    { es: "el facsímil", en: "facsimile", type: "noun" },
    { es: "el folleto", en: "brochure / pamphlet", type: "noun" },
    { es: "el panfleto", en: "pamphlet", type: "noun" },
    { es: "el papiro", en: "papyrus", type: "noun" },
    { es: "el incunable", en: "incunable (early printed book)", type: "noun" },
    { es: "el lomo", en: "spine (of a book)", type: "noun" },
    { es: "la portada", en: "title page / front cover", type: "noun" },
    { es: "la cubierta", en: "cover", type: "noun" },
    { es: "la contraportada", en: "back cover", type: "noun" },
    { es: "el prefacio", en: "preface", type: "noun" },
    { es: "el prólogo", en: "prologue", type: "noun" },
    { es: "el epílogo", en: "epilogue", type: "noun" },
    { es: "el colofón", en: "colophon", type: "noun" },
    { es: "la tabla de materias", en: "table of contents", type: "noun" },
    { es: "el carrito", en: "book cart", type: "noun" },
    { es: "el código de barras", en: "barcode", type: "noun" },
    { es: "la etiqueta", en: "label", type: "noun" },
    { es: "el tejuelo", en: "spine label", type: "noun" },
    { es: "la signatura topográfica", en: "call number", type: "noun" },
    { es: "el préstamo interbibliotecario", en: "interlibrary loan", type: "noun" },
    { es: "la reserva", en: "reservation / hold", type: "noun" },
    { es: "el donativo", en: "donation", type: "noun" },
    { es: "el expurgo", en: "weeding / discarding of books", type: "noun" },
    { es: "el deterioro", en: "deterioration", type: "noun" },
    { es: "la preservación", en: "preservation", type: "noun" },
    { es: "la conservación", en: "conservation", type: "noun" },
    { es: "el encuadernador", en: "bookbinder", type: "noun" },
    { es: "la restauración", en: "restoration", type: "noun" },
    { es: "el depósito", en: "depository / storage", type: "noun" },
    { es: "la sala de lectura", en: "reading room", type: "noun" },
    { es: "el puesto de estudio", en: "study carrel", type: "noun" },
    { es: "la cabina", en: "cubicle / study booth", type: "noun" },
    { es: "el silencio", en: "silence", type: "noun" },
    { es: "el ruido", en: "noise", type: "noun" },
    { es: "el préstamo", en: "loan", type: "noun" },
    { es: "la tirada", en: "print run", type: "noun" },
    { es: "la reimpresión", en: "reprint", type: "noun" },
    { es: "el ISBN", en: "ISBN", type: "noun" },
    { es: "el ISSN", en: "ISSN", type: "noun" },
    { es: "la imprenta", en: "printing press", type: "noun" },
    { es: "la editorial", en: "publisher", type: "noun" },
    { es: "el autor", en: "author (male)", type: "noun" },
    { es: "la autora", en: "author (female)", type: "noun" },
    { es: "el editor", en: "editor (male)", type: "noun" },
    { es: "la editora", en: "editor (female)", type: "noun" },
    { es: "el redactor", en: "copywriter / redactor", type: "noun" },
    { es: "el traductor", en: "translator", type: "noun" },
    { es: "la sinopsis", en: "synopsis / blurb", type: "noun" },
    { es: "el seudónimo", en: "pseudonym", type: "noun" },
    { es: "la antología", en: "anthology", type: "noun" },
    { es: "la compilación", en: "compilation", type: "noun" },
    { es: "el compendio", en: "compendium", type: "noun" },
    { es: "el extracto", en: "excerpt", type: "noun" },
    { es: "la cita textual", en: "direct quote", type: "noun" },
    { es: "la paráfrasis", en: "paraphrase", type: "noun" },
    { es: "el formato APA", en: "APA format", type: "noun" },
    { es: "el formato MLA", en: "MLA format", type: "noun" },
    { es: "el manual de estilo", en: "style manual", type: "noun" },
    { es: "el derecho de autor", en: "copyright", type: "noun" },
    { es: "el dominio público", en: "public domain", type: "noun" },
    { es: "la licencia", en: "license", type: "noun" },
    { es: "el acceso abierto", en: "open access", type: "noun" },
    { es: "el embargo", en: "embargo", type: "noun" },
    { es: "el consorcio", en: "consortium", type: "noun" },
    { es: "el metabuscador", en: "metasearch engine", type: "noun" },
    { es: "el operador booleano", en: "Boolean operator", type: "noun" },
    { es: "la palabra clave", en: "keyword", type: "noun" },
    { es: "la búsqueda avanzada", en: "advanced search", type: "noun" },
    { es: "el campo de búsqueda", en: "search field", type: "noun" },
    { es: "el truncamiento", en: "truncation", type: "noun" },
    { es: "la taxonomía", en: "taxonomy", type: "noun" },

    // --- IT, HARDWARE, SOFTWARE & PRODUCTIVITY ---
    { es: "el dispositivo", en: "device", type: "noun" },
    { es: "el aparato", en: "appliance / device", type: "noun" },
    { es: "el móvil", en: "mobile phone (Spain)", type: "noun" },
    { es: "el celular", en: "cell phone (LatAm)", type: "noun" },
    { es: "la tableta", en: "tablet", type: "noun" },
    { es: "el portátil", en: "laptop", type: "noun" },
    { es: "el auricular", en: "earphone / headset", type: "noun" },
    { es: "el micrófono", en: "microphone", type: "noun" },
    { es: "el altavoz", en: "speaker (Spain)", type: "noun" },
    { es: "el parlante", en: "speaker (LatAm)", type: "noun" },
    { es: "la cámara web", en: "webcam", type: "noun" },
    { es: "el puerto HDMI", en: "HDMI port", type: "noun" },
    { es: "la placa base", en: "motherboard", type: "noun" },
    { es: "el microprocesador", en: "microprocessor", type: "noun" },
    { es: "el ventilador", en: "cooling fan", type: "noun" },
    { es: "el servidor web", en: "web server", type: "noun" },
    { es: "el dominio", en: "web domain", type: "noun" },
    { es: "la dirección IP", en: "IP address", type: "noun" },
    { es: "el protocolo", en: "protocol", type: "noun" },
    { es: "el certificado SSL", en: "SSL certificate", type: "noun" },
    { es: "la cookie", en: "browser cookie", type: "noun" },
    { es: "el caché", en: "cache", type: "noun" },
    { es: "el complemento", en: "add-on / add-in", type: "noun" },
    { es: "la extensión", en: "browser extension", type: "noun" },
    { es: "el plugin", en: "plugin", type: "noun" },
    { es: "la interfaz", en: "interface", type: "noun" },
    { es: "el panel de control", en: "control panel", type: "noun" },
    { es: "el tablero", en: "dashboard", type: "noun" },
    { es: "la consola", en: "console", type: "noun" },
    { es: "la terminal", en: "terminal (command line)", type: "noun" },
    { es: "el código fuente", en: "source code", type: "noun" },
    { es: "la etiqueta HTML", en: "HTML tag", type: "noun" },
    { es: "la hoja de estilos", en: "stylesheet (CSS)", type: "noun" },
    { es: "el script", en: "script", type: "noun" },
    { es: "el algoritmo", en: "algorithm", type: "noun" },
    { es: "la base de datos relacional", en: "relational database", type: "noun" },
    { es: "la consulta", en: "database query", type: "noun" },
    { es: "el respaldo", en: "backup", type: "noun" },
    { es: "la copia de seguridad", en: "backup copy", type: "noun" },
    { es: "el almacenamiento", en: "storage", type: "noun" },
    { es: "el megabyte", en: "megabyte", type: "noun" },
    { es: "el gigabyte", en: "gigabyte", type: "noun" },
    { es: "el terabyte", en: "terabyte", type: "noun" },
    { es: "el píxel", en: "pixel", type: "noun" },
    { es: "la resolución", en: "resolution", type: "noun" },
    { es: "el brillo", en: "brightness", type: "noun" },
    { es: "el contraste", en: "contrast", type: "noun" },
    { es: "el filtro", en: "filter", type: "noun" },
    { es: "la macro", en: "macro (spreadsheet)", type: "noun" },
    { es: "la celda activa", en: "active cell", type: "noun" },
    { es: "el rango", en: "range (data)", type: "noun" },
    { es: "el gráfico de barras", en: "bar chart", type: "noun" },
    { es: "el gráfico circular", en: "pie chart", type: "noun" },
    { es: "el eje", en: "axis (graphing)", type: "noun" },
    { es: "la leyenda", en: "legend (chart)", type: "noun" },
    { es: "la viñeta", en: "bullet point", type: "noun" },
    { es: "la sangría", en: "indentation", type: "noun" },
    { es: "el margen", en: "margin", type: "noun" },
    { es: "el espaciado", en: "spacing", type: "noun" },
    { es: "el interlineado", en: "line spacing", type: "noun" },
    { es: "la alineación", en: "alignment", type: "noun" },
    { es: "el encabezado", en: "header", type: "noun" },
    { es: "el pie de página", en: "footer", type: "noun" },
    { es: "el salto de página", en: "page break", type: "noun" },
    { es: "la marca de agua", en: "watermark", type: "noun" },
    { es: "el cuadro de texto", en: "text box", type: "noun" },
    { es: "la imagen prediseñada", en: "clipart", type: "noun" },
    { es: "el hipertexto", en: "hypertext", type: "noun" },
    { es: "el enlace roto", en: "broken link", type: "noun" },
    { es: "el error", en: "error", type: "noun" },
    { es: "el fallo", en: "bug / glitch", type: "noun" },
    { es: "la captura de pantalla", en: "screenshot", type: "noun" },
    { es: "el pantallazo", en: "screenshot (colloquial)", type: "noun" },
    { es: "el atajo de teclado", en: "keyboard shortcut", type: "noun" },
    { es: "el metadato", en: "metadata", type: "noun" },

            // --- VERBS (Higher Ed & Library) ---
            { es: "enseñar", en: "to teach", type: "verb" },
            { es: "aprender", en: "to learn", type: "verb" },
            { es: "estudiar", en: "to study", type: "verb" },
            { es: "leer", en: "to read", type: "verb" },
            { es: "escribir", en: "to write", type: "verb" },
            { es: "investigar", en: "to research", type: "verb" },
            { es: "citar", en: "to cite", type: "verb" },
            { es: "evaluar", en: "to evaluate", type: "verb" },
            { es: "calificar", en: "to grade", type: "verb" },
            { es: "prestar", en: "to lend (books)", type: "verb" },
            { es: "matricularse", en: "to enroll / register", type: "verb" },
    { es: "inscribirse", en: "to sign up / enroll", type: "verb" },
    { es: "especializarse", en: "to major in", type: "verb" },
    { es: "graduarse", en: "to graduate", type: "verb" },
    { es: "aprobar", en: "to pass (an exam/class)", type: "verb" },
    { es: "reprobar", en: "to fail (LatAm)", type: "verb" },
    { es: "suspender", en: "to fail (Spain)", type: "verb" },
    { es: "asistir", en: "to attend", type: "verb" },
    { es: "faltar", en: "to be absent / miss class", type: "verb" },
    { es: "entregar", en: "to turn in / submit", type: "verb" },
    { es: "presentar", en: "to present", type: "verb" },
    { es: "debatir", en: "to debate", type: "verb" },
    { es: "analizar", en: "to analyze", type: "verb" },
    { es: "resumir", en: "to summarize", type: "verb" },
    { es: "revisar", en: "to review / check", type: "verb" },
    { es: "corregir", en: "to correct / grade", type: "verb" },
    { es: "subrayar", en: "to underline / highlight", type: "verb" },
    { es: "destacar", en: "to highlight / emphasize", type: "verb" },
    { es: "memorizar", en: "to memorize", type: "verb" },
    { es: "repasar", en: "to review (study)", type: "verb" },
    { es: "parafrasear", en: "to paraphrase", type: "verb" },
    { es: "clasificar", en: "to classify", type: "verb" },
    { es: "catalogar", en: "to catalog", type: "verb" },
    { es: "archivar", en: "to file / archive", type: "verb" },
    { es: "indexar", en: "to index", type: "verb" },
            
// --- VERBS (IT & Productivity) ---
            { es: "guardar", en: "to save", type: "verb" },
            { es: "borrar", en: "to delete / erase", type: "verb" },
            { es: "descargar", en: "to download", type: "verb" },
            { es: "subir", en: "to upload", type: "verb" },
            { es: "imprimir", en: "to print", type: "verb" },
            { es: "hacer clic", en: "to click", type: "verb" },
            { es: "navegar", en: "to navigate / browse", type: "verb" },
            { es: "copiar", en: "to copy", type: "verb" },
            { es: "pegar", en: "to paste", type: "verb" },
            { es: "reiniciar", en: "to restart", type: "verb" },
{ es: "buscar", en: "to search", type: "verb" },
    { es: "recuperar", en: "to recover (data)", type: "verb" },
    { es: "renovar", en: "to renew", type: "verb" },
    { es: "devolver", en: "to return (items)", type: "verb" },
    { es: "escanear", en: "to scan", type: "verb" },
    { es: "fotocopiar", en: "to photocopy", type: "verb" },
    { es: "encuadernar", en: "to bind (a book)", type: "verb" },
    { es: "teclear", en: "to type", type: "verb" },
    { es: "arrastrar", en: "to drag", type: "verb" },
    { es: "soltar", en: "to drop (drag and drop)", type: "verb" },
    { es: "maximizar", en: "to maximize", type: "verb" },
    { es: "minimizar", en: "to minimize", type: "verb" },
    { es: "adjuntar", en: "to attach", type: "verb" },
    { es: "comprimir", en: "to zip / compress", type: "verb" },
    { es: "descomprimir", en: "to unzip / extract", type: "verb" },
    { es: "instalar", en: "to install", type: "verb" },
    { es: "desinstalar", en: "to uninstall", type: "verb" },
    { es: "actualizar", en: "to update", type: "verb" },
    { es: "reiniciar", en: "to restart", type: "verb" },
    { es: "conectar", en: "to connect", type: "verb" },
    { es: "desconectar", en: "to disconnect", type: "verb" },
    { es: "sincronizar", en: "to sync", type: "verb" },
    { es: "formatear", en: "to format", type: "verb" },
    { es: "configurar", en: "to configure / set up", type: "verb" },
    { es: "personalizar", en: "to customize", type: "verb" }
        ];

        let currentDeck = [...allVocab];
        let currentIndex = 0;

        const cardElement = document.getElementById('flashcard');
        const esWordElement = document.getElementById('es-word');
        const enWordElement = document.getElementById('en-word');
        const esTypeElement = document.getElementById('es-type');
        const enTypeElement = document.getElementById('en-type');
        const counterElement = document.getElementById('counter');

        function updateCard() {
            if (currentDeck.length === 0) {
                esWordElement.textContent = "No cards";
                enWordElement.textContent = "No cards";
                esTypeElement.textContent = "";
                enTypeElement.textContent = "";
                counterElement.textContent = "0 / 0";
                return;
            }

            // Ensure card is showing the front when updating
            cardElement.classList.remove('is-flipped');
            
            setTimeout(() => {
                const card = currentDeck[currentIndex];
                esWordElement.textContent = card.es;
                enWordElement.textContent = card.en;
                esTypeElement.textContent = card.type;
                enTypeElement.textContent = card.type;
                counterElement.textContent = `${currentIndex + 1} / ${currentDeck.length}`;
            }, 150); // slight delay to allow flip animation to reset smoothly
        }

        function flipCard() {
            if (currentDeck.length > 0) {
                cardElement.classList.toggle('is-flipped');
            }
        }

        function nextCard() {
            if (currentDeck.length > 0) {
                currentIndex = (currentIndex + 1) % currentDeck.length;
                updateCard();
            }
        }

        function prevCard() {
            if (currentDeck.length > 0) {
                currentIndex = (currentIndex - 1 + currentDeck.length) % currentDeck.length;
                updateCard();
            }
        }

        function filterCards() {
            const filterValue = document.getElementById('typeFilter').value;
            if (filterValue === 'all') {
                currentDeck = [...allVocab];
            } else {
                currentDeck = allVocab.filter(word => word.type === filterValue);
            }
            currentIndex = 0;
            updateCard();
        }

        function shuffleCards() {
            for (let i = currentDeck.length - 1; i > 0; i--) {
                const j = Math.floor(Math.random() * (i + 1));
                [currentDeck[i], currentDeck[j]] = [currentDeck[j], currentDeck[i]];
            }
            currentIndex = 0;
            updateCard();
        }

        // Initialize first card
        updateCard();
    </script>
</body>
</html>
