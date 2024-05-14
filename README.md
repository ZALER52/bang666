# bang666
<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Тест по IT технологиям</title>
    <style>
        body {
            margin: 0;
            padding: 0;
            background-image: url('cont1.jpg');
            background-size: cover;
            background-position: center;
            height: 100vh;
            display: flex;
            justify-content: center;
            align-items: center;
            flex-direction: column;
            color: white;
            font-family: Arial, sans-serif;
        }

        #content {
            text-align: center;
        }

        button {
            padding: 10px 20px;
            font-size: 18px;
            background-color: #007bff;
            color: white;
            border: none;
            cursor: pointer;
        }
    </style>
</head>
<body>
    <div id="content">
        <h1>Хочешь узнать свой уровень знаний по IT технологиям?</h1>
        <p>Тогда нажимай на кнопку ниже и проходи тестирование</p>
        <button onclick="window.location.href = 'Data/reg.html'">Перейти к тесту</button>
    </div>
</body>
</html>
Регистрация
<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Регистрация</title>
    <style>
        body {
            background-image: url('cont3.jpg');
            background-size: cover;
            background-position: center;
            height: 100vh;
            margin: 0;
            display: flex;
            justify-content: center;
            align-items: center;
        }

        form {
            background-color: rgba(255, 255, 255, 0.8);
            padding: 20px;
            border-radius: 10px;
        }

        input {
            width: 69%;
            padding: 7px;
            margin-bottom: 10px;
        }

        button {
            width: 100%;
            padding: 10px;
            background-color: #007bff;
            color: white;
            border: none;
            border-radius: 5px;
            cursor: pointer;
        }
    </style>
</head>
<body>
    <form action="console.html" method="post">
        <h2>Регистрация</h2>
        <input type="text" name="name" placeholder="Имя" autocomplete="off" required><br>
        <input type="text" name="login" placeholder="Логин" autocomplete="off" required><br>
        <input type="password" name="password" placeholder="Пароль" autocomplete="off" required><br>
        <button type="submit">Готово</button>
    </form>
</body>
</html>
Переход к тесту
<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Внедряем консоль Python</title>
    <style>
        body {
            margin: 0;
            padding: 0;
            background-image: url('cont2.jpg');
            background-size: cover;
            background-position: center;
            height: 100vh;
            display: flex;
            justify-content: center;
            align-items: center;
            flex-direction: column;
        }
        #console {
            width: 800px;
            background-color: rgba(255, 255, 255, 0.8);
            border-radius: 10px;
            padding: 20px;
            overflow-y: auto;
            font-size: 14px;
        }

    </style>
</head>
<body>
    <div id="console">
        <h1>Добро пожаловать на тест по IT технологиям!</h1>
        <button onclick="runTest()">Запустить тест</button>
    </div>

    <script>
        const question_prompts = [
 ];

        const questions = [
 ];

        let currentQuestionIndex = 0;
        let score = 0;

        function runTest() {
            let consoleElement = document.getElementById("console");
            consoleElement.innerHTML = questions[currentQuestionIndex].vopros;

            let inputElement = document.createElement("input");
            inputElement.type = "text";
            consoleElement.appendChild(inputElement);

            let submitButton = document.createElement("button");
            submitButton.textContent = "Ответить";
            submitButton.disabled = true;
            submitButton.onclick = checkAnswer;
            consoleElement.appendChild(submitButton);

        inputElement.addEventListener("input", function() {
            if (inputElement.value.trim() !== "") {
                submitButton.disabled = false;
            } else {
                submitButton.disabled = true;
            }
        });
        }

        function checkAnswer() {
            let userAnswer = document.querySelector("input").value.toLowerCase();
            let correctAnswer = questions[currentQuestionIndex].otvet;

            if (userAnswer === correctAnswer) {
                score++;
                addToConsole("Правильно!");
            } else {
                addToConsole("Неправильно. Попробуйте еще раз.");
            }

            currentQuestionIndex++;

            if (currentQuestionIndex < questions.length) {
                runTest();
            } else {
                displayResults();
            }
        }

        function displayResults() {
            if (score === questions.length) {
                addToConsole("Молодец");
            } else if (score >= questions.length / 2) {
                addToConsole("Хорошо, но можно лучше.");
            } else {
                addToConsole("Плохо.");
            }
            addToConsole("У вас " + score + " ответов из " + questions.length + " верны!");

            // Сброс переменных для повторного прохождения теста
            currentQuestionIndex = 0;
            score = 0;
        }

        function addToConsole(message) {
            document.getElementById("console").innerHTML += message + "<br>";
        }
    </script>
</body>
</html>
