x��AJ1E]���t:���Y��R�T�I2�8�7/�_=>�ϋ��c���4�*h��M��kQd�H�)r�m���q�:��CL>D��ʙ���%�&!���"Lb�>����>\��kb��y����{kϱ�7XV\WDNv��v:���5��
����˟3�o��&�ʩ���&R�                                                                                                                                                                                                                                                                                                                                           1. Line 41 - Format String Vulnerability
	2. Line 64 - Buffer Overflow Vulnerability

	In client.c
	The call to the vulnerable buffer overflow is at line 56

	Here's the plan
	1. Create a reverse shell function and edit the server code to call it directly
		This will verify that we can actually achjieve the attack 
	2. Add a new function dummy() that will just print a String to standard out and try to call it via a stack overflow and verify that the server prints the string 
		-This will verify that we can actually overflow the buffer and make it execute some code
	3. Create the payload from the remote shellcode we created from 1. 
	4. Alter the client2 app at line 56 to send the remote shell code as the payload.
	
## UPDATES

	The app now does 2 things.
	1. Uses the format string vulnerability to retrieve the saved frame pointer in read_name()
	2. Uses the strcpy stack overflow vulnerability to invoke a shell on the server (not a remote shell)
	
	Next Step: Write a Remote Shell will be invoked by the overflow vulnerability.