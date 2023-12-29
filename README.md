import RPi.GPIO as GPIO
import time

GPIO.setmode(GPIO.BCM)

button_pin = 18
led_pin = 17

GPIO.setup(button_pin, GPIO.IN, pull_up_down=GPIO.PUD_UP)
GPIO.setup(led_pin, GPIO.OUT)

try:
    while True:
        button_state = GPIO.input(button_pin)

        if button_state == GPIO.HIGH:
            # Button is NOT pressed, blink the LED
            GPIO.output(led_pin, not GPIO.input(led_pin))
            time.sleep(0.5)
        else:
            # Button IS pressed, keep the LED on
            GPIO.output(led_pin, GPIO.HIGH)

except KeyboardInterrupt:
    GPIO.cleanup()



circuit diagram:(https://user-images.githubusercontent.com/11957243/54884972-204a0800-4e9f-11e9-9d22-28af1fead8cd.png) 
