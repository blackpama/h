```html
<!DOCTYPE html>
<html lang="en">

<head>
  <meta charset="UTF-8">
  <meta name="viewport" content="width=device-width, initial-scale=1.0">
  <title>Custom Code Editor</title>
  <style>
    /* Define styles for different elements */
    .output {
        border: 1px solid #ccc;
        padding: 10px;
        margin: 10px 0;
        white-space: pre-line; /* Preserve line breaks */
    }
  </style>
  <script
    src="https://cdnjs.cloudflare.com/ajax/libs/js-beautify/1.13.5/beautify-html.min.js">
  </script>
</head>

<body>
  <!-- Create buttons for different actions -->
  <button id="addMainHeading">Add Main Heading</button>
  <button id="addSubHeading">Add Sub Heading</button>
  <button id="addHR">Add HR</button>
  <button id="addBR">Add BR</button>
  <button id="addCode">Add Code</button>
  <button id="addLink">Add Link</button>

  <!-- Output area to display the generated code -->
  <div id="output" class="output"></div>

  <!-- JavaScript to handle button clicks -->
  <script>
    // Get the output div
    const outputDiv = document.getElementById("output");
    
    // Function to add content based on button clicks
    function addButtonClickListener(buttonId, tag) {
        const button = document.getElementById(buttonId);
        button.addEventListener("click", function () {
            const userInput = prompt("Enter content:");
            if (userInput !== null && userInput.trim() !== "") {
                // Add a line break if the output area is not empty
                if (outputDiv.innerHTML !== "") {
                    outputDiv.appendChild(document.createElement("br"));
                }
                outputDiv.appendChild(document.createTextNode(`<${tag}>${userInput}</${tag}>`));
                if (outputDiv.innerHTML !== "") {
                    outputDiv.appendChild(document.createElement("br"));
                }
            }
        });
    }
    
    addButtonClickListener("addMainHeading", "h1");
    addButtonClickListener("addSubHeading", "h2");
    addButtonClickListener("addHR", "hr");
    addButtonClickListener("addBR", "br");
    
    // Function to add code with user input in pre format
    document.getElementById("addCode").addEventListener("click", function () {
        const code = prompt("Enter your HTML code:");
        if (code !== null && code.trim() !== "") {
            // Add a line break if the output area is not empty
            if (outputDiv.innerHTML !== "") {
                outputDiv.appendChild(document.createElement("br"));
            }
    
            // Add triple backticks and a line break before the code
            outputDiv.appendChild(document.createTextNode("```html"));
            outputDiv.appendChild(document.createElement("br"));
    
            // Beautify the code
            const beautifiedCode = html_beautify(code, {
                indent_size: 2,
                wrap_line_length: 80,
                max_preserve_newlines: 2,
                preserve_newlines: true
            });
    
            // Create a <pre> element to display the beautified code
            const preElement = document.createElement("pre");
            preElement.textContent = beautifiedCode;
            outputDiv.appendChild(preElement);
    
            // Add triple backticks and a line break after the code
            outputDiv.appendChild(document.createElement("br"));
            outputDiv.appendChild(document.createTextNode("```"));
            outputDiv.appendChild(document.createElement("br"));
        }
    });
    
    // Function to add a link
    document.getElementById("addLink").addEventListener("click", function () {
        const title = prompt("Enter link title:");
        const link = prompt("Enter link URL:");
        if (title !== null && link !== null && title.trim() !== "" && link.trim() !== "") {
            // Add a line break if the output area is not empty
            if (outputDiv.innerHTML !== "") {
                outputDiv.appendChild(document.createElement("br"));
            }
            outputDiv.appendChild(document.createTextNode(`<a href="${link}">${title}</a>`));
            outputDiv.appendChild(document.createElement("br"));
        }
    });
  </script>
</body>

</html>

```

<h1>good</h1>

<a href="https://youtu.be/ciTmo7K5OVo?feature=shared">g</a>
