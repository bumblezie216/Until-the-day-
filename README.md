<html lang="en">
<head>
<meta charset="UTF-8">
<meta name="viewport" content="width=device-width, initial-scale=1.0">
<title>Pink Piano ♡</title>

<style>
* {
    box-sizing: border-box;
    -webkit-tap-highlight-color: transparent;
}

html, body {
    margin: 0;
    min-height: 100%;
}

body {
    min-height: 100vh;
    display: flex;
    justify-content: center;
    align-items: center;
    overflow-x: hidden;
    font-family: Georgia, "Times New Roman", serif;
    background:
        radial-gradient(circle at 20% 10%, #fff0f8 0%, transparent 25%),
        radial-gradient(circle at 85% 15%, #ffd0e7 0%, transparent 25%),
        linear-gradient(145deg, #f7b4d2, #e77cac 50%, #b9477d);
    color: #6c1747;
}

.page {
    width: 100%;
    max-width: 1100px;
    padding: 25px 14px 40px;
    text-align: center;
}

.title {
    margin: 0;
    color: white;
    font-size: clamp(2.3rem, 7vw, 4.8rem);
    text-shadow: 0 5px 15px rgba(91, 17, 58, 0.3);
    letter-spacing: 1px;
}

.subtitle {
    color: white;
    margin: 7px 0 25px;
    font-size: clamp(0.9rem, 2.5vw, 1.15rem);
}

.piano-shell {
    background:
        linear-gradient(145deg, #ffcae3, #f494c0 55%, #df6ba4);
    border: 2px solid rgba(255,255,255,0.6);
    border-radius: 28px;
    padding: clamp(12px, 3vw, 25px);
    box-shadow:
        0 25px 50px rgba(91, 17, 58, 0.35),
        inset 0 2px 5px rgba(255,255,255,0.8);
}

.piano {
    position: relative;
    display: flex;
    width: 100%;
    height: clamp(230px, 48vw, 390px);
    user-select: none;
    touch-action: none;
}

/* WHITE KEYS */

.white-key {
    position: relative;
    flex: 1;
    min-width: 0;
    height: 100%;
    background: linear-gradient(
        to right,
        #fff,
        #fffafd 50%,
        #f8eaf3
    );
    border: 1px solid #d58aae;
    border-bottom: 8px solid #c36a97;
    border-radius: 0 0 12px 12px;
    box-shadow:
        inset 0 -15px 20px rgba(192, 87, 139, 0.09),
        0 5px 8px rgba(87, 16, 55, 0.22);
    cursor: pointer;
    display: flex;
    justify-content: center;
    align-items: flex-end;
    padding-bottom: 17px;
    z-index: 1;
    transition:
        transform 0.07s ease,
        background 0.07s ease;
}

.white-key.active {
    transform: translateY(7px);
    background: linear-gradient(
        to bottom,
        #fff1f8,
        #ffc7e1
    );
    border-bottom-width: 3px;
}

.white-key:focus-visible,
.black-key:focus-visible {
    outline: 3px solid white;
    outline-offset: 2px;
}

/* BLACK KEYS */

.black-key {
    position: absolute;
    top: 0;
    width: 7.5%;
    height: 61%;
    background:
        linear-gradient(
            135deg,
            #3a102a,
            #74234f 55%,
            #210918
        );
    border: 2px solid #48132f;
    border-top: 0;
    border-radius: 0 0 9px 9px;
    box-shadow:
        0 8px 10px rgba(47, 8, 29, 0.48),
        inset 2px 0 4px rgba(255,255,255,0.15);
    cursor: pointer;
    z-index: 5;
    transition: transform 0.07s ease;
}

.black-key.active {
    transform: translateY(6px);
    background:
        linear-gradient(
            135deg,
            #8f2f64,
            #bd4f87
        );
}

.white-content {
    pointer-events: none;
    display: flex;
    flex-direction: column;
    align-items: center;
    gap: 5px;
}

.note {
    color: #a33d72;
    font-size: clamp(0.65rem, 2vw, 0.9rem);
}

.keyboard-letter {
    display: inline-flex;
    align-items: center;
    justify-content: center;
    min-width: 31px;
    min-height: 30px;
    padding: 3px 7px;
    border-radius: 8px;
    background: #ffe0ef;
    color: #d23c82;
    font-weight: bold;
    font-size: clamp(0.7rem, 2vw, 1rem);
}

.black-label {
    position: absolute;
    left: 0;
    right: 0;
    bottom: 10px;
    color: #ffd5e9;
    font-weight: bold;
    font-size: clamp(0.6rem, 1.7vw, 0.8rem);
    pointer-events: none;
}

/* CONTROLS */

.controls {
    margin-top: 20px;
    display: flex;
    justify-content: center;
    align-items: center;
    flex-wrap: wrap;
    gap: 10px;
}

.control {
    border: 0;
    border-radius: 999px;
    padding: 12px 19px;
    min-height: 44px;
    background: white;
    color: #a62f69;
    font-family: Georgia, "Times New Roman", serif;
    font-size: 0.95rem;
    font-weight: bold;
    cursor: pointer;
    box-shadow: 0 5px 12px rgba(91, 17, 58, 0.2);
    transition: transform 0.15s ease, background 0.15s ease;
}

.control:hover {
    transform: translateY(-2px);
    background: #fff0f7;
}

.control:active {
    transform: translateY(1px);
}

.recording {
    background: #ffe0ed;
    color: #c51d61;
}

.status {
    min-height: 24px;
    margin-top: 13px;
    color: white;
    font-size: 0.9rem;
    font-weight: bold;
}

/* HELP */

.help {
    margin-top: 17px;
    padding: 14px;
    border-radius: 18px;
    background: rgba(255,255,255,0.2);
    color: white;
    line-height: 1.6;
}

.help strong {
    color: white;
}

/* FLOATING HEARTS */

.heart {
    position: fixed;
    z-index: 100;
    pointer-events: none;
    color: white;
    font-size: 20px;
    animation: floatHeart 1.35s ease-out forwards;
    text-shadow: 0 2px 8px rgba(120,20,75,0.25);
}

@keyframes floatHeart {
    0% {
        opacity: 1;
        transform: translate(-50%, -50%) scale(0.7) rotate(0deg);
    }

    100% {
        opacity: 0;
        transform: translate(-50%, -170px) scale(1.5) rotate(15deg);
    }
}

/* SMALL SCREENS */

@media (max-width: 600px) {

    .page {
        padding-top: 18px;
    }

    .piano-shell {
        padding: 9px;
        border-radius: 20px;
    }

    .piano {
        height: 235px;
    }

    .white-key {
        padding-bottom: 10px;
    }

    .keyboard-letter {
        min-width: 25px;
        min-height: 25px;
        padding: 2px 5px;
    }

    .black-key {
        height: 57%;
    }

    .black-label {
        bottom: 7px;
    }

    .control {
        padding: 10px 15px;
    }
}
</style>
</head>

<body>

<main class="page">

    <h1 class="title">♡ Pink Piano ♡</h1>

    <p class="subtitle">
        Tap the keys or use your computer keyboard 🎀
    </p>

    <section class="piano-shell">

        <div
            class="piano"
            id="piano"
            aria-label="Interactive pink piano"
        >

            <!-- WHITE KEYS -->

            <button
                class="white-key"
                data-note="C4"
                data-key="a"
                aria-label="C4, keyboard A"
                type="button"
            >
                <span class="white-content">
                    <span class="note">C4</span>
                    <span class="keyboard-letter">A</span>
                </span>
            </button>

            <button
                class="white-key"
                data-note="D4"
                data-key="s"
                aria-label="D4, keyboard S"
                type="button"
            >
                <span class="white-content">
                    <span class="note">D4</span>
                    <span class="keyboard-letter">S</span>
                </span>
            </button>

            <button
                class="white-key"
                data-note="E4"
                data-key="d"
                aria-label="E4, keyboard D"
                type="button"
            >
                <span class="white-content">
                    <span class="note">E4</span>
                    <span class="keyboard-letter">D</span>
                </span>
            </button>

            <button
                class="white-key"
                data-note="F4"
                data-key="f"
                aria-label="F4, keyboard F"
                type="button"
            >
                <span class="white-content">
                    <span class="note">F4</span>
                    <span class="keyboard-letter">F</span>
                </span>
            </button>

            <button
                class="white-key"
                data-note="G4"
                data-key="g"
                aria-label="G4, keyboard G"
                type="button"
            >
                <span class="white-content">
                    <span class="note">G4</span>
                    <span class="keyboard-letter">G</span>
                </span>
            </button>

            <button
                class="white-key"
                data-note="A4"
                data-key="h"
                aria-label="A4, keyboard H"
                type="button"
            >
                <span class="white-content">
                    <span class="note">A4</span>
                    <span class="keyboard-letter">H</span>
                </span>
            </button>

            <button
                class="white-key"
                data-note="B4"
                data-key="j"
                aria-label="B4, keyboard J"
                type="button"
            >
                <span class="white-content">
                    <span class="note">B4</span>
                    <span class="keyboard-letter">J</span>
                </span>
            </button>

            <button
                class="white-key"
                data-note="C5"
                data-key="k"
                aria-label="C5, keyboard K"
                type="button"
            >
                <span class="white-content">
                    <span class="note">C5</span>
                    <span class="keyboard-letter">K</span>
                </span>
            </button>

            <button
                class="white-key"
                data-note="D5"
                data-key="l"
                aria-label="D5, keyboard L"
                type="button"
            >
                <span class="white-content">
                    <span class="note">D5</span>
                    <span class="keyboard-letter">L</span>
                </span>
            </button>


            <!-- BLACK KEYS -->

            <button
                class="black-key"
                data-note="C#4"
                data-key="w"
                style="left: 7.1%;"
                aria-label="C sharp 4, keyboard W"
                type="button"
            >
                <span class="black-label">W</span>
            </button>

            <button
                class="black-key"
                data-note="D#4"
                data-key="e"
                style="left: 18.2%;"
                aria-label="D sharp 4, keyboard E"
                type="button"
            >
                <span class="black-label">E</span>
            </button>

            <button
                class="black-key"
                data-note="F#4"
                data-key="t"
                style="left: 40.4%;"
                aria-label="F sharp 4, keyboard T"
                type="button"
            >
                <span class="black-label">T</span>
            </button>

            <button
                class="black-key"
                data-note="G#4"
                data-key="y"
                style="left: 51.5%;"
                aria-label="G sharp 4, keyboard Y"
                type="button"
            >
                <span class="black-label">Y</span>
            </button>

            <button
                class="black-key"
                data-note="A#4"
                data-key="u"
                style="left: 62.6%;"
                aria-label="A sharp 4, keyboard U"
                type="button"
            >
                <span class="black-label">U</span>
            </button>

            <button
                class="black-key"
                data-note="C#5"
                data-key="o"
                style="left: 84.8%;"
                aria-label="C sharp 5, keyboard O"
                type="button"
            >
                <span class="black-label">O</span>
            </button>

        </div>


        <div class="controls">

            <button
                class="control"
                id="recordBtn"
                type="button"
            >
                🔴 Record
            </button>

            <button
                class="control"
                id="stopBtn"
                type="button"
            >
                ⏹ Stop
            </button>

            <button
                class="control"
                id="playBtn"
                type="button"
            >
                ▶ Play
            </button>

            <button
                class="control"
                id="clearBtn"
                type="button"
            >
                🗑 Clear
            </button>

        </div>

        <div
            class="status"
            id="status"
            aria-live="polite"
        >
            Ready to play ♡
        </div>

        <div class="help">
            <strong>Keyboard controls</strong><br>
            White keys: A S D F G H J K L<br>
            Black keys: W E T Y U O
        </div>

    </section>

</main>


<script>

const piano = document.getElementById("piano");

const statusText =
    document.getElementById("status");

const recordButton =
    document.getElementById("recordBtn");

const stopButton =
    document.getElementById("stopBtn");

const playButton =
    document.getElementById("playBtn");

const clearButton =
    document.getElementById("clearBtn");


/* -----------------------------
   AUDIO
----------------------------- */

let audioContext = null;
let masterGain = null;

function setupAudio() {

    if (audioContext) {

        if (audioContext.state === "suspended") {
            audioContext.resume();
        }

        return;
    }

    const AudioContext =
        window.AudioContext ||
        window.webkitAudioContext;

    if (!AudioContext) {

        statusText.textContent =
            "Your browser does not support piano audio.";

        return;
    }

    audioContext = new AudioContext();

    masterGain =
        audioContext.createGain();

    masterGain.gain.value = 0.28;

    masterGain.connect(
        audioContext.destination
    );
}


/* -----------------------------
   NOTE FREQUENCIES
----------------------------- */

const frequencies = {

    "C4": 261.63,
    "C#4": 277.18,

    "D4": 293.66,
    "D#4": 311.13,

    "E4": 329.63,

    "F4": 349.23,
    "F#4": 369.99,

    "G4": 392.00,
    "G#4": 415.30,

    "A4": 440.00,
    "A#4": 466.16,

    "B4": 493.88,

    "C5": 523.25,
    "C#5": 554.37,

    "D5": 587.33
};


/* -----------------------------
   PLAY NOTE
----------------------------- */

function playNote(note) {

    setupAudio();

    if (!audioContext || !masterGain) {
        return;
    }

    const frequency =
        frequencies[note];

    if (!frequency) {
        return;
    }

    const oscillator =
        audioContext.createOscillator();

    const gain =
        audioContext.createGain();

    /*
       Triangle gives a softer,
       piano-like electronic sound.
    */

    oscillator.type = "triangle";

    oscillator.frequency.setValueAtTime(
        frequency,
        audioContext.currentTime
    );

    oscillator.connect(gain);
    gain.connect(masterGain);

    const now =
        audioContext.currentTime;

    gain.gain.setValueAtTime(
        0.0001,
        now
    );

    gain.gain.exponentialRampToValueAtTime(
        0.8,
        now + 0.015
    );

    gain.gain.exponentialRampToValueAtTime(
        0.001,
        now + 1.25
    );

    oscillator.start(now);

    oscillator.stop(
        now + 1.3
    );
}


/* -----------------------------
   HEART ANIMATION
----------------------------- */

function createHeart(x, y) {

    const heart =
        document.createElement("div");

    heart.className = "heart";

    const hearts = [
        "♡",
        "♥",
        "♡",
        "✦"
    ];

    heart.textContent =
        hearts[
            Math.floor(
                Math.random() * hearts.length
            )
        ];

    heart.style.left =
        `${x}px`;

    heart.style.top =
        `${y}px`;

    document.body.appendChild(
        heart
    );

    setTimeout(() => {
        heart.remove();
    }, 1400);
}


/* -----------------------------
   RECORDING
----------------------------- */

let recording = false;

let recordedNotes = [];

let recordingStart = 0;


function startRecording() {

    recordedNotes = [];

    recording = true;

    recordingStart =
        performance.now();

    recordButton.textContent =
        "🔴 Recording...";

    recordButton.classList.add(
        "recording"
    );

    statusText.textContent =
        "Recording your melody ♡";
}


function stopRecording() {

    recording = false;

    recordButton.textContent =
        "🔴 Record";

    recordButton.classList.remove(
        "recording"
    );

    if (recordedNotes.length > 0) {

        statusText.textContent =
            `Recorded ${recordedNotes.length} notes ♡`;

    } else {

        statusText.textContent =
            "Nothing recorded yet ♡";
    }
}


/* -----------------------------
   ACTIVATE KEY
----------------------------- */

function activateKey(
    keyElement,
    shouldRecord = true
) {

    if (!keyElement) {
        return;
    }

    const note =
        keyElement.dataset.note;

    keyElement.classList.add(
        "active"
    );

    playNote(note);

    const rectangle =
        keyElement.getBoundingClientRect();

    createHeart(
        rectangle.left +
        rectangle.width / 2,

        rectangle.top +
        rectangle.height * 0.45
    );

    window.setTimeout(() => {

        keyElement.classList.remove(
            "active"
        );

    }, 120);


    if (
        recording &&
        shouldRecord
    ) {

        recordedNotes.push({

            note: note,

            time:
                performance.now() -
                recordingStart

        });

    }
}


/* -----------------------------
   MOUSE / TOUCH
----------------------------- */

const keys =
    document.querySelectorAll(
        ".white-key, .black-key"
    );

keys.forEach(key => {

    key.addEventListener(
        "pointerdown",
        event => {

            event.preventDefault();

            activateKey(key);

        }
    );

});


/* -----------------------------
   COMPUTER KEYBOARD
----------------------------- */

document.addEventListener(
    "keydown",
    event => {

        /*
           Don't play piano when the user
           is typing into another input.
        */

        const tag =
            event.target.tagName;

        if (
            tag === "INPUT" ||
            tag === "TEXTAREA" ||
            tag === "SELECT"
        ) {
            return;
        }

        if (event.repeat) {
            return;
        }

        const pressed =
            event.key.toLowerCase();

        const matchingKey =
            document.querySelector(
                `[data-key="${pressed}"]`
            );

        if (!matchingKey) {
            return;
        }

        event.preventDefault();

        activateKey(
            matchingKey
        );

    }
);


/* -----------------------------
   BUTTONS
----------------------------- */

recordButton.addEventListener(
    "click",
    () => {

        if (recording) {

            stopRecording();

        } else {

            startRecording();

        }

    }
);


stopButton.addEventListener(
    "click",
    () => {

        stopRecording();

    }
);


clearButton.addEventListener(
    "click",
    () => {

        recordedNotes = [];

        recording = false;

        recordButton.textContent =
            "🔴 Record";

        recordButton.classList.remove(
            "recording"
        );

        statusText.textContent =
            "Recording cleared ♡";

    }
);


/* -----------------------------
   PLAY RECORDED MELODY
----------------------------- */

playButton.addEventListener(
    "click",
    () => {

        if (
            recordedNotes.length === 0
        ) {

            statusText.textContent =
                "Record a melody first ♡";

            return;
        }

        statusText.textContent =
            "Playing your melody 🎶";

        recordedNotes.forEach(
            recorded => {

                window.setTimeout(
                    () => {

                        const key =
                            document.querySelector(
                                `[data-note="${recorded.note}"]`
                            );

                        activateKey(
                            key,
                            false
                        );

                    },
                    recorded.time
                );

            }
        );

        const finalTime =
            recordedNotes[
                recordedNotes.length - 1
            ].time;

        window.setTimeout(
            () => {

                statusText.textContent =
                    "Finished ♡";

            },
            finalTime + 1400
        );

    }
);

</script>

</body>
</html>
