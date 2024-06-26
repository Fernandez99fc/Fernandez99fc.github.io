OBJECTIVES-------------
HOW APPARMOR PERFORMS MANDATORY ACCESS CONTROL(MAC)
LOCATE APPARMOR DIRECOTRIES
USE APPARMOR COMMANDS TO VIEW THE STATUS, CHANGE THE MODE OF APPARMOR , OR MODIFY PROFILES.

APPARMOR OVERVIEW
--
APPARMOR IS USED FOR MANDATORY ACCESS CONTROL(MAC) ON DEBIAN BASED DISTROS
- APPARMOR IS SIMPLER THAN SELINUX  AND IS ONLY FOCUSED ON SECURING APPLICATIONS.

APPARMOR CONFIGURES ACCESS BASED ON POLICIES , LIKE SELINUX, BUT IN APPARMOR THESE ARE CALLED PROFILES
- THESE ARE TEXT FILES THAT COMES WITH LINUX , INSTALLED WITH APPLICATION PACKAGES , OR ARE MADE BY ADMINISTRATORS.
- SPECIFY FILES AND NETWORK PORTS APPLICATIONS ARE PERMITTED TO USE

IT USES PROFILES OF AN APPLICATION TO DETERMINE WHAT FILES AND PERMISSIONS THE APPLICATION REQUIRES.  SOME PACKAGES WILL INSTALL THEIR OWN PROFILES AND ADDIITONAL PROFILES CAN BE FOUND IN THE APPARMOR-PROFILES PACKAGE

PROFILES CAN RUN IN ENFORCE MODE OR COMPLAIN MODE
- ENFORCE IS SIMILAR TO ENFORCING; COMPLAIN IS SIMILAR TO PERMISSIVE IN SELINUX

APPARMOR FILE LOCATIONS AND STATUS
--
PROFILES USED BY APPARMOR ARE FOUND IN THE DIRECTORY /etc/apparmor.d
PROFILES CAN ALSO CONTAIN VARIABLES ,CALLED TUNABLES.
- THESE ARE FILES STORED IN THE /etc/apparmor.d/tunables directory.
- tunables allow you to change profile behaviour without modifying the picture directly.

THE APPARMOR UTILITIES
--
THE FOLLOWING COMMANDS ARE ALL YOU NEED TO KNOW ABOUT APPARMOR FOR LINUX+

- aa -status - view the status of Apparmor
- aa -enforce - enable a specific profile/places a profile into enforce mode.
-or, enable all profiles : aa -enable /etc/apparmor.d/*
- aa -disable - disable a specific profile
-disable all profiles: aa -disable /etc/apparmor.d/*
- aa -complain -turn off a specific profile/places a profile into complain mode
-set all profiles to complain mode: aa -complain /etc/apparmor.d/*
- aa -unconfined - view active network ports that don't have profile defined