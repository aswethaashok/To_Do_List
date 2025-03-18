# Ex03 To-Do List using JavaScript
## Date: 18-03-25
SWETHA A
212223220114

## AIM
To create a To-do Application with all features using JavaScript.

## ALGORITHM
### STEP 1
Build the HTML structure (index.html).

### STEP 2
Style the App (style.css).

### STEP 3
Plan the features the To-Do App should have.

### STEP 4
Create a To-do application using Javascript.

### STEP 5
Add functionalities.

### STEP 6
Test the App.

### STEP 7
Open the HTML file in a browser to check layout and functionality.

### STEP 8
Fix styling issues and refine content placement.

### STEP 9
Deploy the website.

### STEP 10
Upload to GitHub Pages for free hosting.

## PROGRAM
```
<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>swe todolist</title>
    <link rel="stylesheet" href="styles.css">
</head>

<body style="background: url('background.jpg') no-repeat center center fixed; background-size: cover;">
    <div class="container">
        <h2>To-Do List</h2>
        <div class="input-container">
            <input type="text" id="taskInput" placeholder="what needs to be done?">
            <button onclick="addTask()">+</button>
        </div>
        <ul id="taskList"></ul>
    </div>
    <footer>
        <p>&copy; SWETHA (212223220114). All rights reserved.</p>
    </footer>

    <script src="todo.js"></script>
</body>
</html>

styles.css

body {
    font-family: 'Arial', sans-serif;
    
    display: flex;
    justify-content: center;
    align-items: center;
    height: 100vh;
    margin: 0;
}

.container {
    background: rgb(246, 174, 174);
    padding: 20px;
    border-radius: 10px;
    box-shadow: 0px 5px 15px rgba(0, 0, 0, 0.2);
    text-align: center;
    width: 350px;
    opacity: 0.9;
}

h2 {
    color: #333;
    text-transform: uppercase;
}

.input-container {
    display: flex;
    border: 2px solid #c4a000;
    border-radius: 5px;
    overflow: hidden;
    margin-bottom: 15px;
}

input {
    flex: 1;
    padding: 10px;
    border: none;
    font-style: italic;
    outline: none;
}

button {
    background: #3498db;
    color: rgb(245, 241, 241);
    border: none;
    padding: 10px 15px;
    cursor: pointer;
    font-size: 18px;
}

button:hover {
    background: #217dbb;
}

ul {
    list-style: none;
    padding: 0;
    margin: 0;
}

li {
    background: #d5efef;
    margin-top: 10px;
    padding: 10px;
    display: flex;
    justify-content: space-between;
    align-items: center;
    border-radius: 5px;
    font-size: 16px;
    transition: 0.3s;
}

li.completed {
    text-decoration: line-through;
    color: #888;
}

.delete-btn {
    background:rgb(169, 173, 173);
    border: none;
    cursor: pointer;
    font-size: 18px;
    color: #d9534f;
}

.delete-btn:hover {
    color: red;
}
footer {
    background-color: #333;
    color: white;
    text-align: center;
    padding: 10px 0;
    position: fixed;
    bottom: 0;
    width: 100%;
}

todo.js

document.addEventListener("DOMContentLoaded", loadTasks);

function addTask() {
    let taskInput = document.getElementById("taskInput");
    let taskText = taskInput.value.trim();

    if (taskText === "") return;

    let taskList = document.getElementById("taskList");
    let li = document.createElement("li");

    li.innerHTML = `
        <input type="checkbox" onclick="toggleComplete(this)">
        <span onclick="toggleComplete(this)">${taskText}</span>
        <button class="delete-btn" onclick="removeTask(this)">✖</button>
    `;

    taskList.appendChild(li);
    saveTasks();
    taskInput.value = "";
}

function toggleComplete(element) {
    element.parentElement.classList.toggle("completed");
    saveTasks();
}

function removeTask(button) {
    button.parentElement.remove();
    saveTasks();
}

function saveTasks() {
    let tasks = [];
    document.querySelectorAll("#taskList li").forEach(li => {
        tasks.push({
            text: li.querySelector("span").innerText,
            completed: li.classList.contains("completed"),
        });
    });
    localStorage.setItem("tasks", JSON.stringify(tasks));
}

function loadTasks() {
    let savedTasks = JSON.parse(localStorage.getItem("tasks")) || [];
    let taskList = document.getElementById("taskList");

    savedTasks.forEach(task => {
        let li = document.createElement("li");
        li.classList.toggle("completed", task.completed);
        li.innerHTML = `
            <input type="checkbox" ${task.completed ? "checked" : ""} onclick="toggleComplete(this)">
            <span onclick="toggleComplete(this)">${task.text}</span>
            <button class="delete-btn" onclick="removeTask(this)">✖</button>
        `;
        taskList.appendChild(li);
    });
}

```

## OUTPUT

![Screenshot 2025-03-18 144247](https://github.com/user-attachments/assets/862089fd-aeb6-48b5-905c-702824906bf0)



## RESULT
The program for creating To-do list using JavaScript is executed successfully.
