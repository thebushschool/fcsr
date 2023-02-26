# Introduction to Raspberry PI (rPI) & LED Circuits

### [Reference document for First Steps in Learning about Raspberry PI](Bush_RPI_PYTHON_ROBOTICS.pdf)

### Step 1. Access Your Assigned Team Raspberry PI

1. [Click here to Verify access to Your Team Raspberry PI  (replace bupiX with your assigned  rPI hostname in the address bar of your browser)](http://bupiX.bush.edu)
Do you see Confetti ?? 

1. [Click here to Access Your Team Raspberry PI's JupyterLab (replace bupiX with your rPI hostname in the address bar of your browser)](http://bupiX.bush.edu:8081)

1. Run the sysinfo.ipynb from the /data folder to see output from your PI. If you do not see sysinfo.ipynb you can [download it here](sysinfo.ipynb) and then drag the file to your PI

1. Wire-up your RPI following instructions in the First Steps PDF above

1. Create a new Jupyter Notebook. Name it first_notebook.ipynb. Copy the following lines of code inside a code cell in your notebook. Then Shift-Enter to run it. Do you see your LED blinking?


````
# first led circuit
import gpiozero
import time

led = gpiozero.LED(4)

while True:
    led.on()
    time.sleep(1)
    led.off()
    time.sleep(1)
````

### Step 2. LED circuit
1. Change sleep time to see if it works
2. ChangeGPIO port to 18, re-wire the RPI and see if it works again

### Step 3. Button control
1. Wire-up your RPI following instructions in the First Steps PDF above

1. Create another Jupyter Notebook.  Name it button_test.ipynb. Copy the following lines of code inside a code cell in your notebook.

````
# button pressed
import RPi.GPIO as GPIO
import time
from datetime import datetime

GPIO.setmode(GPIO.BCM)

pin = 21

GPIO.setup(pin, GPIO.IN, pull_up_down=GPIO.PUD_UP)

def is_button_clicked(pin):
    input_state = GPIO.input(pin)
    current_time = datetime.now().strftime("%H:%M:%S")
    if input_state == False:
        print(f'Button Pressed LED on @ {current_time}')

while True:
    is_button_clicked(pin)
    time.sleep(0.2)

````

