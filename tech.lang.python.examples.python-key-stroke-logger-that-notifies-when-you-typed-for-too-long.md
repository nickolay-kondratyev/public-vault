---
id: z03a0gm1ie68i90r9y5q0ky
title: Python Key Logge
desc: ''
updated: 1688096653463
created: 1688096623728
---

```python
# pip install pynput
#
# Save to monitor.py and run it by running `python3 monitor.py`
from pynput.keyboard import Key, Listener
import time
import subprocess

count = 0
limit = 3000  # Set your limit here


def send_notification():
    title = "Break Time"
    message = f"You've typed {limit} keystrokes. It's time to take a break!"
    voice_message = message #"It's time to take a break!"

    subprocess.run(['osascript', '-e', f'display notification "{message}" with title "{title}"'])
    subprocess.run(['say', voice_message])

def on_press(key):
    global count
    count += 1

    print(f"Key limit ({count}/{limit})")

    if count >= limit:
        print("--------------------------------------------------------------------------------")
        print("Sending notification...")
        print("--------------------------------------------------------------------------------")
        send_notification()
        count = 0  # Reset the counter



with Listener(on_press=on_press) as listener:
    listener.join()
```