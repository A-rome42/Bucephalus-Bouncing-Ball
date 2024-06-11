# Bucephalus-Bouncing-Ball
bouncing ball game for Adafruit CPX

## IT BOUNCES
sometimes

My final game will be a timing based game that gradually gets harder until you fail. It is inspired by the mobile game Stack, which I used to play as a kid.

The game begins when you slide the switch. The LED strip will show a light moving from one side of the strip to the other. The objective is to press the corresponding button to “bounce” the ball once it reaches the end of the strip, subsequently sending it in the other direction. If you press the button perfectly at the instant when the light reaches the other side, the speed of the light will not change. If you are slightly early or late, the bouncing will increase in speed proportional to your timing error. That is, the worse you perform, the faster it will speed up, the sooner the game will end (the game ends when the speed of the bouncing light reaches a pre-set threshold determined to be too fast). There will also be the occasional quick-time event, where a flood of purple LEDs light up, and you must shake the board. If you are successful, the light will slow down slightly.

### Buttons
The two buttons tell the game to get the time since the last button press, and restart the arc animation with the new speed.
I am using ISRs and flags to handle these button presses.

### Switch
This is simply here to start the game.
Using a ISR and swicthFlag.

### Acceleromter
If a quick-time event is active and the user shakes the board, It will increase the time it takes for the light bounce.
This is done using getAccelTap().

### LEDS
A trail of lit LEDs will bounce between two sides of the strip to visualize the timing of the game. An occasional flood of purple LEDS will signal a quick-time event.
I have the arcC() and arcCC() functions (clockwise and counter-clockwise) which animate the bouncing light.

The quick time function turns all of the LEDS purple after a random amount of bounces. The arc functions then clear the LEDS as they sweep through

### Speaker
This will beep each bounce, and will also make an alert sound when you lose the game.
Just using tone() function.

