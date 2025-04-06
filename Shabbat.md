# Shabbat automation  

## Goals  
* one button Shabbat mode, or as close as I can get
* automatically enabled and disabled at appropriate time, with override if away
* Ability to enable manually, whether for early Shabbat or testing
* Customizable - can adjust based on variables
* Minimally confusing - don't do anything so fancy that it is hard to figure out
* User friendly - aka wife acceptance factor

  ## Approach
  Note:  Both shabbat_switcher and shabbat mode are blueprints!
  Using the Jewish Calendar integration, trigger an automation using the issur melacha entity (binary_sensor.jewish_calendar_issur_melacha_in_effect)  
  [shabbat_switcher](ha/automations/shabbat-switcher.yaml)  
  Have that automation test for any conditions, such as away, and triggers the appropriate action (ie. turn shabbat mode on if off and not away, turn shabbat mode off if it was on)  
  This action is setting an input boolean - "Shabbat Active"  
  Have an automation which controls all schedules for Shabbat  
  [shabbat_mode](ha/automations/shabbat-mode.yaml)  
  Have a trigger based automtion which at different times activates different scenes or scripts 
  Use minimal other automations to ensure code is traceable  
  I use a category of "Shabbat" for all the automations to make them easier to find.

  Much more documentation is needed.
  
  
  
   
