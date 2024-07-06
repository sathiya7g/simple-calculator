# simple-calculator
Design a Webpage using JavaScript eith a minimum of five mathematical operations.
**CODING:**

**index.html**
```
<!DOCTYPE html>
<html lang="en">
<head>
  <meta charset="UTF-8">
  <meta name="viewport" content="width=device-width, initial-scale=1.0">
  <title>Beautiful Calculator</title>
  <link rel="stylesheet" href="styles.css">
</head>
<body>
  <div class="container">
    <h1>Beautiful Calculator</h1>
    <div id="calculator">
      <div id="display">
        <div id="inputDisplay"></div>
        <div id="operatorDisplay"></div>
        <div id="resultDisplay"></div>
      </div>
      <div id="buttons">
        <div class="button-row">
          <button onclick="appendNumber('7')">7</button>
          <button onclick="appendNumber('8')">8</button>
          <button onclick="appendNumber('9')">9</button>
          <button class="operator" onclick="setOperator('+')">+</button>
        </div>
        <div class="button-row">
          <button onclick="appendNumber('4')">4</button>
          <button onclick="appendNumber('5')">5</button>
          <button onclick="appendNumber('6')">6</button>
          <button class="operator" onclick="setOperator('-')">-</button>
        </div>
        <div class="button-row">
          <button onclick="appendNumber('1')">1</button>
          <button onclick="appendNumber('2')">2</button>
          <button onclick="appendNumber('3')">3</button>
          <button class="operator" onclick="setOperator('*')">*</button>
        </div>
        <div class="button-row">
          <button onclick="appendNumber('0')">0</button>
          <button class="clear" onclick="clearDisplay()">C</button>
          <button class="equal" onclick="calculate()">=</button>
          <button class="operator" onclick="setOperator('/')">/</button>
        </div>
      </div>
    </div>
  </div>

  <script src="script.js"></script>
</body>
</html>
```
**style.css:**
```
body {
  font-family: 'Segoe UI', Tahoma, Geneva, Verdana, sans-serif;
  background-color: #f3f3f3;
  display: flex;
  justify-content: center;
  align-items: center;
  height: 100vh;
  margin: 0;
}

.container {
  background-color: #fff;
  padding: 20px;
  border-radius: 10px;
  box-shadow: 0 4px 8px rgba(0, 0, 0, 0.1);
  width: 350px;
}

h1 {
  text-align: center;
  color: #007bff;
}

#calculator {
  text-align: center;
}

#display {
  margin-bottom: 20px;
  background-color: #f9f9f9;
  padding: 10px;
  border-radius: 8px;
  box-shadow: 0 2px 4px rgba(0, 0, 0, 0.1);
  display: flex;
  justify-content: space-between;
  align-items: center;
}

#inputDisplay, #operatorDisplay, #resultDisplay {
  font-size: 1.5em;
  padding: 5px;
}

#inputDisplay {
  text-align: right;
  flex: 2;
}

#operatorDisplay, #resultDisplay {
  text-align: center;
  color: #007bff;
  flex: 1;
}

#buttons {
  display: flex;
  flex-direction: column;
  align-items: center;
}

.button-row {
  margin-bottom: 10px;
  display: flex;
  justify-content: center;
}

button {
  padding: 16px 24px;
  margin: 5px;
  background-color: #007bff;
  color: #fff;
  border: none;
  border-radius: 8px;
  cursor: pointer;
  font-size: 1.2em;
  box-shadow: 0 2px 4px rgba(0, 0, 0, 0.1);
  transition: background-color 0.3s ease;
}

button:hover {
  background-color: #0056b3;
}

button:active {
  transform: translateY(2px);
  box-shadow: none;
}

button.operator {
  background-color: #ff9500;
}

button.operator:hover {
  background-color: #e67e22;
}

button.clear {
  background-color: #dc3545;
}

button.clear:hover {
  background-color: #c82333;
}

button.equal {
  background-color: #28a745;
}

button.equal:hover {
  background-color: #218838;
}
```
**script.js:**
```
let currentInput = ''; // Variable to store the current input
let operator = ''; // Variable to store the current operator
let firstOperand = ''; // Variable to store the first operand

function appendNumber(number) {
  currentInput += number;
  updateDisplay();
}

function setOperator(op) {
  operator = op;
  firstOperand = currentInput;
  currentInput = '';
  updateDisplay();
}

function clearDisplay() {
  currentInput = '';
  operator = '';
  firstOperand = '';
  updateDisplay();
}

function calculate() {
  let result = '';
  const num1 = parseFloat(firstOperand);
  const num2 = parseFloat(currentInput);
  switch (operator) {
    case '+':
      result = num1 + num2;
      break;
    case '-':
      result = num1 - num2;
      break;
    case '*':
      result = num1 * num2;
      break;
    case '/':
      if (num2 !== 0) {
        result = num1 / num2;
      } else {
        result = 'Error: Divide by zero';
      }
      break;
    default:
      result = 'Error';
      break;
  }
  document.getElementById('inputDisplay').textContent = `${num1} ${operator} ${num2}`;
  document.getElementById('resultDisplay').textContent = `= ${result}`;
}

function updateDisplay() {
  document.getElementById('inputDisplay').textContent = currentInput;
  document.getElementById('operatorDisplay').textContent = operator;
  document.getElementById('resultDisplay').textContent = '';
}
```
**OUTPUT:**
![image](https://github.com/sathiya7g/simple-calculator/assets/113282947/916086c3-1427-4d2c-9b92-7f0a00e856a8)
