Task 5 : Develop a countdown timer

Create a countdown timer that counts down
from a set time to zero, with options to stop,
reset, and restart the timer.


<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Countdown Timer</title>
    <style>
        body {
            font-family: Arial, sans-serif;
            background-color: #f4f4f4;
            margin: 0;
            padding: 0;
            display: flex;
            justify-content: center;
            align-items: center;
            height: 100vh;
        }

        #timer {
            background-color: #fff;
            border-radius: 8px;
            box-shadow: 0 0 10px rgba(0, 0, 0, 0.1);
            padding: 20px;
            text-align: center;
        }

        button {
            padding: 10px 15px;
            font-size: 16px;
            margin: 5px;
            cursor: pointer;
        }

        button.start {
            background-color: #4caf50;
            color: #fff;
        }

        button.start:hover {
            background-color: #45a049;
        }

        button.stop {
            background-color: #d9534f;
            color: #fff;
        }

        button.stop:hover {
            background-color: #c9302c;
        }

        button.reset {
            background-color: #007bff;
            color: #fff;
        }

        button.reset:hover {
            background-color: #0056b3;
        }
    </style>
</head>
<body>
    <div id="timer">
        <h1 id="countdown">00:00:00</h1>
        <button class="start" onclick="startTimer()">Start</button>
        <button class="stop" onclick="stopTimer()">Stop</button>
        <button class="reset" onclick="resetTimer()">Reset</button>
    </div>

    <script>
        var interval;
        var timeLeft = 300; // Set the initial time in seconds

        function startTimer() {
            interval = setInterval(function() {
                if (timeLeft > 0) {
                    updateTimerDisplay();
                    timeLeft--;
                } else {
                    clearInterval(interval);
                    alert("Time's up!");
                }
            }, 1000);
        }

        function stopTimer() {
            clearInterval(interval);
        }

        function resetTimer() {
            clearInterval(interval);
            timeLeft = 300; // Reset the timer to the initial time
            updateTimerDisplay();
        }

        function updateTimerDisplay() {
            var hours = Math.floor(timeLeft / 3600);
            var minutes = Math.floor((timeLeft % 3600) / 60);
            var seconds = timeLeft % 60;

            document.getElementById('countdown').innerText = pad(hours) + ":" + pad(minutes) + ":" + pad(seconds);
        }

        function pad(num) {
            return num.toString().padStart(2, '0');
        }
    </script>
</body>
</html>
