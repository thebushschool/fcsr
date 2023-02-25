# Introduction to Raspberry PI (rPI) & LED Circuits

[Access This Link for First Steps in Learning about Raspberry PI](Bush_RPI_PYTHON_ROBOTICS.pdf)

### Access Your Assigned Team Raspberry PI

1. [Click here to Verify access to Your Team Raspberry PI  (replace bupiX with your assigned  rPI hostname in the address bar of your browser)](http://bupiX.bush.edu)
Do you see Confetti ?? 

1. [Click here to Access Your Team Raspberry PI's JupyterLab (replace bupiX with your rPI hostname in the address bar of your browser)](http://bupiX.bush.edu:8081)

1. Run the sysinfo.ipynb from the /data folder to see output from your PI

1. Wire-up your RPI following instructions in the First Steps PDF above

1. Write the following lines of code in a new Jupyter Notebook named first_notebook.ipynb inside a code cell. Then Shift-Enter to run it. Do you see your LED blinking?
````
import gpiozero
import time

led = gpiozero.LED(4)

while True:
    led.on()
    time.sleep(1)
    led.off()
    time.sleep(1)
````

- Change sleep time to see if it works
- ChangeGPIO port to 18, re-wire the RPI and see if it works again
