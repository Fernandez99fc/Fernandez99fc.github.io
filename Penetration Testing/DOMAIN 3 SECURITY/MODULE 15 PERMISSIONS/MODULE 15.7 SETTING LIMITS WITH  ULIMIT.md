OBJECTIVES-----------
Understand the purpose of ulimit command 
Explain how ulimit can be used to restrict user accounts.

Each user on a system consumes resources like cpu time and memory or file space. So without guard rails on a system, it's easy for users to overload the system.
Ulimit allows you to restrict user to system resources
If we reached the limit of open file then we get ther error message is like |"too many files open"
Ulimit provides control over the resources available to the shell and processes it creates, on systems that allows such control.  It is a bash built-in command

There are a huge number of options to ulimit but these are the most useful:
ulimit -a - See the limit on the current user account
ulimit -f -Set the limit on the size of files created.
ulimit -l -Set the maximum memory that can be locked by  a user.
ulimit -t -Set the maximum CPU time a User is allowed to use.
ulimit -u- set the mamimum number of processes available to a single user.  The max number is 64000
To make these options permanent they need to be placed in:
--
user configuration file- ~/.bashrc or ~/.profile
global configuration files -/etc/bashrc or /etc/profile

/etc/security/limit.conf