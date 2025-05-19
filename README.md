# Match-Enigma-Game 
<!DOCTYPE html>
<html lang="pt-br">
<head>
  <meta charset="UTF-8" />
  <meta name="viewport" content="width=device-width, initial-scale=1.0" />
  <title>Jogo de Enigmas Matemáticos</title>
  <style>
    body {
      font-family: Arial, sans-serif;
      background-color: #f4f4f4;
      display: flex;
      flex-direction: column;
      align-items: center;
      justify-content: center;
      height: 100vh;
      margin: 0;
    }
    .container {
      background: white;
      padding: 30px;
      border-radius: 12px;
      box-shadow: 0 4px 12px rgba(0,0,0,0.1);
      text-align: center;
      width: 90%;
      max-width: 400px;
    }
    input {
      padding: 10px;
      font-size: 16px;
      width: 100px;
      margin-bottom: 15px;
    }
    button {
      padding: 10px 20px;
      font-size: 16px;
      border: none;
      background-color: #28a745;
      color: white;
      border-radius: 6px;
      cursor: pointer;
    }
    button:hover {
      background-color: #218838;
    }
    .result {
      margin-top: 15px;
      font-size: 18px;
    }
  </style>
</head>
<body>
  <div class="container">
    <h2>Desafio Matemático</h2>
    <p id="question">Carregando desafio...</p>
    <input type="number" id="answer" placeholder="Sua resposta" />
    <br />
    <button onclick="checkAnswer()">Verificar</button>
    <div class="result" id="result"></div>
    <br />
    <button onclick="nextQuestion()">Próximo desafio</button>
    <p>Acertos: <span id="score">0</span></p>
  </div>

  <script>
    const challenges = [
      { number: "8421", answer: 63 },
      { number: "7315", answer: 58 },
      { number: "6207", answer: 55 },
      { number: "5102", answer: 49 },
      { number: "9643", answer: 53 },
      { number: "8716", answer: 71 - 16 },
      { number: "4209", answer: 42 - 9 },
    ];

    let current = 0;
    let score = 0;

    function loadQuestion() {
      document.getElementById("question").textContent =
        challenges[current].number + " = ?";
      document.getElementById("answer").value = "";
      document.getElementById("result").textContent = "";
    }

    function checkAnswer() {
      const userAnswer = parseInt(document.getElementById("answer").value);
      if (userAnswer === challenges[current].answer) {
        document.getElementById("result").textContent = "✅ Correto!";
        score++;
        document.getElementById("score").textContent = score;
      } else {
        document.getElementById("result").textContent = "❌ Tente novamente.";
      }
    }

    function nextQuestion() {
      current++;
      if (current >= challenges.length) {
        alert("Fim dos desafios! Seu total de acertos foi: " + score);
        current = 0;
        score = 0;
        document.getElementById("score").textContent = 0;
      }
      loadQuestion();
    }

    // Inicializa o jogo
    window.onload = loadQuestion;
  </script>
</body>
</html>
