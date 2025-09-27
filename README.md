calculadora cientifica
const display = document.getElementById("display");
const historyList = document.getElementById("historyList");

function appendValue(val) {
  display.textContent += val;
}

function clearDisplay() {
  display.textContent = "";
}

function deleteLast() {
  display.textContent = display.textContent.slice(0, -1);
}

function calculateResult() {
  let expression = display.textContent
    .replace(/π/g, "Math.PI")
    .replace(/sqrt\(/g, "Math.sqrt(")
    .replace(/sin\(/g, "Math.sin(")
    .replace(/cos\(/g, "Math.cos(")
    .replace(/tan\(/g, "Math.tan(")
    .replace(/log\(/g, "Math.log10(")
    .replace(/ln\(/g, "Math.log(")
    .replace(/e/g, "Math.E")
    .replace(/\^/g, "**");

  try {
    const result = eval(expression);
    historyList.innerHTML = `<li>${display.textContent} = ${result}</li>` + historyList.innerHTML;
    display.textContent = result;
  } catch (e) {
    display.textContent = "Error";
  }
}

<!DOCTYPE html>
<html lang="es">
<head>
  <meta charset="UTF-8" />
  <meta name="viewport" content="width=device-width, initial-scale=1.0"/>
  <title>Calculadora Científica</title>
  <link rel="stylesheet" href="style.css"/>
</head>
<body>
  <div class="calculator-container">
    <div class="calculator">
      <div class="display" id="display"></div>
      <div class="buttons">
        <!-- Fila 1 -->
        <button onclick="clearDisplay()">C</button>
        <button onclick="deleteLast()">⌫</button>
        <button onclick="appendValue('(')">(</button>
        <button onclick="appendValue(')')">)</button>

        <!-- Fila 2 -->
        <button onclick="appendValue('sin(')">sin</button>
        <button onclick="appendValue('cos(')">cos</button>
        <button onclick="appendValue('tan(')">tan</button>
        <button onclick="appendValue('/')">÷</button>

        <!-- Fila 3 -->
        <button onclick="appendValue('7')">7</button>
        <button onclick="appendValue('8')">8</button>
        <button onclick="appendValue('9')">9</button>
        <button onclick="appendValue('*')">×</button>

        <!-- Fila 4 -->
        <button onclick="appendValue('4')">4</button>
        <button onclick="appendValue('5')">5</button>
        <button onclick="appendValue('6')">6</button>
        <button onclick="appendValue('-')">−</button>

        <!-- Fila 5 -->
        <button onclick="appendValue('1')">1</button>
        <button onclick="appendValue('2')">2</button>
        <button onclick="appendValue('3')">3</button>
        <button onclick="appendValue('+')">+</button>

        <!-- Fila 6 -->
        <button onclick="appendValue('0')">0</button>
        <button onclick="appendValue('.')">.</button>
        <button onclick="calculateResult()">=</button>
        <button onclick="appendValue('^')">^</button>

        <!-- Fila 7 -->
        <button onclick="appendValue('sqrt(')">√</button>
        <button onclick="appendValue('log(')">log</button>
        <button onclick="appendValue('ln(')">ln</button>
        <button onclick="appendValue('pi')">π</button>
      </div>
    </div>

    <div class="history">
      <h2>Historial</h2>
      <ul id="historyList"></ul>
    </div>
  </div>

  <script src="script.js"></script>
</body>
</html>

/*estilo global*/
body {
  margin: 0;
  padding: 0;
  font-family: 'Segoe UI', sans-serif;
  background: radial-gradient(circle at top left, #1f1c2c, #928dab);
  color: #fff;
  display: flex;
  justify-content: center;
  align-items: flex-start;
  min-height: 100vh;
  padding: 30px;
  }

/* Contenedor principal */
.calculator-container {
  display: flex;
  flex-wrap: wrap;
  gap: 20px;
  max-width: 1000px;
  width: 100%;
}

/* Calculadora */
.calculator {
  background: #2d2d44;
  padding: 20px;
  border-radius: 15px;
  box-shadow: 0 10px 25px rgba(0,0,0,0.4);
  flex: 2;
  min-width: 300px;
}

/* Pantalla */
.display {
  background: #000;
  color: #00ffcc;
  padding: 15px;
  font-size: 1.6em;
  border-radius: 10px;
  margin-bottom: 15px;
  word-wrap: break-word;
  min-height: 50px;
}

/* Botones */
.buttons {
  display: grid;
  grid-template-columns: repeat(4, 1fr);
  gap: 10px;
}

button {
  background: #3f3f5a;
  color: #00ffe7;
  border: none;
  padding: 15px;
  font-size: 1.2em;
  border-radius: 10px;
  transition: background 0.2s;
}

button:hover {
  background: #5c5c8a;
}

/* Historial */
.history {
  background: #1e1e2f;
  padding: 15px;
  border-radius: 15px;
  flex: 1;
  min-width: 250px;
  max-height: 600px;
  overflow-y: auto;
}

.history h2 {
  margin-top: 0;
  color: #00ffc8;
}

#historyList {
  list-style: none;
  padding-left: 0;
}

#historyList li {
  background: #333355;
  margin-bottom: 10px;
  padding: 10px;
  border-radius: 8px;
  font-size: 0.9em;
  color: #afffff;
}
