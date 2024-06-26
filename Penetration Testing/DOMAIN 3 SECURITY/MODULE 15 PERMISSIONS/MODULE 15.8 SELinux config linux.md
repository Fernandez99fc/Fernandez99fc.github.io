OBJECTIVES---------------
	Explain the purpose of SELinux
	Understand how SELinux is implemented
	Use the gentenforce command to determine the SELinux mode

SECURITY ENHANCED LINUX(SELinux)
--
Security Enhanced Linux was created by the United States National Security Agency (NSA)
Released in 2000 as a security system architecture .
Was derived from a decade of earlier NSA projects.

SELinux is known as a Linux Security Module(LSM).
Primarily used in Red Hat , Fedora and CentOS.
Available in Ubuntu, but we'll cover the LSM AppArmor for Ubuntu.

SELinux Implements Mandatory Access Control(MAC)
By comaprison, the basic Linux Security bits(u,g,o and r,w,x) are known as a Discretionary Access Control(DAC) Mechanism

The MAC design in SELinux restricts all actions to the least privilege
If an action is not explicity granted, it is denied!

MAC Is Implemented in SELinux via policy rules,controlling access to Linux Object types,
including;
users
files
directories
network ports
memory
processes.

There is a bit of SELinux glossary to Know:
Subject- A user or application requesting access to an object
Reference monitor/monitor- Checks the subject's rights to the object
context- a label defined for the object, checked by the monitor to verify a subject has rights to an object.

SUBJECT REQUESTS ACCESS TO AN OBJECT
(REMEMBER: SUBJECT CAN BE A USER OR PROCESS)
                   |
                   |
                   |
                   |
REFERENCE MONITOR CHECKS SUBJECT ACCESS TO AN OBJECT
(MONITOR EXAMINES THE  CONTEXT LABEL.
CONTEXT LABEL DETERMINES WHETHER OR NOT THE  SUBJECT HAS  RIGHT TO THE OBJECT)
                     |
                     |
                     |
                     |
CONTEXT LABEL GRANTS SUBJECT ACCESS TO THE OBJECT
(DOES IT SAY THE SUBJECT HAS ACCESS TO THE OBJECT-           "ACCESS GRANTED")
(DOES IT SAY THE SUBJECT DOES NOT HAVE ACCESS TO THE OBJECT -     "ACCESS DENIED")

SELinux Modes and the getenforce command
--
SELinux has 3 modes in which it operates:

Disabled: In This Mode SELinux is not functional at all and no access checks are performed.

Permissive: In this Mode SELinux performs access checks on subjects but does not block access to objects 
-The access checks are logged and this mode is used auditing and troubleshooting.

Enforcing: SELinux performs access checks and block subject access to objects if it does not match the object context label

The SELinux Mode can be seen by running the getenforce command 
