---
id: pdwzuuxczwwuolr7wkowhgg
title: Close Its Own Tab after Counting down 10 Seconds
desc: ''
updated: 1679248305898
created: 1679248305898
---

```html
<!DOCTYPE html>
<html lang="en">
<head>
  <meta charset="UTF-8">
  <meta name="viewport" content="width=device-width, initial-scale=1.0">
  <title>Close Tab with Countdown Example</title>
  <script>
      let countdown;
      let countdownDisplay;
      let closeTimeout;

      function startCountdown() {
          countdown = 10;
          countdownDisplay = document.getElementById('countdown');
          countdownDisplay.innerText = `Closing in ${countdown} seconds`;
          countdown--;

          const countdownInterval = setInterval(() => {
              if (countdown <= 0) {
                  clearInterval(countdownInterval);
                  closeTab();
              } else {
                  countdownDisplay.innerText = `Closing in ${countdown} seconds`;
                  countdown--;
              }
          }, 1000);
      }

      function closeTab() {
          clearTimeout(closeTimeout);
          window.close();
      }
  </script>
</head>
<body>
  <h1>Close Tab with Countdown Example</h1>
  <p>Click the button below to start the countdown. The tab will close in 10 seconds.</p>
  <button onclick="startCountdown()">Start Countdown</button>
  <p id="countdown"></p>
</body>
</html>
```