<!DOCTYPE html>
<html>
<head>
    <title>Таймеры с обратным отсчетом</title>
    <style>
        .timer {
            font-size: 24px;
            margin: 10px;
        }
        .container {
            display: flex;
            flex-direction: column;
            align-items: center;
            margin-top: 20px; /* Отступ сверху */
        }
        .timer-container {
            margin-bottom: 20px;
            text-align: center;
            border: 2px solid #ccc; /* Рамка */
            padding: 10px;
            border-radius: 10px; /* Скругление углов */
        }
        .title {
            font-size: 20px;
            margin-bottom: 5px;
        }
        .row {
            display: flex;
            justify-content: center;
        }
        .column {
            margin: 0 20px;
        }
    </style>
</head>
<body>
    <div class="container">
        <div class="timer-container">
            <div class="title">Грот 1 - Тигдаль</div>
            <div id="timer1" class="timer">10:00:00</div>
            <button onclick="startTimer('timer1', 36000, this)">Убит!</button>
        </div>
        <div class="timer-container">
            <div class="title">Грот 2 - Гатфилион</div>
            <div id="timer2" class="timer">10:00:00</div>
            <button onclick="startTimer('timer2', 36000, this)">Убит!</button>
        </div>
        <div class="row">
            <div class="column">
                <div class="timer-container">
                    <div class="title">Грот 3 - Моди</div>
                    <div id="timer3" class="timer">10:00:00</div>
                    <button onclick="startTimer('timer3', 36000, this)">Убит!</button>
                </div>
            </div>
            <div class="column">
                <div class="timer-container">
                    <div class="title">Грот 3 - Хотура</div>
                    <div id="timer4" class="timer">10:00:00</div>
                    <button onclick="startTimer('timer4', 36000, this)">Убит!</button>
                </div>
            </div>
        </div>
        <div class="row">
            <div class="column">
                <div class="timer-container">
                    <div class="title">Грот 4 - Стомид</div>
                    <div id="timer5" class="timer">10:00:00</div>
                    <button onclick="startTimer('timer5', 36000, this)">Убит!</button>
                </div>
            </div>
            <div class="column">
                <div class="timer-container">
                    <div class="title">Грот 4 - Фандир</div>
                    <div id="timer6" class="timer">10:00:00</div>
                    <button onclick="startTimer('timer6', 36000, this)">Убит!</button>
                </div>
            </div>
        </div>
        <div class="timer-container">
            <div class="title">Грот 5 - Мольтанис</div>
            <div id="timer7" class="timer">10:00:00</div>
            <button onclick="startTimer('timer7', 36000, this)">Убит!</button>
        </div>
        <div class="timer-container">
            <div class="title">Грот 6 - Дардаль Лока</div>
            <div id="timer8" class="timer">10:00:00</div>
            <button onclick="startTimer('timer8', 36000, this)">Убит!</button>
        </div>
        <div class="timer-container">
            <div class="title">Всадник смерти</div>
            <div id="timer9" class="timer">10:00:00</div>
            <button onclick="startTimer('timer9', 36000, this)">Убит!</button>
        </div>
    </div>

    <script>
        function startTimer(timerId, duration, button) {
            var timerElement = document.getElementById(timerId);
            var remainingTime = duration;

            // Если таймер уже запущен, выходим из функции
            if (button.disabled) return;

            var interval = setInterval(function() {
                var hours = Math.floor(remainingTime / 3600);
                var minutes = Math.floor((remainingTime % 3600) / 60);
                var seconds = remainingTime % 60;

                timerElement.textContent = 
                    (hours < 10 ? '0' : '') + hours + ':' + 
                    (minutes < 10 ? '0' : '') + minutes + ':' + 
                    (seconds < 10 ? '0' : '') + seconds;

                if (remainingTime <= 0) {
                    clearInterval(interval);
                } else {
                    remainingTime--;
                }
            }, 1000);

            // После запуска таймера делаем кнопку неактивной
            button.disabled = true;
        }
    </script>
</body>
</html>
