# Lights Control System

This is a simple Python script that controls the lights based on sunrise and sunset times. The script calculates the sunrise and sunset times for a given date, latitude, and longitude using the `astral` module. It then schedules tasks to turn on the lights 30 minutes before sunrise and turn them off 30 minutes after sunset using the `schedule` module. The script runs in an infinite loop, continuously checking for scheduled tasks and executing them at the specified times.

## Prerequisites

- Python 3.x
- `pytz` module
- `astral` module
- `schedule` module

## Installation

1. Clone the repository or download the script to your local machine.

2. Install the required dependencies by running the following command:
   ```bash
   pip install pytz astral schedule
   ```

## Usage

1. Open the script in a text editor or an integrated development environment (IDE) of your choice.

2. Modify the following variables according to your location and preferences:
   - `date`: The specific date for which you want to calculate the sunrise and sunset times.
   - `latitude`: The latitude of your location.
   - `longitude`: The longitude of your location.

3. Save the changes to the script.

4. Run the script using the following command:
   ```bash
   python lights_control.py
   ```

   The script will print the calculated sunrise and sunset times to the console.

5. The script will schedule tasks to turn on the lights 30 minutes before sunrise and turn them off 30 minutes after sunset. The tasks will be repeated every day until the script is stopped.

## Customization

- If you want to modify the timing of turning on and off the lights, you can adjust the timedelta values in the following lines of code:
  ```python
  schedule.every().day.at((sunrise - datetime.timedelta(minutes=30)).strftime("%H:%M")).do(turn_on_lights)
  schedule.every().day.at((sunset + datetime.timedelta(minutes=30)).strftime("%H:%M")).do(turn_off_lights)
  ```
  Simply change the number of minutes before sunrise and after sunset to your desired values.

- If you want to change the time zone used for the calculations, modify the `tz` variable in the `calculate_sunrise_sunset` function:
  ```python
  tz = pytz.timezone("Europe/Belfast")
  ```

- You can customize the `turn_on_lights` and `turn_off_lights` functions to control your actual lights instead of printing messages. Replace the print statements with the appropriate code to control your lights.

## License

This project is licensed under the [MIT License](LICENSE).

Feel free to use, modify, and distribute this code according to the terms of the license.

## Acknowledgements

- The `astral` module: [https://astral.readthedocs.io/](https://astral.readthedocs.io/)
- The `schedule` module: [https://schedule.readthedocs.io/](https://schedule.readthedocs.io/)

## Disclaimer

This script is provided as-is without any warranty. Use it at your own risk.
