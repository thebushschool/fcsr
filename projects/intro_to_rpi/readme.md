# Introduction to Raspberry PI (rPI) & LED Circuits

### [Reference document for First Steps in Learning about Raspberry PI](Bush_RPI_PYTHON_ROBOTICS.pdf)

### Step 1. Geto to know and then Access Your Assigned Team Raspberry PI

1. Let's examine your rPI host and get to know it. It has to be handled delicately at all times!. We will now power it up and wait for 2 minutes. We can then make sure it shows up on the Bush network!
![rPI](rPI.png)

1. [Click here to Verify access to Your Team Raspberry PI  (replace bupiX with your assigned  rPI hostname in the address bar of your browser)](http://bupiX.bush.edu)
Do you see Confetti ?? 

1. [Click here to Access Your Team Raspberry PI's JupyterLab (replace bupiX with your rPI hostname in the address bar of your browser)](http://bupiX.bush.edu:8081)
1. Run the sysinfo.ipynb from the /data folder to see output from your PI. If you do not see sysinfo.ipynb you can [download it here](sysinfo.ipynb) and then drag the file to your PI

1. We will use the Multimeter to measure some voltages from the pins.
![multi](multimeter.png)

1. Create a wiring diagram for the following. 
1. Wire-up your RPI following diagram below. Note LED +lead is connected to GPIO4. The other (-ve) lead of the LED can be directly connected to the ground via the -ve rail of the breadboard.
![led1](circ1_led.png)
![led2](circ1_led_pic.png)

1. Create a new Jupyter Notebook. Name it ```first_notebook.ipynb```. Copy the following lines of code inside a code cell in your notebook. Then Shift-Enter to run it. Do you see your LED blinking?


````
# first led circuit
from gpiozero import LED
import time

# LED setup
gpio_ledpin = 4
led = LED(gpio_ledpin)

while True:
    led.on()
    time.sleep(1)
    led.off()
    time.sleep(1)
````

### Step 2. LED circuit
1. Change sleep time to see if it works
2. Change LED to GPIO port to 18. The other (-ve) lead of the LED can be directly connected to the ground via the -ve rail of the breadboard. Change the code correspondingly and and run to see if it works again!

### Step 3. Button control
1. Now we are going to add a Button to the circuit.
1. Create a wiring diagram for the following. 
1. Change LED to GPIO port back to GPIO4. Install the button further down the breadboard so as not to interfere with the led previously installed.
![but1](circ2_button.png)
![but2](circ2_button_pic.png)

1.  Connect one leg of the button to GPIO17 and the other to the ground rail.

1. Create another Jupyter Notebook.  Name it ```button_test.ipynb```. Copy the following lines of code inside a code cell in your notebook. Ensure that the code correctly reflects the GPIO pins you used for the LED and Button.

1. Note that we have added a callback function for the button called ```pressed``` in the ```BUTTON setup ``` block. We will walkthrough this code together.  The ```MAIN loop``` block remains the same as before, although the LED is blinking faster!

````
from gpiozero import LED, Button
from time import sleep
from datetime import datetime

# LED setup
gpio_ledpin = 4
led = LED(gpio_ledpin)

# BUTTON setup
def pressed(button):
    current_time = datetime.now()
    print(f'button {button.pin.number} was pressed @ {current_time}')
    
gpio_btnpin = 17
button = Button(gpio_btnpin)
button.when_pressed = pressed

# MAIN loop
while True:
    led.on()
    sleep(0.5)
    led.off()
    sleep(0.5)

````

1. Run the ```button_test.ipynb``` notebook.  Now you will see that both the LED and Button are functional, except they are NOT linked to each other.  This will be the purpose of the next step.

### Step 4. Control LED via Button
1. Create a 3rd Jupyter Notebook to accomplish this Step. Name it ```toggle_led.ipynb```

1. Now we will attempt to combine the Button capability to turn on or turn off the LED. This means that the button needs to behave like a toggle switch. 

1. Create a wiring diagram to accomplish this

    * Press it once - LED should turn On.
    * Press it again - LED turns off.  

1. We will start by making a modification to the function by adding a global ```button_state``` variable which will toggle between True and False depending on the button pushes. Add the following code to ```toggle_led.ipynb```
    ````
    from gpiozero import LED, Button
    from time import sleep
    from datetime import datetime

    # LED setup
    ledpin = 4
    led = LED(ledpin)

    # BUTTON setup
    def pressed(button):
        global button_state
        current_time = datetime.now()
        print(f'button {button.pin.number} was pressed @ {current_time}')
        button_state = not button_state

    btnpin = 21
    button = Button(btnpin)
    button.when_pressed = pressed
    button_state = True

    # MAIN loop
    while True:
        led.on()
        sleep(0.5)
        led.off()
        sleep(0.5)
    ````
1. Your challenge is to modify inside the ```MAIN loop``` block underneath the ```While True:``` and add to make it work.

    ````
    if button_state:
        # some code ..
    else:
        # some code ..
    ````

    Consult with your team member to see if you can accomplish this.  I will be there to help!

1. Create a wiring diagram to accomplish this

### Step 5. Finally let us create a Button Reaction Game!

1. Create a last Jupyter Notebook to accomplish this.  Name it ```reaction_game.ipynb```.

1. Copy the code below, your job is to wire the circuit according to the the code!

    ````
    from gpiozero import LED, Button
    from time import sleep
    from datetime import datetime

    # led setup
    ledpin = 4
    led = LED(ledpin)

    # Button setup
    def pressed(button):
        global button_state
        current_time = datetime.now()
        print(f'button {button.pin.number} was pressed @ {current_time}')
        button_state = not button_state

    btnpin = 21
    button = Button(btnpin)
    button.when_pressed = pressed
    button_state = True

    # main loop
    while True:
        if button_state:
            led.on()
        else:
            led.off()
        sleep(0.5)
        
    ````
1. Once circuit is wired according to the code, two of you can play this game to see who has the fastest finger in the West! Seek help if you cannot get it to work.