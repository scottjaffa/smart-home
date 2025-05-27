# Shabbat Mode

## About

Shabbat mode is a set of Home Assistant blueprints which configure a house at the start/end of Shabbat or Yom Tov and automates actions during Shabbat or Yom Tov.  It is designed to be simple yet flexible.  
Using a integration like [Jewish Calendar](https://www.home-assistant.io/integrations/jewish_calendar/), it automatically switches regardless of day of week.
It controls lights, fans, warming devices.  Later todo are HVAC and other home appliances.  



  ## Quick Installation & Setup

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


  | First Header  | Second Header |
| ------------- | ------------- |
| Content Cell  | Content Cell  |
| Content Cell  | Content Cell  |
  
  
  
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
  
  
  
   
