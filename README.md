<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Vocabulary Exercise: General English</title>
    <style>
        :root {
            --primary-color: #00897B; /* Teal */
            --secondary-color: #80CBC4; /* Light Teal */
            --background-color: #F4F6F6;
            --container-bg: #FFFFFF;
            --correct-color: #4CAF50;
            --incorrect-color: #F44336;
        }

        body {
            font-family: 'Segoe UI', Tahoma, Geneva, Verdana, sans-serif;
            margin: 0;
            padding: 20px;
            background-color: var(--background-color);
            color: #333;
            line-height: 1.6;
        }

        .container {
            max-width: 900px;
            margin: 0 auto;
            background-color: var(--container-bg);
            padding: 30px;
            border-radius: 15px;
            box-shadow: 0 10px 30px rgba(0, 0, 0, 0.1);
        }

        h1 {
            color: var(--primary-color);
            text-align: center;
            margin-bottom: 25px;
            font-size: 2em;
        }

        /* --- Navigation --- */
        .nav-buttons {
            display: flex;
            justify-content: center;
            gap: 10px;
            margin-bottom: 30px;
        }

        .nav-buttons button {
            padding: 10px 20px;
            border: none;
            border-radius: 8px;
            cursor: pointer;
            font-size: 1em;
            font-weight: 600;
            transition: all 0.3s ease;
            background: #E0F2F1;
            color: var(--primary-color);
        }

        .nav-buttons button.active,
        .nav-buttons button:hover {
            background: var(--primary-color);
            color: white;
            box-shadow: 0 4px 10px rgba(0, 0, 0, 0.2);
        }

        .section {
            padding: 20px 0;
            border-top: 1px solid #EEE;
            display: none;
        }

        .section.active {
            display: block;
        }

        /* --- Scoreboard --- */
        #score-display {
            position: absolute;
            top: 20px;
            right: 20px;
            font-size: 1.1em;
            font-weight: 600;
            color: var(--primary-color);
            background: var(--secondary-color);
            padding: 8px 15px;
            border-radius: 5px;
        }

        /* --- Vocabulary List --- */
        .vocab-item {
            display: flex;
            justify-content: space-between;
            align-items: center;
            padding: 15px;
            margin-bottom: 10px;
            border-bottom: 1px dashed var(--secondary-color);
        }

        .vocab-item:last-child {
            border-bottom: none;
        }

        .vocab-word-details {
            flex-grow: 1;
        }

        .word {
            font-weight: 700;
            color: var(--primary-color);
            font-size: 1.2em;
        }

        .context {
            font-style: italic;
            color: #777;
            font-size: 0.9em;
            margin-left: 10px;
        }

        .explanation, .example {
            margin-top: 5px;
            font-size: 0.95em;
        }

        .speak-button {
            background: var(--secondary-color);
            color: var(--primary-color);
            border: none;
            padding: 8px 12px;
            border-radius: 6px;
            cursor: pointer;
            font-weight: 600;
            transition: background 0.2s;
        }

        .speak-button:hover {
            background: var(--primary-color);
            color: white;
        }

        /* --- Word Bank Styling --- */
        .word-bank {
            display: flex;
            flex-wrap: wrap;
            gap: 10px;
            padding: 15px;
            margin-bottom: 20px;
            border-radius: 10px;
            background: linear-gradient(135deg, #E8F5E9 0%, #B9F6CA 100%);
            border: 1px solid var(--correct-color);
            justify-content: center;
            font-weight: 600;
            color: #1B5E20;
        }

        .word-bank span {
            padding: 5px 12px;
            background-color: white;
            border-radius: 20px;
            box-shadow: 0 2px 5px rgba(0, 0, 0, 0.1);
        }

        /* --- Fill in the Gaps (Writing) --- */
        .gap-sentence {
            padding: 10px 0;
            border-bottom: 1px dotted #CCC;
            margin-bottom: 15px;
        }

        .gap-sentence input[type="text"] {
            padding: 8px;
            border: 1px solid var(--secondary-color);
            border-radius: 5px;
            font-size: 1em;
            width: 150px;
            text-align: center;
            margin: 0 5px;
            transition: border-color 0.3s;
        }

        .gap-sentence input:focus {
            border-color: var(--primary-color);
            outline: none;
        }

        .feedback {
            margin-left: 15px;
            font-weight: 600;
        }

        .writing-controls {
            display: flex;
            gap: 15px;
            margin-top: 20px;
            justify-content: center;
        }

        .writing-controls button {
            padding: 10px 25px;
            border: none;
            border-radius: 8px;
            cursor: pointer;
            font-weight: 700;
            transition: background 0.3s;
        }

        #check-writing {
            background: var(--primary-color);
            color: white;
        }

        #check-writing:hover {
            background: #00695C;
        }

        #reset-writing {
            background: #EEE;
            color: #333;
        }

        #reset-writing:hover {
            background: #DDD;
        }

        /* --- Match Definitions --- */
        .match-container {
            display: flex;
            justify-content: space-around;
            gap: 20px;
        }

        .match-column {
            flex-basis: 48%;
            display: flex;
            flex-direction: column;
            gap: 10px;
        }

        .match-item {
            padding: 12px;
            border: 2px solid var(--secondary-color);
            border-radius: 8px;
            cursor: pointer;
            transition: all 0.3s ease;
            user-select: none;
            min-height: 40px;
            display: flex;
            align-items: center;
            background-color: var(--container-bg);
        }

        .match-word {
            font-weight: 700;
            color: var(--primary-color);
        }

        .match-definition {
            font-style: italic;
        }

        .match-selected {
            border-color: var(--primary-color) !important;
            background-color: #E0F7FA;
            box-shadow: 0 0 10px rgba(0, 137, 123, 0.3);
        }

        .match-correct {
            background-color: var(--correct-color) !important;
            color: white;
            border-color: var(--correct-color) !important;
            cursor: default;
            box-shadow: none;
        }

        .match-incorrect {
            animation: shake 0.5s;
            border-color: var(--incorrect-color) !important;
            background-color: #FFEBEE;
        }

        @keyframes shake {
            0%, 100% { transform: translateX(0); }
            20%, 60% { transform: translateX(-5px); }
            40%, 80% { transform: translateX(5px); }
        }

        /* --- Fill in the Gaps (Pronunciation) --- */
        .pron-sentence {
            display: flex;
            align-items: center;
            padding: 10px 0;
            border-bottom: 1px dotted #CCC;
            margin-bottom: 15px;
        }

        .pron-sentence p {
            flex-grow: 1;
            margin: 0;
            display: flex;
            align-items: center;
        }

        .pron-blank {
            display: inline-block;
            width: 150px;
            height: 25px;
            line-height: 25px;
            text-align: center;
            border-bottom: 2px dashed #999;
            margin: 0 5px;
            font-weight: 600;
            color: var(--primary-color);
        }

        .pron-correct {
            border-bottom: 2px solid var(--correct-color);
            color: var(--correct-color);
        }

        .mic-button {
            background: none;
            border: none;
            cursor: pointer;
            font-size: 1.5em;
            padding: 5px;
            transition: transform 0.2s;
        }

        .mic-button:hover {
            transform: scale(1.1);
        }
        
        .mic-listening {
            color: var(--incorrect-color);
            animation: pulse 1s infinite;
        }

        @keyframes pulse {
            0% { opacity: 1; }
            50% { opacity: 0.5; }
            100% { opacity: 1; }
        }

        .pron-feedback {
            margin-left: 15px;
            font-size: 0.9em;
            font-style: italic;
        }

    </style>
</head>
<body>

    <div id="score-display">Score: 0 / 18</div>

    <div class="container">
        <h1>English Vocabulary Practice</h1>

        <div class="nav-buttons">
            <button onclick="showSection('vocab-list', this)" class="active">📚 Vocabulary List</button>
            <button onclick="showSection('writing-gaps', this)">✍️ Fill in the Gaps</button>
            <button onclick="showSection('match-defs', this)">🧠 Match Definitions</button>
            <button onclick="showSection('pronunciation-gaps', this)">🗣️ Pronunciation</button>
        </div>

        <div id="vocab-list" class="section active">
            <h2>Vocabulary List & Examples</h2>
            <div id="vocab-items-container">
                </div>
        </div>

        <div id="writing-gaps" class="section">
            <h2>✍️ Fill in the Gaps (Writing)</h2>
            <p>Use the words in the bank to complete the sentences. Type the word exactly as it appears.</p>
            <div id="writing-word-bank" class="word-bank">
                </div>
            <div id="writing-sentences-container">
                </div>
            <div class="writing-controls">
                <button id="check-writing" onclick="checkWritingGaps()">Check Answers</button>
                <button id="reset-writing" onclick="resetWritingGaps()">Reset</button>
            </div>
        </div>

        <div id="match-defs" class="section">
            <h2>🧠 Match Definitions</h2>
            <p>Click a word on the left, then click its correct definition on the right.</p>
            <div class="match-container" id="match-container">
                <div class="match-column" id="match-words-container">
                    </div>
                <div class="match-column" id="match-definitions-container">
                    </div>
            </div>
        </div>

        <div id="pronunciation-gaps" class="section">
            <h2>🗣️ Fill in the Gaps (Pronunciation) </h2>
            <p>Press the microphone button, say the missing word to fill the blank.</p>
            <div id="pron-word-bank" class="word-bank">
                </div>
            <div id="pron-sentences-container">
                </div>
        </div>

    </div>

    <script>
        // --- DATA ---
        const vocabData = [
            {
                word: "abroad",
                context: "in or to a foreign country",
                explanation: "In or to a foreign country.",
                example: "She decided to study abroad for a semester to improve her language skills.",
                writingSentence: "After graduation, he plans to move ___ and find work in Australia.",
                pronSentence: "Many students choose to travel ___ during their summer break.",
                definition: "Located in or traveling to a country that is not one's own.",
            },
            {
                word: "stingy",
                context: "unwilling to spend money or share things (negative connotation)",
                explanation: "Unwilling to give or spend money, resources, or time; mean.",
                example: "He is so stingy that he never buys a round of drinks for his friends.",
                writingSentence: "Don't be ___ with the complimentary bread rolls; we are very hungry.",
                pronSentence: "The critics accused the film director of being ___ with special effects.",
                definition: "Reluctant to spend, give, or share things; overly economical.",
            },
            {
                word: "subject",
                context: "the topic being discussed or investigated",
                explanation: "A person or thing that is being discussed, described, or dealt with.",
                example: "The main subject of the lecture was the history of renewable energy.",
                writingSentence: "I didn't understand the complex ___ of the professor's advanced seminar.",
                pronSentence: "History was always my favorite ___ in school, especially ancient history.",
                definition: "The topic or matter that is presented, represented, or discussed.",
            },
            {
                word: "evidence",
                context: "facts or information indicating whether a belief is true or valid",
                explanation: "Facts or information used to support a belief, assertion, or claim.",
                example: "The police needed strong evidence to prove the suspect was guilty.",
                writingSentence: "The lawyer presented photographic ___ to the jury during the trial.",
                pronSentence: "Do you have any solid ___ that suggests the report is false?",
                definition: "Information or facts that help in proving or disproving something.",
            },
            {
                word: "quote",
                context: "preventivo (a formal statement of the estimated cost)",
                explanation: "A formal statement setting out the estimated cost for a particular job or service.",
                example: "I called three different plumbers to get a quote for the bathroom renovation.",
                writingSentence: "Before starting the work, the builder sent me a detailed ___ outlining all the expenses.",
                pronSentence: "Please ask the mechanic to give you a full ___ for the car repairs.",
                definition: "A formal written estimate of the price or cost required for a job or service.",
            },
            {
                word: "prevail",
                context: "prove more powerful or superior (win)",
                explanation: "To prove to be superior in strength, influence, or control; to triumph or win.",
                example: "We hoped that common sense and fairness would eventually prevail in the negotiations.",
                writingSentence: "Despite strong opposition, the new policy is expected to ___ in the parliament.",
                pronSentence: "In the end, we trust that justice will always ___ over corruption.",
                definition: "To be successful; to triumph over rivals or difficulties; to win.",
            }
        ];

        let totalVocabulary = vocabData.length;
        let totalPossibleScore = totalVocabulary * 3;
        let currentScore = 0;
        let writingCorrectCount = 0;
        let matchingCorrectCount = 0;
        let pronCorrectCount = 0;

        let selectedWordMatch = null;
        let selectedDefinitionMatch = null;
        const matchingAnswers = {}; // wordId -> definitionId

        const pronResults = {}; // word -> true/false

        const recognitionFallback = ('webkitSpeechRecognition' in window || 'SpeechRecognition' in window);

        // --- UTILITY FUNCTIONS ---
        function shuffleArray(array) {
            for (let i = array.length - 1; i > 0; i--) {
                const j = Math.floor(Math.random() * (i + 1));
                [array[i], array[j]] = [array[j], array[i]];
            }
            return array;
        }

        function varToHex(variable) {
            // Helper to get CSS variable color (for dynamic styling)
            const style = getComputedStyle(document.documentElement);
            const value = style.getPropertyValue(variable).trim();
            return value || '#333333';
        }

        function updateScore() {
            currentScore = writingCorrectCount + matchingCorrectCount + pronCorrectCount;
            document.getElementById('score-display').innerText = `Score: ${currentScore} / ${totalPossibleScore}`;
        }

        function showSection(id, button) {
            document.querySelectorAll('.section').forEach(section => {
                section.classList.remove('active');
            });
            document.getElementById(id).classList.add('active');

            document.querySelectorAll('.nav-buttons button').forEach(btn => {
                btn.classList.remove('active');
            });
            button.classList.add('active');
        }

        // --- 1. VOCABULARY LIST ---
        function generateVocabList() {
            const container = document.getElementById('vocab-items-container');
            container.innerHTML = '';
            vocabData.forEach(item => {
                const div = document.createElement('div');
                div.className = 'vocab-item';
                div.innerHTML = `
                    <div class="vocab-word-details">
                        <span class="word">${item.word}</span> <span class="context">(${item.context})</span>
                        <p class="explanation"><strong>Meaning:</strong> ${item.explanation}</p>
                        <p class="example"><strong>Example:</strong> <em>"${item.example}"</em></p>
                    </div>
                    <button class="speak-button" onclick="speak('${item.word}')">▶️ Hear</button>
                `;
                container.appendChild(div);
            });
        }

        function speak(text) {
            if ('speechSynthesis' in window) {
                const u = new SpeechSynthesisUtterance(text);
                u.lang = "en-US";
                speechSynthesis.speak(u);
            } else {
                alert("Speech synthesis not supported in your browser.");
            }
        }


        // --- 2. FILL IN THE GAPS (WRITING) ---
        function generateWritingGaps() {
            const container = document.getElementById('writing-sentences-container');
            const bank = document.getElementById('writing-word-bank');
            container.innerHTML = '';
            bank.innerHTML = '';

            // Generate Word Bank
            shuffleArray([...vocabData]).forEach(item => {
                const span = document.createElement('span');
                span.innerText = item.word;
                bank.appendChild(span);
            });

            // Generate Sentences (Shuffled)
            shuffleArray([...vocabData]).forEach((item, index) => {
                const sentence = item.writingSentence;
                const expectedWord = item.word;
                const sentenceHTML = sentence.replace('___', `<input type="text" data-expected="${expectedWord}" id="write-gap-${index}">`);

                const div = document.createElement('div');
                div.className = 'gap-sentence';
                div.innerHTML = `
                    <p>${sentenceHTML}<span id="write-feedback-${index}" class="feedback"></span></p>
                `;
                container.appendChild(div);
            });
        }

        function checkWritingGaps() {
            let correctCount = 0;
            document.querySelectorAll('#writing-sentences-container input').forEach((input, index) => {
                const expected = input.getAttribute('data-expected').toLowerCase().trim();
                const actual = input.value.toLowerCase().trim();
                const feedbackSpan = document.getElementById(`write-feedback-${index}`);

                if (input.disabled) {
                    if (actual === expected) correctCount++;
                    return; // Already checked and correct, don't re-evaluate
                }

                if (actual === expected) {
                    feedbackSpan.innerHTML = '✔️ Correct!';
                    feedbackSpan.style.color = varToHex('--correct-color');
                    input.style.borderColor = varToHex('--correct-color');
                    input.disabled = true;
                    correctCount++;
                } else {
                    feedbackSpan.innerHTML = '❌ Try again.';
                    feedbackSpan.style.color = varToHex('--incorrect-color');
                    input.style.borderColor = varToHex('--incorrect-color');
                }
            });

            writingCorrectCount = correctCount;
            updateScore();
        }

        function resetWritingGaps() {
            document.querySelectorAll('#writing-sentences-container input').forEach((input, index) => {
                input.value = '';
                input.style.borderColor = varToHex('--secondary-color');
                input.disabled = false;
                document.getElementById(`write-feedback-${index}`).innerHTML = '';
            });
            writingCorrectCount = 0;
            updateScore();
        }

        // --- 3. MATCH DEFINITIONS ---
        function generateMatchDefs() {
            const wordsContainer = document.getElementById('match-words-container');
            const defsContainer = document.getElementById('match-definitions-container');
            wordsContainer.innerHTML = '';
            defsContainer.innerHTML = '';
            selectedWordMatch = null;
            selectedDefinitionMatch = null;
            matchingCorrectCount = 0;
            updateScore();

            const words = shuffleArray(vocabData.map((item, index) => ({ id: `word-${index}`, text: item.word, answer: `def-${index}` })));
            const definitions = shuffleArray(vocabData.map((item, index) => ({ id: `def-${index}`, text: item.definition, answer: `word-${index}` })));

            words.forEach(item => {
                const div = document.createElement('div');
                div.className = 'match-item match-word';
                div.id = item.id;
                div.setAttribute('data-answer', item.answer);
                div.setAttribute('onclick', 'selectMatchItem(this, "word")');
                div.innerText = item.text;
                wordsContainer.appendChild(div);
            });

            definitions.forEach(item => {
                const div = document.createElement('div');
                div.className = 'match-item match-definition';
                div.id = item.id;
                div.setAttribute('data-answer', item.answer);
                div.setAttribute('onclick', 'selectMatchItem(this, "definition")');
                div.innerText = item.text;
                defsContainer.appendChild(div);
            });
        }

        function selectMatchItem(element, type) {
            if (element.classList.contains('match-correct')) return;

            // Clear previous selection of the same type
            document.querySelectorAll(`.match-${type}`).forEach(item => item.classList.remove('match-selected', 'match-incorrect'));

            element.classList.add('match-selected');

            if (type === 'word') {
                selectedWordMatch = element;
            } else {
                selectedDefinitionMatch = element;
            }

            if (selectedWordMatch && selectedDefinitionMatch) {
                checkMatch();
            }
        }

        function checkMatch() {
            const word = selectedWordMatch;
            const definition = selectedDefinitionMatch;

            if (word.getAttribute('data-answer') === definition.id) {
                // Correct Match
                word.classList.add('match-correct');
                definition.classList.add('match-correct');
                matchingCorrectCount++;
                updateScore();
            } else {
                // Incorrect Match
                word.classList.add('match-incorrect');
                definition.classList.add('match-incorrect');
                setTimeout(() => {
                    word.classList.remove('match-incorrect');
                    definition.classList.remove('match-incorrect');
                }, 800);
            }

            // Clear selections
            selectedWordMatch = null;
            selectedDefinitionMatch = null;
            setTimeout(() => {
                document.querySelectorAll('.match-item').forEach(item => item.classList.remove('match-selected'));
            }, 500);
        }

        // --- 4. FILL IN THE GAPS (PRONUNCIATION) ---
        function generatePronunciationGaps() {
            const container = document.getElementById('pron-sentences-container');
            const bank = document.getElementById('pron-word-bank');
            container.innerHTML = '';
            bank.innerHTML = '';
            pronCorrectCount = 0;
            updateScore();
            Object.keys(pronResults).forEach(key => pronResults[key] = false); // Reset results

            // Generate Word Bank
            shuffleArray([...vocabData]).forEach(item => {
                const span = document.createElement('span');
                span.innerText = item.word;
                bank.appendChild(span);
            });

            // Generate Sentences (Shuffled)
            shuffleArray([...vocabData]).forEach((item, index) => {
                const sentence = item.pronSentence;
                const expectedWord = item.word;
                const blankPlaceholder = `<span class="pron-blank" id="pron-gap-${index}">?</span>`;
                const sentenceHTML = sentence.replace('___', blankPlaceholder);

                const div = document.createElement('div');
                div.className = 'pron-sentence';
                div.innerHTML = `
                    <p>
                        ${sentenceHTML}
                    </p>
                    <button class="mic-button" data-expected="${expectedWord}" data-index="${index}" onclick="startSpeechRecognition(this)">🎙️</button>
                    <span id="pron-feedback-${index}" class="pron-feedback"></span>
                `;
                container.appendChild(div);
                pronResults[expectedWord] = false;
            });

            if (!recognitionFallback) {
                console.warn("Speech Recognition is not fully supported in this browser. The pronunciation exercise may not work.");
            }
        }

        let recognition = null;
        let isListening = false;
        let currentMicButton = null;

        function startSpeechRecognition(button) {
            if (!recognitionFallback) {
                alert("Speech Recognition not supported in your browser.");
                return;
            }

            if (isListening) {
                // If already listening, stop the current session
                if (recognition) recognition.stop();
                return;
            }

            const expectedWord = button.getAttribute('data-expected');
            const index = button.getAttribute('data-index');
            const gapElement = document.getElementById(`pron-gap-${index}`);
            const feedbackElement = document.getElementById(`pron-feedback-${index}`);

            // If already correct, do nothing
            if (pronResults[expectedWord]) return;

            // Reset UI for new attempt
            gapElement.innerText = '?';
            gapElement.classList.remove('pron-correct');
            feedbackElement.innerText = '';
            
            // Highlight button
            currentMicButton = button;
            currentMicButton.classList.add('mic-listening');
            isListening = true;

            const SpeechRecognition = window.SpeechRecognition || window.webkitSpeechRecognition;
            recognition = new SpeechRecognition();
            recognition.continuous = false;
            recognition.interimResults = false;
            recognition.lang = 'en-US';

            recognition.onresult = (event) => {
                const transcript = event.results[0][0].transcript.toLowerCase().trim();
                const cleanTranscript = transcript.replace(/\s/g, ''); 
                const cleanExpected = expectedWord.toLowerCase().trim().replace(/\s/g, '');

                if (cleanTranscript === cleanExpected) {
                    if (!pronResults[expectedWord]) {
                        pronResults[expectedWord] = true;
                        pronCorrectCount++;
                        updateScore();
                    }
                    gapElement.innerText = expectedWord;
                    gapElement.classList.add('pron-correct');
                    feedbackElement.innerText = '✅ Success!';
                    feedbackElement.style.color = varToHex('--correct-color');
                } else {
                    feedbackElement.innerText = `❌ Heard: "${transcript}". Try again.`;
                    feedbackElement.style.color = varToHex('--incorrect-color');
                }
            };

            recognition.onerror = (event) => {
                console.error('Speech recognition error:', event.error);
                feedbackElement.innerText = `⚠️ Error: ${event.error}.`;
                feedbackElement.style.color = '#FF9800';
                stopListeningUI();
            };

            recognition.onend = () => {
                stopListeningUI();
            };

            recognition.start();
            feedbackElement.innerText = '...Listening...';
            feedbackElement.style.color = varToHex('--primary-color');
        }

        function stopListeningUI() {
            if (currentMicButton) {
                currentMicButton.classList.remove('mic-listening');
            }
            isListening = false;
            currentMicButton = null;
        }

        // --- INITIALIZATION ---
        document.addEventListener('DOMContentLoaded', () => {
            generateVocabList();
            generateWritingGaps();
            generateMatchDefs();
            generatePronunciationGaps();
            updateScore();
            showSection('vocab-list', document.querySelector('.nav-buttons button:first-child'));
        });
    </script>
</body>
</html>
