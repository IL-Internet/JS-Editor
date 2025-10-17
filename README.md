# JS Editor
>
>### Here you can copy the code to use it offline.
>
>Just save it as `html` file , Then you can use it localy on your browser.
>
#
```html
<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>JS Editor</title>
    <style>
        body {
            font-family: Arial, sans-serif;
            display: flex;
            height: 100vh;
            margin: 0;
            overflow: hidden;
        }
        #editor-container {
            flex: 1;
            padding: 10px;
            display: flex;
            flex-direction: column;
        }
        #code-editor {
            width: 100%;
            flex-grow: 1;
            font-family: 'Courier New', monospace;
            font-size: 14px;
            padding: 10px;
            border: 1px solid #ccc;
            resize: none;
        }
        #console-container {
            flex: 1;
            padding: 10px;
            display: flex;
            flex-direction: column;
            background-color: #f0f0f0;
            border-left: 1px solid #ccc;
        }
        #console-output {
            flex-grow: 1;
            background-color: #333;
            color: #eee;
            padding: 10px;
            overflow-y: auto;
            font-family: 'Courier New', monospace;
            font-size: 13px;
            white-space: pre-wrap;
        }
        button {
            margin-top: 10px;
            padding: 8px 15px;
            background-color: #007bff;
            color: white;
            border: none;
            cursor: pointer;
        }
        button:hover {
            background-color: #0056b3;
        }
    </style>
</head>
<body>
    <div id="editor-container">
        <h2>JavaScript Code</h2>
        <textarea id="code-editor" spellcheck="false">Replace this text with your javascript code.. </textarea>
        <button onclick="runCode()">Run Code</button>
    </div>
    <div id="console-container">
        <h2>Console Output</h2>
        <pre id="console-output"></pre>
        <button onclick="clearConsole()">Clear Console</button>
    </div>
    <script>
        const codeEditor = document.getElementById('code-editor');
        const consoleOutput = document.getElementById('console-output');
        const originalConsoleLog = console.log;
        console.log = (...args) => {
            originalConsoleLog(...args); 
            consoleOutput.textContent += args.map(arg => typeof arg === 'object' ? JSON.stringify(arg) : arg).join(' ') + '\n';
            consoleOutput.scrollTop = consoleOutput.scrollHeight; 
        }
        function runCode() {
            clearConsole(); 
                eval(codeEditor.value);
        }
        function clearConsole() {
            consoleOutput.textContent = ''
        }
        runCode()
    </script>
</body>
</html>
```
