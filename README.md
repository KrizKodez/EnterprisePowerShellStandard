# PESTemplates
PowerShell template files to kick off with scripting in a standardized form.

## Motivation
The templates are a good starting point for working in a team and later perhaps in a larger audience to build a unified code base. Through the defined structure and formatting it is easier to read, debug or adapt other people's code. The defined metadata captures important data about the code and allows the automated creation of a script catalog. The creation of a lightweight function library is also supported, which can avoid the much more complex creation of PowerShell modules.

## Description
In principle, we differentiate between two types of scripts, Controller scripts and Tool scripts.

| Type | Template |
|------|------------|
| Controller | ControllerWithFunctionsTemplate.ps1
| | ControllerWithoutFunctionsTemplate.ps1
| Tool | PrivateLibraryTemplate.lib.ps1
| | PublicLibraryTemplate.lib.ps1

Controllers are the frontend of a PowerShell solution, the workhorse, so to speak, this is where the task is defined and solved. Tool scripts provide support in the form of functions, scriptblocks or modules, they are loaded and used by the Controllers.

### **ControllerWithFunctionsTemplate.ps1**
This template is used if the Controller is structured through usage of functions which reside inside the script. It uses a function called Main (like in other programming languages) as visible entry point for the code execution. Because of the fact that the Main function is the first function in the script it avoids searching where the script starts and annoying scrolling through a lot of functions which are not interesting when inspecting for the first time.

### **ControllerWithoutFunctionsTemplate.ps1**
This template is used if the Controller does not have functions inside or load all needed functions from a library file.

### **PrivateLibraryTemplate.lib.ps1**
This template is a Tool and consist of all functions which are used only in one dedicated Controller. If functions could be used in other Controllers as well the author should move them to a public function library.

### **PublicLibraryNameTemplate.lib.ps1**
This template is a Tool and contains a Company wide used function library.

### **Naming the Templates in real use**
As with all names they should be unique and descriptive but in the practice of the author it has been shown that administrators are using the Verb-Noun naming schema for PowerShell functions introduced from Microsoft also for the Controller names which leads in many cases to a lack of clear names. So the recommendation is:
**<p align="center">:exclamation: Do not use Verb-Noun convention for Controller names :exclamation:</p>**

If a Controller stores his functions in a private library Template its name must be identical with the Controller name extended with the suffix .lib.ps1 e.g.
```
RemoveFileShare.ps1
RemoveFileShare.lib.ps1
```

For public library files the Tool name must be extended with the suffix [CompanyName].lib.ps1 e.g.
```
ActiveDirectory.ACME.lib.ps1
```
where the name of the library should describe the scope of the functions it contains. If the amount of library files of the company grow the PublicLibraryName itself could be devided into groups with the dot-notation comparable to the .Net-Namespaces e.g.
```
ActiveDirectory.User.ACME.lib.ps1
ActiveDirectory.Group.ACME.lib.ps1
Active.Directory.Check.ACME.lib.ps1
```
In this way a hierachical structure of library files is created.


## Contributing
All Administrators which using PowerShell are very welcome to help and make the templates better, more useful or contribute new ideas.


## License

This project is licensed under the terms of the GPL V3 license. Please see the included Licence.txt file for more details.
