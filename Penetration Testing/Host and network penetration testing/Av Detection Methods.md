Types of Antivirus systems:

- Signature based detection- Contains a known property or signature of a malware in their database in form of bytes. Make sure our payload or exploit does not match a signature present in the database. We can bypass a signature based detection by modifying the malware's bytes sequence.

- Heuristic based detection- Relies on rules or policies to determine if a binary is malicious. It looks for specific patterns within the code. or program.

- Behaviour Based Detection- Relies on identifying malware based on it's behaviour. Mostly used on newer malwares.

# Av Evasion Techniques

**On-disk Evasion Techniques-** Techniques used to bypass detection when a malware in form of an executable is on the target's hard disk, usually when you copy a malware to a target system rather than running in memory.

- Obfuscation-  Refers to the method of concealing or hiding something important. This can be to hide certain properties from the Av detection system to be undetected. It re-organizes code in order to make it harder to be detected by an Av.
- Encoding- Refers to changing data into a new format using a scheme e.g to base64. Not really effective because once an encoded format is being identified, it is easily reversible.
- Packing- Generates a new binary structure for an executable with a smaller size therefore provides it a new signature.
- Crypters- Encrypts codes and payloads and decrypts them in memory. The decryption key/function is usually stored in a stub

**In Memory Techniques-** Focuses on manipulation of memory and does not write to the disk.
- Injects payload into a process by leveraging various windows APIs
- Payload is then executed in memory in a separate thread.

# Shellter

A dynamic shell injection PE(portable executable) which injects a payload into a 32bit windows executable and only supports 32 bits payloads. It is used to perform obfuscation, packing and encoding to bypass antivirus system by embedding a payload into a legitimate software and changing the structure to bypass signature based firewalls. You can also encode a msfvenom payload and use it with it.

# Firewall Bypass Using Shellter

**Installation:**
- **sudo apt-get install shellter**
- **sudo dpkg --add-architecture i386**
- **sudo apt-get install wine32**         #Wine is used to run windows executables on unix or linux.

We need to select a windows application to use with the shell injection.

/usr/share/windows-binaries  contains windows executables
![[Uploading_VirtualBox_LINUX 2023_01_07_2024_16_16_33.png..]()
![Uploading VirtualBox_LINUX 2023_01_07_2024_16_16_33.png…]()

I will be using vncviewer.exe  I will copy vncviewer.exe to root's home directory, this is to have a copy and keep the original file in it's state. We will be using the copy for the experiment.

After, navigate to **/usr/share/windows-resources/shellter** - This is where shellter is stored.
![[VirtualBox_LINUX 2023_01_07_2024_17_26_34.png]]

Run "sudo wine shellter.exe"
![[VirtualBox_LINUX 2023_01_07_2024_17_29_00.png]]

Select "A" for automatic
Then it would ask to select our target PE(Portable executable) we want to inject the shellcode with, we can then specify the path to **vncviewer.exe** stored in root's home directory **/root/vncviewer.exe
![[VirtualBox_LINUX 2023_01_07_2024_20_46_10.png]]
Automatically, shellter makes a backup for the executable in **/usr/share/windows-resources/shellter/shellter_backups**, because the operation we are doing isn't reversible. 

![[VirtualBox_LINUX 2023_01_07_2024_17_53_35.png]]We can see information about the minimum operating system it supports for the target in other for it to work, and other info such as the PE which states that the portable executable has not been packed and it has been obfuscated.

![[VirtualBox_LINUX 2023_01_07_2024_17_53_54 1.png]]

![[VirtualBox_LINUX 2023_01_07_2024_19_54_54.png]]**"Y**" to enable to stealth mode which is basically the aim of the task. This will allow  to run vnc as it should and also run the payload secretly in the background after being executed.
![[VirtualBox_LINUX 2023_01_07_2024_20_03_59.png]]You can decide to use a custom payload if you have, type **"L"** to use a listed payload and set lhost and lport to your system ip address and a port.
![[VirtualBox_LINUX 2023_01_07_2024_20_08_46.png]]

![[VirtualBox_LINUX 2023_01_07_2024_20_49_29.png]]Shell Code Injection complete.

![[end.png]]
Send the file to your target's system(This could be via a usb stick or any means). I will be hosting a python server to download the file on the target machine.
![[VirtualBox_LINUX 2023_02_07_2024_08_39_41.png]]
The server runs on **port 8000**. Then we enter the url on our target browser.
![[VirtualBox_windows 7 64x_01_07_2024_20_54_44.png]]Download Vncviewer.exe

Then we need to setup a listener on our system for the target to connect back to since it's a reverse shell.
Open **metasploit** and setup a listener with **use exploit/multi/handler**
![[VirtualBox_LINUX 2023_01_07_2024_20_59_44.png]]
Set lhost, lport and payload. Type run to start listening. Run the application on the target machine and we should have a reverse shell.
