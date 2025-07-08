## Hi there 👋

<!--
**SpectralworksAi/SpectralworksAi** is a ✨ _special_ ✨ repository because its `README.md` (this file) appears on your GitHub profile.

Here are some ideas to get you started:

- 🔭 I’m currently working on ...
- 🌱 I’m currently learning ...
- 👯 I’m looking to collaborate on ...
- 🤔 I’m looking for help with ...
- 💬 Ask me about ...
- 📫 How to reach me: ...
- 😄 Pronouns: ...
- ⚡ Fun fact: ...
-->




<!DOCTYPE html> <html lang="en"> <head> <meta charset="UTF-8"> <meta name="viewport" content="width=device-width, initial-scale=1.0"> <title>ÖLIVERSE v0.3a - Emotional OS</title> <style> /* General Styling */ * { margin: 0; padding: 0;

pasted


Claude
Pasted content
22.77 KB •590 lines
Formatting may be inconsistent from source

<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>ÖLIVERSE v0.3a - Emotional OS</title>
    <style>
        /* General Styling */
        * {
            margin: 0;
            padding: 0;
            box-sizing: border-box;
        }

        body {
            font-family: 'Courier New', monospace;
            background: linear-gradient(135deg, #0a0a0a 0%, #1a1a2e 50%, #16213e 100%);
            color: #e0e0e0;
            min-height: 100vh;
            overflow-x: hidden;
            display: flex;
            flex-direction: column;
        }

        .container {
            max-width: 1200px;
            margin: 0 auto;
            padding: 20px;
            flex-grow: 1; /* Allow container to grow */
        }

        /* Header */
        .header {
            text-align: center;
            margin-bottom: 40px;
            background: rgba(255, 255, 255, 0.05);
            border-radius: 20px;
            padding: 30px;
            border: 1px solid rgba(255, 255, 255, 0.1);
            backdrop-filter: blur(10px);
        }

        .header h1 {
            font-size: 2.5rem;
            background: linear-gradient(45deg, #ff6b6b, #4ecdc4, #45b7d1);
            -webkit-background-clip: text;
            -webkit-text-fill-color: transparent;
            background-clip: text;
            margin-bottom: 10px;
            animation: glow 3s ease-in-out infinite alternate;
        }

        @keyframes glow {
            from { filter: drop-shadow(0 0 5px rgba(78, 205, 196, 0.5)); }
            to { filter: drop-shadow(0 0 20px rgba(78, 205, 196, 0.8)); }
        }

        .header p {
            font-size: 1.1rem;
            color: #b0b0b0;
            margin-bottom: 20px;
        }

        /* Modules Grid */
        .modules {
            display: grid;
            grid-template-columns: repeat(auto-fit, minmax(350px, 1fr));
            gap: 30px;
            margin-bottom: 40px;
        }

        .module {
            background: rgba(255, 255, 255, 0.05);
            border-radius: 20px;
            padding: 30px;
            border: 1px solid rgba(255, 255, 255, 0.1);
            backdrop-filter: blur(10px);
            transition: all 0.3s ease;
            position: relative;
            overflow: hidden;
        }

        .module::before {
            content: '';
            position: absolute;
            top: -50%;
            left: -50%;
            width: 200%;
            height: 200%;
            background: linear-gradient(45deg, transparent, rgba(78, 205, 196, 0.1), transparent);
            transform: rotate(45deg);
            transition: all 0.3s ease;
            opacity: 0;
        }

        .module:hover::before {
            opacity: 1;
            animation: shimmer 2s infinite;
        }

        @keyframes shimmer {
            0% { transform: rotate(45deg) translateX(-100%); }
            100% { transform: rotate(45deg) translateX(100%); }
        }

        .module:hover {
            transform: translateY(-5px);
            box-shadow: 0 20px 40px rgba(0, 0, 0, 0.3);
        }

        .module h2 {
            color: #4ecdc4;
            margin-bottom: 20px;
            font-size: 1.5rem;
            position: relative;
            z-index: 1;
        }

        /* Glyph Input */
        .glyph-input {
            display: flex;
            gap: 15px;
            margin-bottom: 20px;
            flex-wrap: wrap;
        }

        .glyph-btn {
            background: linear-gradient(45deg, #ff6b6b, #4ecdc4);
            border: none;
            border-radius: 15px;
            color: white;
            font-size: 1.5rem;
            padding: 15px 20px;
            cursor: pointer;
            transition: all 0.3s ease;
            font-family: 'Courier New', monospace;
            position: relative;
            overflow: hidden;
            flex-shrink: 0; /* Prevent buttons from shrinking */
        }

        .glyph-btn::before {
            content: '';
            position: absolute;
            top: 50%;
            left: 50%;
            width: 0;
            height: 0;
            background: rgba(255, 255, 255, 0.3);
            border-radius: 50%;
            transform: translate(-50%, -50%);
            transition: all 0.3s ease;
        }

        .glyph-btn:hover::before {
            width: 100%;
            height: 100%;
        }

        .glyph-btn:hover {
            transform: scale(1.1);
            box-shadow: 0 10px 20px rgba(0, 0, 0, 0.3);
        }

        .glyph-btn.active {
            background: linear-gradient(45deg, #45b7d1, #96ceb4);
            transform: scale(1.05);
            animation: pulse 0.5s ease-in-out;
        }

        @keyframes pulse {
            0% { transform: scale(1); }
            50% { transform: scale(1.2); }
            100% { transform: scale(1.05); }
        }

        /* Output Areas */
        .output-area {
            background: rgba(0, 0, 0, 0.3);
            border-radius: 15px;
            padding: 20px;
            margin-top: 20px;
            min-height: 120px;
            border: 1px solid rgba(255, 255, 255, 0.1);
            backdrop-filter: blur(5px);
        }
        
        .output-area strong {
            color: #ff6b6b;
        }

        /* Journal Template */
        .journal-template {
            background: rgba(0, 0, 0, 0.3);
            border-radius: 15px;
            padding: 20px;
            margin-top: 20px;
            border: 1px solid rgba(255, 255, 255, 0.1);
            backdrop-filter: blur(5px);
        }

        .journal-entry {
            margin-bottom: 20px;
        }

        .journal-entry label {
            display: block;
            color: #4ecdc4;
            margin-bottom: 8px;
            font-weight: bold;
        }

        .journal-entry textarea {
            width: 100%;
            background: rgba(255, 255, 255, 0.05);
            border: 1px solid rgba(255, 255, 255, 0.1);
            border-radius: 10px;
            padding: 15px;
            color: #e0e0e0;
            font-family: 'Courier New', monospace;
            resize: vertical;
            min-height: 80px;
            transition: all 0.3s ease;
        }

        .journal-entry textarea:focus {
            outline: none;
            border-color: #4ecdc4;
            box-shadow: 0 0 10px rgba(78, 205, 196, 0.3);
        }

        .journal-entry textarea::placeholder {
            color: #888;
        }

        /* Memory Triad */
        .memory-triad {
            display: grid;
            grid-template-columns: repeat(auto-fit, minmax(200px, 1fr));
            gap: 20px;
            margin-top: 20px;
        }

        .triad-step {
            background: rgba(255, 255, 255, 0.05);
            border-radius: 15px;
            padding: 20px;
            border: 1px solid rgba(255, 255, 255, 0.1);
            text-align: center;
            transition: all 0.3s ease;
        }

        .triad-step:hover {
            transform: translateY(-3px);
            box-shadow: 0 10px 20px rgba(0, 0, 0, 0.2);
        }

        .triad-step h3 {
            color: #ff6b6b;
            margin-bottom: 10px;
            font-size: 1.3rem;
        }

        .triad-step p {
            color: #b0b0b0;
            margin-bottom: 15px;
        }

        .triad-input {
            width: 100%;
            background: rgba(255, 255, 255, 0.05);
            border: 1px solid rgba(255, 255, 255, 0.1);
            border-radius: 10px;
            padding: 15px;
            color: #e0e0e0;
            font-family: 'Courier New', monospace;
            min-height: 80px;
            resize: vertical;
            transition: all 0.3s ease;
        }

        .triad-input:focus {
            outline: none;
            border-color: #ff6b6b;
            box-shadow: 0 0 10px rgba(255, 107, 107, 0.3);
        }

        /* Music Visualizer Placeholder */
        .music-visualizer {
            display: flex;
            justify-content: center;
            align-items: center;
            height: 150px; /* Placeholder height */
            background: rgba(0, 0, 0, 0.3);
            border-radius: 15px;
            margin-top: 20px;
            border: 1px solid rgba(255, 255, 255, 0.1);
            color: #b0b0b0;
            font-size: 1.2rem;
            text-align: center;
            position: relative;
            overflow: hidden;
        }
        .music-visualizer::before {
            content: '';
            position: absolute;
            width: 100%;
            height: 100%;
            background: linear-gradient(45deg, rgba(78, 205, 196, 0.2), transparent, rgba(255, 107, 107, 0.2));
            background-size: 200% 200%;
            animation: gradient-move 10s ease infinite alternate;
            z-index: 0;
        }
        @keyframes gradient-move {
            0% { background-position: 0% 50%; }
            100% { background-position: 100% 50%; }
        }
        .music-visualizer p {
            z-index: 1; /* Keep text above background effect */
            background: rgba(0,0,0,0.5); /* Slightly opaque background for readability */
            padding: 10px 20px;
            border-radius: 8px;
        }

        /* Footer */
        .footer {
            text-align: center;
            padding: 20px;
            margin-top: 40px;
            color: #888;
            font-size: 0.9rem;
            border-top: 1px solid rgba(255, 255, 255, 0.05);
        }

        /* Responsive adjustments */
        @media (max-width: 768px) {
            .header h1 {
                font-size: 2rem;
            }
            .modules {
                grid-template-columns: 1fr;
            }
            .glyph-btn {
                font-size: 1.2rem;
                padding: 12px 18px;
            }
            .memory-triad {
                grid-template-columns: 1fr;
            }
        }
    </style>
</head>
<body>
    <div class="container">
        <header class="header">
            <h1>ÖLIVERSE v0.3a - Emotional OS</h1>
            <p>Decoding and Harmonizing the Inner Cosmos</p>
            <p class="text-purple-200">Current System Time: July 8, 2025, 1:32:36 PM EDT (Toronto, Ontario, Canada)</p>
        </header>

        <main class="modules">
            <section class="module">
                <h2>// EMOTION GLYPH SEQUENCE //</h2>
                <div class="glyph-input" id="glyphButtons">
                    <button class="glyph-btn" data-glyph="✨">✨</button>
                    <button class="glyph-btn" data-glyph="💭">💭</button>
                    <button class="glyph-btn" data-glyph="⚡">⚡</button>
                    <button class="glyph-btn" data-glyph="〰️">〰️</button>
                    <button class="glyph-btn" data-glyph="🔮">🔮</button>
                    <button class="glyph-btn" data-glyph="💧">💧</button>
                    <button class="glyph-btn" data-glyph="⚙️">⚙️</button>
                    <button class="glyph-btn" data-glyph="🌱">🌱</button>
                    <button class="glyph-btn" data-glyph="🌌">🌌</button>
                    <button class="glyph-btn" data-glyph="🔗">🔗</button>
                    <button class="glyph-btn" data-glyph="⏳">⏳</button>
                </div>
                <div class="output-area">
                    <p id="glyphDisplay">Select glyphs to build your emotional sequence</p>
                    <p id="emotionInterpretation" style="margin-top: 10px;"><strong>Emotional Interpretation:</strong> Choose glyphs above to see their meaning</p>
                </div>
                <button 
                    class="flex items-center gap-2 px-4 py-2 mt-4 bg-purple-600 hover:bg-purple-700 disabled:bg-gray-600 rounded-lg transition-colors"
                    onclick="triggerEmotionalMusicSimulation()"
                    style="display: block; margin: 20px auto 0; padding: 15px 30px; font-size: 1.1rem; border-radius: 10px; background: linear-gradient(45deg, #4ecdc4, #45b7d1); color: white; border: none; cursor: pointer; transition: all 0.3s ease;"
                >
                    Simulate Music for State
                </button>
            </section>

            <section class="module">
                <h2>// ÖS JOURNALING //</h2>
                <div class="journal-template">
                    <div class="journal-entry">
                        <label for="eventDescription">Event/Catalyst:</label>
                        <textarea id="eventDescription" placeholder="Describe what happened or triggered this moment..."></textarea>
                    </div>
                    <div class="journal-entry">
                        <label for="initialFeeling">Initial Emotional Response:</label>
                        <textarea id="initialFeeling" placeholder="How did you first feel?"></textarea>
                    </div>
                    <div class="journal-entry">
                        <label for="reflectionInsight">Reflection/Insight:</label>
                        <textarea id="reflectionInsight" placeholder="What did you learn or realize?"></textarea>
                    </div>
                    <button 
                        class="flex items-center gap-2 px-4 py-2 mt-4 bg-purple-600 hover:bg-purple-700 disabled:bg-gray-600 rounded-lg transition-colors"
                        onclick="captureJournalEntry()"
                        style="display: block; margin: 20px auto 0; padding: 15px 30px; font-size: 1.1rem; border-radius: 10px; background: linear-gradient(45deg, #ff6b6b, #ee9b00); color: white; border: none; cursor: pointer; transition: all 0.3s ease;"
                    >
                        Capture to ÖS Memory
                    </button>
                    <div class="output-area" id="journalFeedback" style="margin-top: 20px;">
                        <p>Journal entries are processed and integrated into your ÖS Memory Matrix.</p>
                    </div>
                </div>
            </section>
        </main>

        <section class="module">
            <h2>// EMOTIONAL SONIFICATION //</h2>
            <div class="music-visualizer" id="musicSimulationOutput">
                <p>Music simulation results will appear here after analysis.</p>
            </div>
            <div class="output-area" style="margin-top: 20px;">
                <p><strong>Your Simulated Emotional State:</strong> <span id="simulatedEmotionText">Awaiting analysis...</span></p>
                <p style="margin-top: 10px;"><strong>Music Characteristics:</strong> <span id="musicCharacteristicsText">Awaiting analysis...</span></p>
            </div>
        </section>

        <section class="module">
            <h2>// ÖLIVERSE MEMORY MATRIX //</h2>
            <div id="oliverseMemoryRoot" style="min-height: 600px; display: flex; align-items: center; justify-content: center; background: rgba(0,0,0,0.3); border-radius: 15px; border: 1px solid rgba(255,255,255,0.1);">
                <p style="color: #b0b0b0;">(React ÖliverseMemory component would render here, showing the constellation of your thoughts)</p>
            </div>
            <div class="output-area" style="margin-top: 20px;">
                <p><strong>Memory Status:</strong> Connected to ÖS Core.</p>
                <p id="memoryActivityText" style="margin-top: 10px;">Monitor memory formation and recall in the visualizer above.</p>
            </div>
        </section>


    </div>

    <footer class="footer">
        ÖLIVERSE OS v0.3a © 2025. All rights reserved.
    </footer>

    <script>
        // Placeholder for the React component mounting
        // In a real application, you'd use ReactDOM.render(<ÖliverseMemory />, document.getElementById('oliverseMemoryRoot'));
        // For this simulation, we'll just show the placeholder text.

        let currentGlyphs = [];

        const glyphMappings = {
            '✨': { meaning: 'Curiosity, Discovery, Glimmer of Hope' },
            '💭': { meaning: 'Introspection, Deep Thought, Contemplation' },
            '⚡': { meaning: 'Sudden Insight, Energy Burst, Shock' },
            '〰️': { meaning: 'Flow, Fluidity, Ambiguity, Undulation' },
            '🔮': { meaning: 'Anticipation, Prediction, Foresight' },
            '💧': { meaning: 'Subtlety, Gradual Change, Emotion welling up' },
            '⚙️': { meaning: 'Analytical, Mechanical, Structured Thought' },
            '🌱': { meaning: 'Growth, New Beginnings, Potential' },
            '🌌': { meaning: 'Vastness, Wonder, Existentialism' },
            '🔗': { meaning: 'Connection, Interdependence, Linkage' },
            '⏳': { meaning: 'Patience, Passage of Time, Impermanence' }
        };

        document.addEventListener('DOMContentLoaded', () => {
            const glyphButtonsContainer = document.getElementById('glyphButtons');
            Object.keys(glyphMappings).forEach(glyph => {
                const button = document.createElement('button');
                button.className = 'glyph-btn';
                button.textContent = glyph;
                button.dataset.glyph = glyph;
                button.onclick = () => addGlyph(glyph);
                glyphButtonsContainer.appendChild(button);
            });

            // Initial display update
            updateGlyphDisplay();
            updateEmotionInterpretation();
        });

        function addGlyph(glyph) {
            const index = currentGlyphs.indexOf(glyph);
            const button = document.querySelector(`.glyph-btn[data-glyph="${glyph}"]`);

            if (index === -1) {
                currentGlyphs.push(glyph);
                button.classList.add('active');
            } else {
                currentGlyphs.splice(index, 1); // toggle off
                button.classList.remove('active');
            }
            updateGlyphDisplay();
            updateEmotionInterpretation();
        }

        function updateGlyphDisplay() {
            const display = document.getElementById('glyphDisplay');
            display.textContent = currentGlyphs.join(' ') || 'Select glyphs to build your emotional sequence';
        }

        function updateEmotionInterpretation() {
            const interp = document.getElementById('emotionInterpretation');
            if (currentGlyphs.length === 0) {
                interp.innerHTML = '<strong>Emotional Interpretation:</strong> Choose glyphs above to see their meaning';
                return;
            }
            let meanings = currentGlyphs.map(g => glyphMappings[g].meaning).join(', ');
            interp.innerHTML = `<strong>Emotional Interpretation:</strong> ${meanings}`;
        }

        function triggerEmotionalMusicSimulation() {
            const simulatedEmotionEl = document.getElementById('simulatedEmotionText');
            const musicCharacteristicsEl = document.getElementById('musicCharacteristicsText');
            const musicVisualizer = document.getElementById('musicSimulationOutput');

            // Simulate the emotional state based on the current glyphs or a default if none selected
            let simulatedEmotion = "Introspective Contemplation with Glimmers of Analytical Playfulness and Underlying Flux.";
            let musicCharacteristics = `
                **Tempo:** Andante Moderato (80-92 BPM).<br/>
                **Drums (Glass & Metal):** Crystalline, resonant, sharp, sparse, irregular, sometimes gated hits.<br/>
                **String Quartet (Pizzicato):** Sharp, bouncy, distinct, short melodic fragments, call-and-response.<br/>
                **Evolving Pad:** Lush, atmospheric, slow-moving, gradual timbral shifts, often gated for rhythmic "breaths".<br/>
                **Gated Effect:** Applied rhythmically across instruments, creating intermittent, precise sounds.
            `;
            let visualizerContent = `
                <p>Now processing your emotional signature...</p>
                <p style="margin-top: 10px;">[Visualizer shows abstract patterns, resonant waves, and sharp glints of light, reflecting the music characteristics]</p>
            `;

            if (currentGlyphs.length > 0) {
                const interpretations = currentGlyphs.map(g => glyphMappings[g].meaning);
                const uniqueMeanings = [...new Set(interpretations)]; // Remove duplicates
                
                // A simplified way to derive a combined emotional state from glyphs for display
                if (uniqueMeanings.includes("Introspection, Deep Thought, Contemplation") && uniqueMeanings.includes("Analytical, Mechanical, Structured Thought")) {
                    simulatedEmotion = "Focused Analytical Contemplation.";
                } else if (uniqueMeanings.includes("Curiosity, Discovery, Glimmer of Hope") && uniqueMeanings.includes("Growth, New Beginnings, Potential")) {
                    simulatedEmotion = "Hopeful Exploration and Emerging Growth.";
                } else {
                    simulatedEmotion = "A complex state woven from: " + uniqueMeanings.join(", ") + ".";
                }
            }

            simulatedEmotionEl.textContent = simulatedEmotion;
            musicCharacteristicsEl.innerHTML = musicCharacteristics; // Use innerHTML for line breaks
            musicVisualizer.innerHTML = visualizerContent;

            // Optional: A more dynamic visualizer could be implemented with D3.js or a canvas element
            // For now, it's illustrative text.
            setTimeout(() => {
                musicVisualizer.innerHTML = `
                    <p style="font-size: 1.5rem; color: #4ecdc4;">🎶 Emotional Sonification Complete 🎶</p>
                    <p style="margin-top: 10px;">Listen closely to your inner symphony...</p>
                `;
            }, 2000); // Simulate processing time
        }

        function captureJournalEntry() {
            const eventDesc = document.getElementById('eventDescription').value;
            const initialFeel = document.getElementById('initialFeeling').value;
            const reflection = document.getElementById('reflectionInsight').value;
            const journalFeedback = document.getElementById('journalFeedback');

            if (eventDesc || initialFeel || reflection) {
                const timestamp = new Date().toLocaleString();
                const entry = {
                    timestamp,
                    eventDesc,
                    initialFeel,
                    reflection
                };
                console.log("Journal Entry Captured:", entry);
                journalFeedback.innerHTML = `<p style="color: #96ceb4;">Journal entry captured to ÖS Memory Matrix at ${timestamp}.</p>`;
                // In a real app, you'd send this to a backend or state management system.
                // Clear fields
                document.getElementById('eventDescription').value = '';
                document.getElementById('initialFeeling').value = '';
                document.getElementById('reflectionInsight').value = '';
            } else {
                journalFeedback.innerHTML = `<p style="color: #ff6b6b;">Please write something in your journal before capturing.</p>`;
            }
        }
    </script>
</body>
</html>