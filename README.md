<!DOCTYPE html>
<html>

<head>
    <title>Quản lý công việc</title>
</head>

<body>
    <h1>Quản lý công việc</h1>
    <input type="text" id="taskInput" placeholder="Nhập công việc">
    <button onclick="addTask()">Thêm</button>
    <ul id="taskList"></ul>

    <script>
        let tasks = [];

        function renderTasks() {
            const taskList = document.getElementById('taskList');
            taskList.innerHTML = '';
            tasks.forEach((task, index) => {
                const li = document.createElement('li');
                li.innerHTML = `
                    <span>${task}</span>
                    <button onclick="editTask(${index})">Sửa</button>
                    <button onclick="deleteTask(${index})">Xóa</button>
                `;
                taskList.appendChild(li);
            });
        }

        function addTask() {
            const taskInput = document.getElementById('taskInput');
            const task = taskInput.value.trim();
            if (task) {
                tasks.push(task);
                taskInput.value = '';
                renderTasks();
            }
        }

        function editTask(index) {
            const newTask = prompt('Sửa công việc:', tasks[index]);
            if (newTask !== null) {
                tasks[index] = newTask.trim();
                renderTasks();
            }
        }

        function deleteTask(index) {
            tasks.splice(index, 1);
            renderTasks();
        }

        renderTasks();
    </script>
</body>

</html>
