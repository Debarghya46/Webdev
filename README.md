# Webdev
Calculator
<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Document</title>
    <style>
        html {
            box-sizing: border-box;
          }
          
          *,
          *::before,
          *::after {
            box-sizing: inherit;
          }
          
          body {
            margin: 0;
          }
          
          
          embed,
          iframe,
          img,
          object,
          video {
            max-width: 100%;
          }
          
          h1,
          h2,
          h3,
          h4,
          h5,
          h6,
          ul,
          ol,
          li,
          p,
          pre,
          blockquote,
          figure,
          hr {
            margin: 0;
            padding-right: 0;
            padding-left: 0;
          }
          
          a {
            text-decoration: none;
          }
          
          a:focus {
            outline: none;
          }
          
          h1,
          h2,
          h3,
          h4,
          h5,
          h6 {
            display: block;
          }
          
         
          ol,
          ul {
            list-style: none;
          }
          
          
          input,
          textarea,
          button {
            border: 0;
            border-radius: 0;
            background-color: transparent;
            font-size: inherit;
            font-family: inherit;
            font-weight: inherit;
            outline: none;
            -webkit-appearance: none;
               -moz-appearance: none;
                    appearance: none;
            text-align: left;
          }
          
          input:hover,
          input:active,
          input:focus,
          textarea:hover,
          textarea:active,
          textarea:focus,
          button:hover,
          button:active,
          button:focus {
            outline: none;
          }
          
          :root {
            font-family: Helvetica, Arial, sans-serif;
          }
          
          html {
            font-size: 175%;
            font-weight: 300;
            line-height: 1.3;
          }
          
          body {
            align-items: center;
            background-image: linear-gradient(236deg, #74ebd5, #acb6e5);
            display: flex;
            height: 120vh;
            justify-content: center;
          }
          
          .container {
            max-width: 20em;
          }
          
          .container > p {
            text-align: center;
          }
          
          .calculator {
            border-radius: 12px;
            box-shadow: 0 0 40px 0px rgba(0, 0, 0, 0.15);
            margin-left: auto;
            margin-right: auto;
            margin-top: 2em;
            max-width: 15em;
            overflow: hidden;
          }
          
          .calculator__display {
            background-color: #222222;
            color: #fff;
            font-size: 1.714285714em;
            padding: 0.5em 0.75em;
            text-align: right;
          }
          
          .calculator__keys {
            background-color: #999;
            display: grid;
            grid-gap: 1px;
            grid-template-columns: repeat(4, 1fr);
          }
          
          .calculator__keys > * {
            background-color: #fff;
            padding: 0.5em 1.25em;
            position: relative;
            text-align: center;
          }
          
          .calculator__keys > *:active::before,
          .calculator__keys > .is-depressed::before {
            background-color: rgba(0, 0, 0, 0.2);
            bottom: 0;
            box-shadow: 0 0 6px 0 rgba(0, 0, 0, 0.5) inset;
            content: "";
            left: 0;
            opacity: 0.3;
            position: absolute;
            right: 0;
            top: 0;
            z-index: 1;
          }
          
          .key--operator {
            background-color: #eee;
          }
          
          .key--equal {
            background-image: linear-gradient(to bottom, #fe886a, #ff7033);
            grid-column: -2;
            grid-row: 2/span 3;
          }
    </style>

    <script>

        function addData(num) {

            var dataCal = document.getElementById("calculator__display").innerHTML;
            var lastChar = dataCal.slice(-1);
            
            if((lastChar == '+' || lastChar =='-') && (num == '*' || num == '/' || num == '+' || num == '-')) {
                document.getElementById("calculator__display").innerHTML = dataCal.slice(0, -1) + num;
            }

            else if(lastChar == '*' && (num =='/' || num == '*')) {
                document.getElementById("calculator__display").innerHTML = dataCal.slice(0, -1) + num;
            }

            else if(lastChar == '/' && (num =='*' || num == '/')) {
                document.getElementById("calculator__display").innerHTML = dataCal.slice(0, -1) + num;
            }
            else if(dataCal.includes('.') == true && num == '.') {
                document.getElementById("calculator__display").innerHTML = dataCal;
            }
             
            else if(dataCal == '0') 
            document.getElementById("calculator__display").innerHTML = num;

            else 
            document.getElementById("calculator__display").innerHTML += num;
        }

        function allClear() {
            document.getElementById("calculator__display").innerHTML = 0;
        }

        function calculate() {
            var dataCal = document.getElementById("calculator__display").innerHTML = eval(document.getElementById("calculator__display").innerHTML);
        }

        function contentload() {
            document.getElementById("calculator__display").contentEditable=true;
        }

        function backspace() {
            var dataCal = document.getElementById("calculator__display").innerHTML;

            document.getElementById("calculator__display").innerHTML = dataCal.slice(0, -1);
        }
    </script>
</head>

<body onload = 'contentload()'>
    <div class="container">
   
        <div class="calculator">
          <div class="calculator__display" id = "calculator__display" >0</div>
    
          <div class="calculator__keys">
            <button class="key--operator" data-action="add" onclick = "addData('+')">+</button>
            <button class="key--operator" data-action="subtract" onclick = "addData('-')">-</button>
            <button class="key--operator" data-action="multiply" onclick = "addData('*')">&times;</button>
            <button class="key--operator" data-action="divide" onclick = "addData('/')">÷</button>
            <button onclick = "addData(7)">7</button>
            <button onclick = "addData(8)">8</button>
            <button onclick = "addData(9)">9</button>
            <button onclick = "addData(4)">4</button>
            <button onclick = "addData(5)">5</button>
            <button onclick = "addData(6)">6</button>
            <button onclick = "addData(1)">1</button>
            <button onclick = "addData(2)">2</button>
            <button onclick = "addData(3)">3</button>
            <button onclick = "addData(0)">0</button>

            <button data-action="decimal" onclick = "addData('.')">.</button>
            <button data-action="clear" onclick = "allClear()">AC</button>
            <button data-action="clear" onclick = "backspace()">←</button>
            <button class="key--equal" data-action="calculate" onclick = "calculate()">=</button>
          </div>
        </div>
      </div>
      <br>
      <br>
      <br>
      <br>
</body>
</html>
