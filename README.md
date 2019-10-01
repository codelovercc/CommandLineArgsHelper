# CommandLineArgsHelper
A parsing class to dramatically simplify working with command line arguments in a .Net application (e.g. console, client, or even web application).

It supports a variety of parameter syntaxes, and seamlessly parses all of them into a simplified Dictionary interface of key value string pairs.

_The Code has been adapted from the original source located at:_
https://www.codeproject.com/Articles/3111/C-NET-Command-Line-Arguments-Parser


But it has been updated and simplified with:
- Updated with new C# syntax
- Enhanced class wrapper (e.g. exposed read only dictionary for enumeration)
- More robust parsing for wider array of parameter syntaxes
- Support for both key/value parameters as well as simple boolean flags (param is defined or not)
- Improved thread safety
- Eliminated code duplication

### Usage:
Usage is extremely simple:
```
//Intialize given a string array of arguments (string[])...
//  1) injected into console app main routine
//  2) accessed via Environment.GetCommandLineArgs()
var commandLineArgHelper = new CommandLineArgsHelper(args);

var value = commandLineArgsHelper["paramKeyName"];

Console.WriteLine($"paramKeyName == {value]")
```

### Example:

Command line with all of the following (mixed syntaxes fully supported):
```
-size=100 /height:'400' /day:"happy birthday" -tgif="Thank God It's Friday" -AmINice "Nice stuff !" 
--debug -param1 value1 --param2Alone /param3:"Test-:-work" /param4=--value4-- -param5 "--=nice=--"
```

Will result in an easily accesible set of values as follows:
Command Line Arguments:
   1) [size] == [100]
   2) [height] == [400]
   3) [day] == [happy birthday] //Complex value with spaces in the value
   4) [tgif] == [Thank God It's Friday] //Complex value with spaces & apostrophe (special characters) in the value
   5) [AmINice] == [Nice stuff !]
   6) [debug] == [true] //Boolean flag if a standalone param key is defined
   7) [param1] == [value1]
   8) [param3] == [Test-:-work] //Complex value with colon (special characters) in the value
   9) [param2Alone] == [true]  //Boolean flag if a standalone param key is defined
   10) [param4] == [--value4--] //Complex value with dashes (special characters) in the value
   11) [param5] == [--=nice=--] //Complex value with equal sign (special characters) in the value

```


/*
MIT License

Copyright (c) 2018

Permission is hereby granted, free of charge, to any person obtaining a copy
of this software and associated documentation files (the "Software"), to deal
in the Software without restriction, including without limitation the rights
to use, copy, modify, merge, publish, distribute, sublicense, and/or sell
copies of the Software, and to permit persons to whom the Software is
furnished to do so, subject to the following conditions:

The above copyright notice and this permission notice shall be included in all
copies or substantial portions of the Software.

THE SOFTWARE IS PROVIDED "AS IS", WITHOUT WARRANTY OF ANY KIND, EXPRESS OR
IMPLIED, INCLUDING BUT NOT LIMITED TO THE WARRANTIES OF MERCHANTABILITY,
FITNESS FOR A PARTICULAR PURPOSE AND NONINFRINGEMENT. IN NO EVENT SHALL THE
AUTHORS OR COPYRIGHT HOLDERS BE LIABLE FOR ANY CLAIM, DAMAGES OR OTHER
LIABILITY, WHETHER IN AN ACTION OF CONTRACT, TORT OR OTHERWISE, ARISING FROM,
OUT OF OR IN CONNECTION WITH THE SOFTWARE OR THE USE OR OTHER DEALINGS IN THE
SOFTWARE.
*/
```






