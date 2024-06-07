<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Таймеры</title>
    <style>
        body {
            font-family: Arial, sans-serif;
            text-align: center;
        }
        .timer {
            margin-bottom: 20px;
        }
    </style>
</head>
<body>
    <h1>Таймеры</h1>
    <div class="timer">
        <h2>Всадник</h2>
        <button onclick="startFixedTimer(25, 0, 'timer1')">Убит!</button>
        <div id="timer1"></div>
    </div>
    <div class="timer">
        <h2>Грот 1 - Тигдаль</h2>
        <button onclick="startFixedTimer(10, 0, 'timer2')">Убит!</button>
        <div id="timer2"></div>
    </div>
    <div class="timer">
        <h2>Грот 2 - Гатфилион</h2>
        <button onclick="startFixedTimer(10, 0, 'timer3')">Убит!</button>
        <div id="timer3"></div>
    </div>
    <div class="timer">
        <h2>Грот 3 - Хотура</h2>
        <button onclick="startFixedTimer(10, 0, 'timer4')">Убит!</button>
        <div id="timer4"></div>
    </div>
    <div class="timer">
        <h2>Грот 3 - Моди</h2>
        <button onclick="startFixedTimer(10, 0, 'timer5')">Убит!</button>
        <div id="timer5"></div>
    </div>
    <div class="timer">
        <h2>Грот 4 - Фандир</h2>
        <button onclick="startFixedTimer(10, 0, 'timer6')">Убит!</button>
        <div id="timer6"></div>
    </div>
    <div class="timer">
        <h2>Грот 4 - Стомид</h2>
        <button onclick="startFixedTimer(10, 0, 'timer7')">Убит!</button>
        <div id="timer7"></div>
    </div>
    <div class="timer">
        <h2>Грот 5 - Мольтанис</h2>
        <button onclick="startFixedTimer(10, 0, 'timer8')">Убит!</button>
        <div id="timer8"></div>
    </div>
    <div class="timer">
        <h2>Грот 6 - Дардаль Лока</h2>
        <button onclick="startFixedTimer(10, 0, 'timer9')">Убит!</button>
        <div id="timer9"></div>
    </div>

    <script>
        function startFixedTimer(hours, minutes, timerId) {
            var totalTime = localStorage.getItem(timerId) || (hours * 3600) + (minutes * 60);
            var timerDisplay = document.getElementById(timerId);
            var interval = setInterval(function() {
                if (totalTime <= 0) {
                    clearInterval(interval);
                    timerDisplay.textContent = "Время вышло!";
                } else {
                    var hoursDisplay = Math.floor(totalTime / 3600);
                    var minutesDisplay = Math.floor((totalTime % 3600) / 60);
                    var secondsDisplay = totalTime % 60;
                    timerDisplay.textContent = ("0" + hoursDisplay).slice(-2) + ":" + ("0" + minutesDisplay).slice(-2) + ":" + ("0" + secondsDisplay).slice(-2);
                    totalTime--;
                    localStorage.setItem(timerId, totalTime);
                }
            }, 1000);
        }

        window.onload = function() {
            startFixedTimer(25, 0, 'timer1');
            startFixedTimer(10, 0, 'timer2');
            startFixedTimer(10, 0, 'timer3');
            startFixedTimer(10, 0, 'timer4');
            startFixedTimer(10, 0, 'timer5');
            startFixedTimer(10, 0, 'timer6');
            startFixedTimer(10
