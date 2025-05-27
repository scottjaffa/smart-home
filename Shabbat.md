# Shabbat Mode

## About

Shabbat mode is a set of Home Assistant blueprints which configure a house at the start/end of Shabbat or Yom Tov and automates actions during Shabbat or Yom Tov.  It is designed to be simple yet flexible.  
Provides schedules, separate bedroom settings for kids, meal schedules, and food warming.  It controls lights, fans, warming devices.  Later todo are HVAC and other home appliances.  

Using a integration like [Jewish Calendar](https://www.home-assistant.io/integrations/jewish_calendar/), it adjusts each week for candlelighting times and automatically runs regardless of day of week (for Yom Tov).


  | Component  | Description | 
| ------------- | ------------- |
| [Jewish Calendar Integration](https://www.home-assistant.io/integrations/jewish_calendar/)  | This provides the sensor that denotes when Shabbat or Yom Tov is active, adjusting for candle lighting times and Yom Tov dates  | 
| [Shabbat Switcher Blueprint](https://github.com/scottjaffa/smart-home/blob/main/ha/automations/shabbat-switcher.yaml) | This provides the logic for when to switch the house into Shabbat mode, including home/away and early Shabbat/Yom Tov |
| Shabbat Active [input boolean helper](https://www.home-assistant.io/integrations/input_boolean/)  | This denotes when the house is in Shabbat mode and controls the activation of the main switch  |
| [Shabbat Mode Blueprint](https://github.com/scottjaffa/smart-home/blob/main/ha/automations/shabbat-mode.yaml) | This provides the automations controlling the house while active |
| Shabbat Start Script | An example script that runs at the start of Shabbat mode |
| Shabbat End Script | An example script that runs at the end of Shabbat mode |


  ## Quick Installation

  1.  Install Jewish Calendar or another integration which provides a binary sensor to identify the start of Shabbat.
  2.  Create an input boolean helper, recommended name "Shabbat Active".
  3.  (Optional but highly recommended) Install The [Shabbat Switcher](https://github.com/scottjaffa/smart-home/blob/main/ha/automations/shabbat-switcher.yaml) blueprint.
  4.  Install the [Shabbat Mode](https://github.com/scottjaffa/smart-home/blob/main/ha/automations/shabbat-mode.yaml) blueprint.
  5.  Create Home Assistant scenes for each schedule in Shabat Mode.
  6.  (Optional) Create or import any scripts for starting or ending Shabbat mode.
  7.  Deploy the Shabbat Switcher blueprint in Home Assistant.
     - Set up the binary sensor (default is Jewish Calendar issur_melacha_in_effect) as the Shabbat trigger.
     - Set up the input boolean helper (Shabbat Active) which is set when Shabbat Mode is Active.
  8. Deploy the Shabbat Mode blueprint in Home Assistant.



## Detailed Installation


## Usage

### Shabbat Switcher

### Shabbat Mode
To use Shabbat Mode it needs a trigger sensor to identify when Shabbat mode is active.  Without this nothing will run.
For start and end, select scripts and scenes to run (note that scripts run before scenes).
For each each schedule, select whether it is active, what time it runs at, and the scripts and/or scenes to run.
The configurable schedules are:

  | Schedule  | Notes |
| ------------- | ------------- |
| Dinner  | This schedule has start and end times and scenes associated with it |
| Evening  |   |
| Night  |   |
| Wakeup  |   |
| Morning  |   |
| Lunch  | This schedule has a start and end times and scenes associated with it |
| Afternoon  |   |
| Dusk  | This schedule is an offset from dusk time |
| Bedroom  | This is designed for kids bedrooms that need to run earlier.  If it is set before Shabbat started, it will run at Shabbat start  |
| Food Heating  | This defines the warming devices and the times they should start.  They automatically end at the end time of the meal schedules listed above  |


  
  
  Using the Jewish Calendar integration, trigger an automation using the issur melacha entity (binary_sensor.jewish_calendar_issur_melacha_in_effect)  
  [shabbat_switcher](ha/automations/shabbat-switcher.yaml)  
  Shabbat Switcher uses that binary sensor to trigger.
  Have that automation test for any conditions, such as away, and triggers the appropriate action (ie. turn shabbat mode on if off and not away, turn shabbat mode off if it was on)  
  This action is setting an input boolean - "Shabbat Active"  
  Have an automation which controls all schedules for Shabbat  
  [shabbat_mode](ha/automations/shabbat-mode.yaml)  
  Have a trigger based automation which at different times activates different scenes or scripts 
  Use minimal other automations to ensure code is traceable  
  I use a category of "Shabbat" for all the automations to make them easier to find.

  Much more documentation is needed.
  
  
  
   
