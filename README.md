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
        <!-- Другие таймеры здесь -->
    </div>

    <script>
        window.onload = function() {
            // Читаем параметры из URL и устанавливаем время таймеров
            var urlParams = new URLSearchParams(window.location.search);
            for (var i = 1; i <= 9; i++) {
                var timerId = 'timer' + i;
                var timerElement = document.getElementById(timerId);
                var timerTime = urlParams.get(timerId);
                if (timerTime) {
                    timerElement.textContent = formatTime(timerTime);
                    startTimer(timerId, timerTime, document.querySelector('#' + timerId + '+button'));
                }
            }
        };

        function startTimer(timerId, duration, button) {
            var timerElement = document.getElementById(timerId);
            var remainingTime = duration;

            // Если таймер уже запущен, выходим из функции
            if (button.disabled) return;

            var interval = setInterval(function() {
                var hours = Math.floor(remainingTime / 3600);
                var minutes = Math.floor((remainingTime % 3600) / 60);
                var seconds = remainingTime % 60;

                timerElement.textContent = formatTime(remainingTime);

                if (remainingTime <= 0) {
                    clearInterval(interval);
                } else {
                    remainingTime--;
                }

                // Сохраняем время таймера в локальное хранилище
                localStorage.setItem(timerId, remainingTime);
            }, 1000);

            // После запуска таймера делаем кнопку неактивной
            button.disabled = true;
        }

        function formatTime(time) {
            var hours = Math.floor(time / 3600);
            var minutes = Math.floor((time % 3600) / 60);
            var seconds = time % 60;
            return (hours < 10 ? '0' : '') + hours + ':' + 
                   (minutes < 10 ? '0' : '') + minutes + ':' + 
                   (seconds < 10 ? '0' : '') + seconds;
        }
    </script>
</body>
</html>
