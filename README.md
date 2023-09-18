<h1> good<h1>

<h2> git<h2>

````html

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
}
.segment {
display: flex;
align-items: center;
}
.delete-icon {
cursor: pointer;
margin-left: 10px;
}
</style>
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
function addButtonClickListener(buttonId, content) {
const button = document.getElementById(buttonId);
button.addEventListener("click", function () {
const userInput = prompt("Enter content:");
if (userInput !== null && userInput.trim() !== "") {
const segment = document.createElement("div");
segment.className = "segment";
const textContent = content.replace("USER_INPUT", userInput);
segment.textContent = textContent + " ";
segment.innerHTML += `<span class="delete-icon" onclick="removeSegment(this)">🗑️</span>`;
outputDiv.appendChild(segment);
}
});
}

function removeSegment(element) {
element.parentElement.remove();
}

addButtonClickListener("addMainHeading", "<h1>USER_INPUT</h1>");
addButtonClickListener("addSubHeading", "<h2>USER_INPUT</h2>");
addButtonClickListener("addHR", "<hr>");
addButtonClickListener("addBR", "<br>");
addButtonClickListener("addCode", "````html\nUSER_INPUT\n````");
addButtonClickListener("addLink", "<strong><a href=\"#\">USER_INPUT</a></strong>");
</script>
</body>
</html>

````

<a href="lokr">g</a>
