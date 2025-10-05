---
# Feel free to add content and custom Front Matter to this file.
# To modify the layout, see https://jekyllrb.com/docs/themes/#overriding-theme-defaults

layout: home
---
<head>
    <link rel="stylesheet" href="styles.css">
    <script src="https://unpkg.com/wavesurfer.js@7"></script>
    <script src="https://unpkg.com/wavesurfer.js@7/dist/plugins/regions.min.js"></script>
    <script src="https://unpkg.com/wavesurfer.js@7/dist/plugins/hover.min.js"></script>
</head>

<p style="text-align: center; font-weight: bold; font-style: italic">
    Composer Note — “Dreamscape at the Louvre Abu Dhabi”
</p>

<p style="text-align: right; font-style: italic; color: dimgray">
“In dreams, music speaks a language deeper than thought —<br>
and in silence, machines may learn to listen.”
</p>

This piece, _Dreamscape at the Louvre Abu Dhabi_, is a poetic experiment in **co-creation between human and machine**, a musical dream spun in collaboration between intuition and computation. It is the first of its kind to enter the Abu Dhabi International Composition Competition — not composed by a person alone, but by a **dialogue between composer and artificial intelligence**.

Inspired by the ethereal architecture of the Louvre Abu Dhabi, the piece travels through light and shadow, across polyrhythmic textures and tonal ambiguity, drawing on the **romantic color palette of Debussy** and occasional bursts of virtuosity reminiscent of Rachmaninoff, Chopin, and Prokofiev. The result is not merely a stylistic imitation, but a refracted dream — of a museum, of a place, of a time when creativity belongs not only to human minds, but shared with the artificial intelligence.

The compositional process unfolded in a process following the spirit of _"You compose, I listen. I select, you extend. We meet somewhere between rule and impulse."_

- **Initial generation**: The AI system proposed a number of musical sketches in the romantic style.
- **Human curation and arrangement**: A human composer carefully selected and combined the sketches emphasizing emotional narrative and stylistic coherence.
- **AI enhancement and extension**: The AI was then re-engaged to smooth transitions, develop themes, and extend the piece with stylistic nuances.


That said, 100% of the notes is composed by AI, while the overall flow is guided by human composer.

---
This **video demo** show the human-AI co-creation process, where minor artistic treatments are added for storytelling purposes, but the core logic of collaboration remains intact.

<div class="center-stuff">
    <video controls preload="metadata" width="85%" src="assets/ai_composer_demo.mp4"></video>
</div>
<br>

Here is the full music audio from the video:
<div class="audio_wrapper">
<button id="play_btn_full_demo" class="play_btn">▶</button>
<div id="waveform_full_demo" class="waveform"></div>
</div>
<script>
    let currentPlayingAudio = null;
    let currentPlayingBtn = null;
    
    function stopPlaying() {
    if (currentPlayingAudio !== null) {
    currentPlayingAudio.pause();
    currentPlayingBtn.textContent = '▶'
    }
    currentPlayingAudio = null;
    currentPlayingBtn = null;
    }
    
    const wavesurfer = WaveSurfer.create({
    container: `#waveform_full_demo`,
    waveColor: '#B1B1B1',
    progressColor: '#F6B094',
    barWidth: 2,
    interact: true,
    pixelRatio: 1,
    height: 40,
    cursorWidth: 2,
    cursorColor: "red",
    url: "/assets/demo_audio.mp3",
    plugins: [
    WaveSurfer.Hover.create({
    lineColor: '#ff0000',
    lineWidth: 2,
    labelBackground: '#555',
    labelColor: '#fff',
    labelSize: '11px',
    }),
    ],
    });
    wavesurfer.on('finish', () => {
    if (currentPlayingAudio !== null) {
    currentPlayingBtn.textContent = '▶'
    }
    currentPlayingAudio = null;
    currentPlayingBtn = null;
    });
    let btnEle = document.getElementById("play_btn_full_demo");
    btnEle.addEventListener("click", function () {
    if (btnEle.textContent === "▶") {
    stopPlaying();
    btnEle.textContent = '◼';
    wavesurfer.play();
    currentPlayingAudio = wavesurfer;
    currentPlayingBtn = btnEle;
    } else {
    stopPlaying();
    }
    });
</script>
<br>

---
### Sheet Music
<div class="pdf-container">
  <iframe src="/assets/ViewerJS/#/assets/Dreamscape_at_the_Louvre_Abu_Dhabi.pdf" width="100%" height="100%" allowfullscreen webkitallowfullscreen></iframe>
</div>
