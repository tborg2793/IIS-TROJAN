# IIS-TROJAN
IIS-Trojan is a native IIS module written in c++ that creates a backdoor in the IIS webserver and carry out custom actions defined by an attacker.

## Documentation

When this IIS native module is installed, it will process every request and method, check for the password header `Sense-Pwd` and compare it to a hard coded value. This is done for filtering purposes. If this value is not matched, the request will continue normally as to not give the target any indication of the existence of a backdoor.

If the password is matched, the communication header is searched for and content is extracted and compare to predefined commands to process the actions.

Four arguments are implemented on the script:
* --url : The URL that will be used to communicate with the backdoor. [Required]
* --password - The pre-shared password on the backdoor [Required]
* --header - The header to use for communication in case it was changed from the default one.
* --method - Change the method to either GET or POST.

Some of the features that are currently implemented in this version are:
* Interactive Command Execution - Allows the execution of commands and retrieve the output.
* Shellcode Injection - Extend functionality by injecting custom shellcode.
* Web Password Extractor - Extract passwords from Web Forms in clear-text.


## Customisation

Before using and compiling the module, you need to change some of the options. To authenticate to the backdoor, the controller uses a pre-shared password with the module. As this is the only mechanism preventing someone else from accessing the backdoor, the default password must be changed.

Apart from the password, other backdoor options can be modified on the Functions.h file:
