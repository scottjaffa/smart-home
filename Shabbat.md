# Shabbat automation  

## Goals  
* one button Shabbat mode
* automatically enabled and disabled at appropriate time, with override if away
* Ability to enable manually, whether for early Shabbat or testing
* Customizable - can adjust based on variables
* Minimally confusing - don't do anything so fancy that it is hard to figure out

  ## Approach  
  Using the Jewish Calendar integration, trigger an automation using the issur melacha entity (binary_sensor.jewish_calendar_issur_melacha_in_effect)  
  [shabbat_switcher](/ha/automations/shabbat_switcher)  
  Have that automation test for any conditions, such as away, and triggers the appropriate action (ie. turn shabbat mode on if off and not away, turn shabbat mode off if it was on)  
  This action is setting an input boolean - "Shabbat Active"  
  Have an automation which starts Shabbat - when Shabbat Active goes true, it modifies hardware configuration to turn off all motion sensors and other device configuration, then activates the first scene  
  [shabbat_scenes](ha/automations/shabbat_scenes)  
  Have a trigger based automtion which at different times activates different scenes  
  Use minimal other automations to ensure code is traceable  
  I use a category of "Shabbat" for all the automations to make them easier to find  
  
  
  
   
