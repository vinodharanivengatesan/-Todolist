### Ex03 To-Do List using JavaScript
### Date:

### AIM
To create a To-do Application with all features using JavaScript.

### ALGORITHM

STEP 1
Build the HTML structure (index.html).

STEP 2
Style the App (style.css).

STEP 3
Plan the features the To-Do App should have.

STEP 4
Create a To-do application using Javascript.

STEP 5
Add functionalities.

STEP 6
Test the App.

STEP 7
Open the HTML file in a browser to check layout and functionality.

STEP 8
Fix styling issues and refine content placement.

STEP 9
Deploy the website.

STEP 10
Upload to GitHub Pages for free hosting.

### PROGRAM
```

<!DOCTYPE html>
<html>
<head>
    <title>Todo Application</title>

    <style>
        body {
            font-family: Arial;
            background: #eaf0f8;
            text-align: center;
            padding: 30px;
        }

        .container {
            background: white;
            width: 400px;
            max-width: 95%;
            margin: auto;
            padding: 25px;
            border-radius: 10px;
            box-shadow: 0 0 10px gray;
        }

        h1 {
            color: #2874f0;
        }

        input {
            padding: 10px;
            width: 55%;
            border: 1px solid gray;
            border-radius: 5px;
        }

        button {
            padding: 10px;
            border: none;
            border-radius: 5px;
            cursor: pointer;
            margin: 3px;
        }

        .add {
            background: #2874f0;
            color: white;
        }

        ul {
            list-style: none;
            padding: 0;
        }

        li {
            background: #f1f1f1;
            margin: 10px 0;
            padding: 10px;
            display: flex;
            justify-content: space-between;
            align-items: center;
            gap: 5px;
            border-radius: 5px;
        }

        .completed {
            text-decoration: line-through;
            color: gray;
        }

        .edit {
            background: orange;
        }

        .delete {
            background: red;
            color: white;
        }

        .done {
            background: green;
            color: white;
        }

        .filters button {
            background: #ddd;
        }
    </style>
</head>

<body>

<div class="container">

    <h1>My Todo List</h1>

    <input type="text" id="taskInput"
           placeholder="Enter your task">

    <button class="add" onclick="addTask()">Add</button>

    <div class="filters">
        <button onclick="showTasks('all')">All</button>
        <button onclick="showTasks('completed')">Completed</button>
        <button onclick="showTasks('pending')">Pending</button>
    </div>

    <ul id="taskList"></ul>

</div>

<script>

    let tasks = [];
    let filter = "all";

    // Add Task
    function addTask() {
        let input = document.getElementById("taskInput");
        let task = input.value.trim();

        if (task === "") {
            alert("Please enter a task!");
            return;
        }

        tasks.push({
            text: task,
            completed: false
        });

        input.value = "";
        displayTasks();
    }

    // Display Tasks
    function displayTasks() {
        let list = document.getElementById("taskList");
        list.innerHTML = "";

        tasks.forEach((task, index) => {

            if (filter === "completed" && !task.completed)
                return;

            if (filter === "pending" && task.completed)
                return;

            let li = document.createElement("li");

            let span = document.createElement("span");
            span.textContent = task.text;

            if (task.completed) {
                span.classList.add("completed");
            }

            // Complete Button
            let done = document.createElement("button");
            done.textContent = "Done";
            done.className = "done";

            done.onclick = function() {
                tasks[index].completed = !tasks[index].completed;
                displayTasks();
            };

            // Edit Button
            let edit = document.createElement("button");
            edit.textContent = "Edit";
            edit.className = "edit";

            edit.onclick = function() {
                let newTask = prompt("Edit your task:", task.text);

                if (newTask !== null && newTask.trim() !== "") {
                    tasks[index].text = newTask.trim();
                    displayTasks();
                }
            };

            // Delete Button
            let del = document.createElement("button");
            del.textContent = "Delete";
            del.className = "delete";

            del.onclick = function() {
                tasks.splice(index, 1);
                displayTasks();
            };

            li.appendChild(span);
            li.appendChild(done);
            li.appendChild(edit);
            li.appendChild(del);

            list.appendChild(li);
        });
    }

    // Filter Tasks
    function showTasks(type) {
        filter = type;
        displayTasks();
    }

</script>

</body>
</html>
```
### OUTPUT

<img width="768" height="476" alt="image" src="https://github.com/user-attachments/assets/4338ec42-d07f-4e05-9327-4ba5ab0a9820" />

### RESULT
The program for creating To-do list using JavaScript is executed successfully.
