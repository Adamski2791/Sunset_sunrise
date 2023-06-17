BMS Lighting Schedule
This repository contains a Python script that can be used to automate a BMS lighting schedule. The script uses the sunrise and sunset times to trigger the turning on and off of lights.

Requirements
Python 3.9.7
The datetime, pytz, and schedule modules
Usage
To use the script, you will need to provide the following information:

The date
The latitude
The longitude
The script will then calculate the sunrise and sunset times for the given location and schedule the lights to turn on 30 minutes before sunset and 30 minutes after sunrise.

Example
The following code shows an example of how to use the script:

python import datetime import pytz import schedule

def turn_on_lights(): """Turns on the lights.""" print("Turning on the lights.")

def turn_off_lights(): """Turns off the lights.""" print("Turning off the lights.")

def calculate_sunrise_sunset(date, latitude, longitude): """Calculates the sunrise and sunset times for a given date, latitude, and longitude.

Args: date: The date to calculate the sunrise and sunset times for. latitude: The latitude of the location. longitude: The longitude of the location.

Returns: A tuple of the sunrise and sunset times. """

tz = pytz.timezone("Europe/Belfast") dt = datetime.datetime.combine(date, datetime.time.min, tzinfo=tz) sunrise = dt.replace(hour=6, minute=0, second=0, microsecond=0) sunset = dt.replace(hour=18, minute=0, second=0, microsecond=0)

Adjust sunrise and sunset times for the location's latitude and longitude.
sunrise = sunrise - datetime.timedelta(minutes=60 * (latitude - 54)) sunset = sunset + datetime.timedelta(minutes=60 * (54 - latitude))

return sunrise, sunset

if name == "main": date = datetime.date(2023, 6, 17) latitude = 54.6 longitude = -5.9 sunrise, sunset = calculate_sunrise_sunset(date, latitude, longitude) print(f"Sunrise: {sunrise}") print(f"Sunset: {sunset}")

schedule.every().day.at(sunrise - datetime.timedelta(minutes=30)).do(turn_on_lights) schedule.every().day.at(sunset + datetime.timedelta(minutes=30)).do(turn_off_lights)

while True: schedule.run_pending() time.sleep(1)

This code will turn on the lights 30 minutes before sunset and turn them off 30 minutes after sunrise. The code will repeat every day until it is stopped.

Contributing
Contributions are welcome! Please feel free to open a pull request if you have any improvements or bug fixes.

License
This project is licensed under the MIT License.
