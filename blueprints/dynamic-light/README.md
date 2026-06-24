# dynamic-light

Automatically controls a dimmable light:

- Turns the light on and off based on presence from one or multiple binary sensors
- Adjusts the light brightness periodically based on:
 - A target lux that varies depending on the hour
 - A lux sensor
- Pauses automation until if any button on a remote is pressed:
  - Resumes automation when no presence is detected
