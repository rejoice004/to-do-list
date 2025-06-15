# to-do-list
A simple to do list app
<!DOCTYPE html>
<html lang="en">
<head>
  <meta charset="UTF-8" />
  <meta name="viewport" content="width=device-width, initial-scale=1.0" />
  <title>Simple To-Do List</title>
  <style>
    body {
      font-family: 'Segoe UI', sans-serif;
      background: #f0f4f8;
      display: flex;
      flex-direction: column;
      align-items: center;
      padding: 40px;
    }
    h1 {
      color: #333;
    }
    .todo-container {
      background: #fff;
      padding: 20px;
      width: 100%;
      max-width: 400px;
      border-radius: 10px;
      box-shadow: 0 5px 15px rgba(0,0,0,0.1);
    }
    input[type="text"] {
      width: 75%;
      padding: 10px;
      border: 1px solid #ddd;
      border-radius: 5px;
      outline: none;
    }
    button {
      padding: 10px;
      margin-left: 5px;
      background-color: #007bff;
      color: white;
      border: none;
      border-radius: 5px;
      cursor: pointer;
    }
    ul {
      list-style: none;
      padding: 0;
      margin-top: 20px;
    }
    li {
      padding: 10px;
      margin-bottom: 10px;
      background: #f9f9f9;
      border-radius: 5px;
      display: flex;
      justify-content: space-between;
      align-items: center;
    }
    li.completed {
      text-decoration: line-through;
      color: gray;
    }
    .delete-btn {
      background-color: red;
      color: white;
      border: none;
      padding: 5px 8px;
      border-radius: 3px;
      cursor: pointer;
    }
  </style>
</head>
<body>
  <h1>My To-Do List</h1>
  <div class="todo-container">
    <input type="text" id="taskInput" placeholder="Add a new task..." />
    <button onclick="addTask()">Add</button>
    <ul id="taskList"></ul>
  </div>

  <script>
    function addTask() {
      const taskInput = document.getElementById("taskInput");
      const taskText = taskInput.value.trim();
      if (taskText === "") return;

      const li = document.createElement("li");
      li.innerText = taskText;

      // Toggle complete
      li.addEventListener("click", function () {
        li.classList.toggle("completed");
      });

      // Delete button
      const delBtn = document.createElement("button");
      delBtn.innerText = "Delete";
      delBtn.className = "delete-btn";
      delBtn.addEventListener("click", function (e) {
        e.stopPropagation(); // prevent toggle when deleting
        li.remove();
      });

      li.appendChild(delBtn);
      document.getElementById("taskList").appendChild(li);

      taskInput.value = "";
    }
  </script>
</body>
</html>
