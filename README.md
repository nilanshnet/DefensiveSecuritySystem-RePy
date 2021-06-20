# Defensive Security System: Reference Monitor
The repository contains a security layer reference monitor which keeps backup copy of a file which is useful if incase the file was written incorrectly, built using the security layer functionality in RepyV2. Along with the reference monitor, there are attack cases that can be done on the reference monitor for validation purposes and to identify improvement opportunities.     

## Reference Monitor security layer

### What is a Reference monitor?
A Reference monitor is an access control mechanism (abstract machine) for mediating access to the objects by the subjects, determined using access policies. 
### Design Considerations for this reference monitor security layer:
- The program must not interfere with any functionality of the RepyV2 API calls (refer the *'RepyV2 Library Reference'* in the **References section**).  
- 

## References

- [What is the difference between RePy and Regular Python?](https://github.com/SeattleTestbed/docs/blob/master/Programming/PythonVsRepy.md#python-built-ins-not-in-repy)
- [RepyV2 Setup](https://github.com/SeattleTestbed/docs/blob/master/Contributing/BuildInstructions.md)
- [RepyV2 Library Reference](https://github.com/SeattleTestbed/docs/blob/master/Programming/RepyV2API.md)