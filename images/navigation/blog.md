---
layout: game
title: Scientific Calculator 
description: A pretty advanced use of JavaScript building classic snake game using menu controls, key events, snake simulation and timers.
search_exclude: true
permalink: /snakegame/
---

<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Scientific Calculator</title>
    <style>
        body {
            background-color: #f0f0f0;
            font-family: Arial, sans-serif;
        }

        .calculator {
            width: 300px;
            background-color: #222;
            border-radius: 10px;
            padding: 20px;
            margin: 50px auto;
            box-shadow: 0 10px 20px rgba(0, 0, 0, 0.3);
        }

        .display {
            width: 100%;
            height: 60px;
            background-color: #444;
            border: none;
            text-align: right;
            padding: 20px;
            font-size: 24px;
            color: #fff;
            border-radius: 10px;
            margin-bottom: 10px;
        }

        .button {
            width: 60px;
            height: 60px;
            background-color: #333;
            color: #fff;
            font-size: 20px;
            border: none;
            border-radius: 10px;
            margin: 5px;
            cursor: pointer;
            transition: background-color 0.3s;
        }

        .button:hover {
            background-color: #555;
        }

        .button-operator {
            background-color: #ff5722;
        }

        .button-operator:hover {
            background-color: #ff784e;
        }

        .button-equal {
            background-color: #4caf50;
        }

        .button-equal:hover {
            background-color: #66bb6a;
        }

        .button-clear {
            background-color: #f44336;
        }

        .button-clear:hover {
            background-color: #e57373;
        }

        .row {
            display: flex;
            justify-content: center;
        }
    </style>
</head>
<body>

    <div class="calculator">
        <input type="text" class="display" id="display" disabled>

        <div class="row">
            <button class="button button-clear" onclick="clearDisplay()">C</button>
            <button class="button" onclick="appendToDisplay('(')">(</button>
            <button class="button" onclick="appendToDisplay(')')">)</button>
            <button class="button button-operator" onclick="appendToDisplay('/')">/</button>
        </div>
        
        <div class="row">
            <button class="button" onclick="appendToDisplay('7')">7</button>
            <button class="button" onclick="appendToDisplay('8')">8</button>
            <button class="button" onclick="appendToDisplay('9')">9</button>
            <button class="button button-operator" onclick="appendToDisplay('*')">*</button>
        </div>

        <div class="row">
            <button class="button" onclick="appendToDisplay('4')">4</button>
            <button class="button" onclick="appendToDisplay('5')">5</button>
            <button class="button" onclick="appendToDisplay('6')">6</button>
            <button class="button button-operator" onclick="appendToDisplay('-')">-</button>
        </div>

        <div class="row">
            <button class="button" onclick="appendToDisplay('1')">1</button>
            <button class="button" onclick="appendToDisplay('2')">2</button>
            <button class="button" onclick="appendToDisplay('3')">3</button>
            <button class="button button-operator" onclick="appendToDisplay('+')">+</button>
        </div>

        <div class="row">
            <button class="button" onclick="appendToDisplay('0')">0</button>
            <button class="button" onclick="appendToDisplay('.')">.</button>
            <button class="button" onclick="appendToDisplay('**')">^</button>
            <button class="button button-equal" onclick="calculate()">=</button>
        </div>

        <div class="row">
            <button class="button" onclick="appendToDisplay('Math.sin(')">sin</button>
            <button class="button" onclick="appendToDisplay('Math.cos(')">cos</button>
            <button class="button" onclick="appendToDisplay('Math.tan(')">tan</button>
            <button class="button" onclick="appendToDisplay('Math.sqrt(')">√</button>
        </div>

    </div>

    <script>
        function appendToDisplay(value) {
            document.getElementById("display").value += value;
        }

        function clearDisplay() {
            document.getElementById("display").value = '';
        }

        function calculate() {
            let display = document.getElementById("display").value;
            try {
                let result = eval(display);
                document.getElementById("display").value = result;
            } catch (error) {
                document.getElementById("display").value = 'Error';
            }
        }
    </script>

</body>
</html>
