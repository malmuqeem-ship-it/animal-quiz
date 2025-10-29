
<!DOCTYPE html>
<html lang="ar">
<head>
<meta charset="UTF-8">
<meta name="viewport" content="width=device-width, initial-scale=1.0">
<title>صدق أو إشاعة عن الحيوانات</title>
<style>
  body {
    background-color: #f4f1e8;
    font-family: "Cairo", sans-serif;
    text-align: center;
    direction: rtl;
    height: 100vh;
    margin: 0;
    display: flex;
    align-items: center;
    justify-content: center;
  }

  h1, h2 {
    color: #2f5132;
    margin-bottom: 10px;
  }

  p {
    color: #3a3a3a;
    font-size: 18px;
  }

  .box {
    background-color: #ffffff;
    border-radius: 15px;
    display: inline-block;
    padding: 25px 30px;
    box-shadow: 0 4px 10px rgba(0,0,0,0.1);
    max-width: 90%;
  }

  button {
    background-color: #6b936b;
    color: white;
    border: none;
    padding: 12px 25px;
    margin: 10px;
    border-radius: 10px;
    font-size: 18px;
    cursor: pointer;
    transition: 0.3s;
  }

  button:hover {
    background-color: #507850;
  }

  #result {
    font-size: 20px;
    margin-top: 20px;
    color: #2b402b;
    font-weight: bold;
  }

  .hidden {
    display: none;
  }

  .start-btn {
    background-color: #4f7850;
  }

  .start-btn:hover {
    background-color: #3b603b;
  }

  .end-btn {
    background-color: #b07d4f;
  }

  .end-btn:hover {
    background-color: #8a6038;
  }
</style>
</head>
<body>

<!-- 🎵 الأصوات -->
<audio id="birds-sound" preload="auto">
  <source src="https://cdn.pixabay.com/download/audio/2022/03/15/audio_48f4cc2b12.mp3?filename=birds-singing-ambient-nature-116199.mp3" type="audio/mpeg">
</audio>

<audio id="click-sound" preload="auto">
  <source src="https://cdn.pixabay.com/download/audio/2022/03/15/audio_c2b1a4b273.mp3?filename=click-button-140881.mp3" type="audio/mpeg">
</audio>

<!-- 🌿 شاشة المقدمة -->
<div id="intro" class="box">
  <h1>🌿 صدق أو إشاعة عن الحيوانات</h1>
  <p>مرحبًا بك في لعبة صدق أو إشاعة عن الحيوانات! 🌾<br>
  اختبر معلوماتك واستمتع باكتشاف حقائق ممتعة عن عالم الصحراء.</p>
  <button class="start-btn" onclick="startGame()">ابدأ اللعبة ▶️</button>
</div>

<!-- 🦌 شاشة السؤال -->
<div id="game" class="box hidden">
  <h2>المها العربي يعيش في الغابات؟</h2>
  <button onclick="checkAnswer(true)">صدق</button>
  <button onclick="checkAnswer(false)">إشاعة</button>
  <p id="result"></p>
  <button id="end-btn" class="end-btn hidden" onclick="endGame()">إنهاء اللعبة 🔁</button>
</div>

<script>
  const birdsSound = document.getElementById("birds-sound");
  const clickSound = document.getElementById("click-sound");
  const intro = document.getElementById("intro");
  const game = document.getElementById("game");
  const result = document.getElementById("result");
  const endBtn = document.getElementById("end-btn");

  // 🔊 السماح بتشغيل الصوت بعد أول تفاعل
  document.addEventListener("click", () => {
    birdsSound.muted = false;
    clickSound.muted = false;
  }, { once: true });

  function startGame() {
    birdsSound.currentTime = 0;
    birdsSound.volume = 0.5;
    birdsSound.play().catch(err => console.log("تعذّر تشغيل الصوت:", err));
    intro.classList.add("hidden");
    game.classList.remove("hidden");
    result.textContent = "";
    endBtn.classList.add("hidden");
  }

  function checkAnswer(answer) {
    clickSound.currentTime = 0;
    clickSound.play().catch(err => console.log("تعذّر تشغيل صوت النقر:", err));
    if (!answer) {
      result.textContent = "✔️ صحيح! المها العربي يعيش في الصحراء وليس في الغابات.";
    } else {
      result.textContent = "❌ خطأ، المها العربي لا يعيش في الغابات.";
    }
    endBtn.classList.remove("hidden");
  }

  function endGame() {
    game.classList.add("hidden");
    intro.classList.remove("hidden");
    birdsSound.pause();
    birdsSound.currentTime = 0;
  }
</script>

</body>
</html>
