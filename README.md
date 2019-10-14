# Robot Subsystem Fan Control-Stan Stewart

This package controls up to 10 fans that cool up to 5 subsystems in a common airflow enclosure based on the maximum temperature of all susbsytems.  The main() module is in multi-fan-control.py

Install with: (tested on Windows, should also work on other O/Ss)
> pip install <path_to_source_tar.gz>\multi-fan-control-0.0.1.tar.gz -t <desiredInstallation_path>

------------
This package controls up to 10 fans that cool up to 5 subsystems in a common airflow enclosure.
The system configuration is defined in "fanSubsysConfig.txt" as follows:

--- START Config File Contents ---
fanName1     fanName2     ..... [fanName10]
maxRpmSpeed1 maxRpmSpeed2 ..... [maxRpmSpeed10]
subSysName1  subSysName2  ..... [subSysName5]
--- END Config File Contents -----

Control System Rules:
1. Commanded fan speeds are based on the highest current sampled temperature of any subsystem.
2. The fans may or may not have different maximum speeds
3. Current max temp <= 25 deg C, each fan set to 20% of max speed
4. Current max temp >= 75 deg C, each fan set tofans=100% of max speed
5. If (75 deg C > max temp > 25 deg C), fan speed=linear interpolation between 20% and 100%

This code has been tested on Windows but not Linux or other O/Ss, but it should work agnostically.
The main() routine in multi-fan-control.py currently simulates 10 sets of incoming subsystem
  temperature data.

--- END of README --------
