# Defensive Security System: Reference Monitor
The repository contains a security layer reference monitor which keeps backup copy of a file which is useful if incase the file was written incorrectly, built using the security layer functionality in RepyV2. Along with the reference monitor, there are attack cases that can be done on the reference monitor for validation purposes and to identify improvement opportunities.     



## Reference Monitor security layer using RepyV2

### What is a Reference monitor?
A Reference monitor is an access control mechanism (abstract machine) for mediating access to the objects by the subjects, determined using access policies. 


### About this Reference Monitor system
This [Reference monitor system](./reference-monitor/Reference_monitor_nn2094.r2py) handles the storage for files in [Repy V2](https://github.com/SeattleTestbed/repy_v2). Using this reference monitor, we are trying to keep a backup copy of the file, so that it can be used if incase the original file was written incorrectly at any time. This kind of technique is commonly used in many modern cloud based security systems like file integrity monitors; also in firmware images, among others. 

[Reference this for more details about building the reference monitor](https://github.com/SeattleTestbed/docs/blob/master/EducationalAssignments/ABStoragePartOne.md)

To validate the reference monitor there are certain [attacks](./attacks/) that we do on a reference monitor. These act as a test cases and help us act as an attacker, trying to bypass the security of this reference monitor.

[Reference this for more details about attacking the reference monitor](https://github.com/SeattleTestbed/docs/blob/master/EducationalAssignments/ABStoragePartTwo.md) 

### Design Considerations and Rules for this reference monitor security layer
- System stores two copies of A/B files on disk. One is a valid backup file (used for Read) and the other one is an active file in which data is written.
- A/B Files are named as **'filename.a'**(valid backup file to read from) and **'filename.b'**(valid file to write to).
- The program must not interfere with any functionality of the RepyV2 API calls like listfiles(), openfile(), removefile(), etc. (refer the *'RepyV2 Library Reference'* in the **References** section).  
- A valid file must have contents starting with **upper case 'S'** and ending with **upper case 'E'**.
- If the file is invalid, the reference monitor writes 'SE' to make it valid.
- Updates the original file with the new data, if new one is valid. 
- No output to the user on normal and invalid operations (no logs).


### Design paradigms at work
- Accuracy: The security layer should only allow or stop certain actions and should not behave in an unexpected manner. For example, if an app tries to read data from a valid file, this must succeed as per normal and must not be blocked.
- Efficiency: The reference monitor security layer's performance must not be compromised. It should only use the minimum necessary amount of resources and should not overdo the resource utilization. For example, keeping a complete copy of every file on disk in memory would be forbidden.
- Security: The reference monitor security layer should not allow any person or process to circumvent the itself. For example, the attacker can cause an invalid file to be read or can write to a valid file, then the security is compromised.


### Get it in Action
To see the reference monitor security layer run:
1. First we need to install and setup RepyV2. Please follow the link in **References** section for the guidelines.
2. After building the RepyV2 in a choice of directory, navigate to the directory using the cmd/terminal. Add the [Reference monitor file](./reference-monitor/Reference_monitor_nn2094.r2py) and one or more of the [attack programs](./attacks/). Remember to use the proper file extensions.
3. Use the following command:
```python repy.py restrictions.default encasementlib.r2py [Reference_monitor_file].r2py [attack_program].r2py```
Replace the ```[Reference_monitor_file].r2py``` with the full name of your reference monitor file and ```[attack_program].r2py``` with the full name of one of the attack cases. Voila!

***If you got an error, please go through the troubleshooting section below.***


### Troubleshooting
- One of the most common errors occur because of using ```print``` instead of ```log``` - Although, Repy is a subset of Python, but its ```print``` is replaced by ```log```. 
- In the execution command above, you must have ```repy.py```, ```restrictions.default```, ```encasementlib.r2py```, the security layer and the program you want to run in the current working directory. If any or all of the above files are not in that directory then you will not be able to run repy files.
- See the Repy V2 library from the **References** section for syntax based troubleshooting.



## References

- [Security Layers in Sandboxes](https://ssl.engineering.nyu.edu/papers/cappos_seattle_ccs_10.pdf)
- [What is the difference between RePy and Regular Python?](https://github.com/SeattleTestbed/docs/blob/master/Programming/PythonVsRepy.md#python-built-ins-not-in-repy)
- [RepyV2 Setup](https://github.com/SeattleTestbed/docs/blob/master/Contributing/BuildInstructions.md)
- [RepyV2 Library Reference](https://github.com/SeattleTestbed/docs/blob/master/Programming/RepyV2API.md)
- [Fixing your Reference monitor bugs for improving security, accuracy and efficiency](https://github.com/SeattleTestbed/docs/blob/master/EducationalAssignments/ABStoragePartThree.md)
- [Building a Reference monitor](https://github.com/SeattleTestbed/docs/blob/master/EducationalAssignments/ABStoragePartOne.md)
- [Attacking the Reference monitor](https://github.com/SeattleTestbed/docs/blob/master/EducationalAssignments/ABStoragePartTwo.md) 
