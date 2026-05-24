## Hello folk!
If you are here, you probably want to try or learn the Asier System Programming Language.
ASPL2 isn't that great of a language, I'm going to be honest in that. But everything in <a href="https://asiersystem.github.io/">Asier System</a> depends on it.
So... let's get on it, shall we?
### Before starting, please note that...
If a command's introduction ends with *, it means that this command is still not supported in the official Asier System Web OS

If a command's introduction ends with **, it means that this command has given problems with its current implementation in the official Asier System Web OS

Asier System Uses a centralised coordinates system (x0, y0 is the center). The limits of this position system depends on the resolution of your device (as of version v.1.0.2)

**With that, lets start! fun programming!**

## The basics
Asier System is heavily inspired by Basic and Fortran, the key difference is that it has an easier syntax that's common in most commands.

Commands are in Uppercase, please remember this.
```
PRINT("hello"); <-- Works
print("hello"); <-- Won't work
```
Nested IF statements don't work yet, for some unknown reasons the interpreter freaks out. Avoid using it for now.
In ASPL2, its **mandatory** to put a semicolon at the end of the line. As the ASPL interpreter in Asier system divides the commands using ;

## Printing
Rendering text is a crucial task for most programs, Asier System uses the .asff format, which, currently, is the only font file that works in Asier System.
Asier System uses <a href="https://raw.githubusercontent.com/AsierSystem/AsierSystem/refs/heads/main/Resources/Fonts/ASunicode.asff">ASunicode</a> font for default, and can be found at A:/kernel/fonts/shellfont.asff
Docs on how to manipulate and create .asff fonts will come soon

### Commands used for rendering text
```
PRINT("Hello, world!"); <- Prints text in an automatically selected position
SPECIALTEXT("Hello, world!","x","y","hex colour","size"); <- Prints text with a customizable colour, position and size** (size doesnt work yet and has given problems since build 121, please for normal text use size 1).
SETFONT("path"); <- changes the font depending to the path*
```

## Rendering
ASPL takes advantage of the HTML Canvas Asier System's based on. You can use many rendering commands to paint complex shapes and images.

### Rendering Commands
```
IMAGE("url or path","x","y","witdh","height"); <- Renders an image
SQUARE("x","y","width","height","hex colour","roundness") <- Renders a Rectangle
TRI("vertex1's x", "vertex1's y","vertex2's x","vertex2's y","vertex3's x","vertex3's y","hex colour"); <- Renders a Triangle
PIXEL("x","y","hexcolour"); <- Renders a Pixel
LINE("point1's x","point1's y","point2's x","point2's y"); <- Renders a line
VIDEO("url or path","x","y","witdh","height"); <- Renders a video*
```

## Logic
ASPL2 is able to use Loops, If statements and Variables
### Loops
To make a loop, you just need 2 lines
```
LOOP;
  EVERYTHING IN BETWEEN WILL RUN INDEFINETLY;
ENDLOOP;
```
***Warning***
When using CLEARCANVAS inside a loop, a flickering might appear, this might be dangerous for photosensitive people. To prevent this, use the WAIT command, and make it wait 0 seconds, it will basically pause the system for a frame. Pauses must be higher if an image is rendered in the Loop.
```
LOOP;
  PRINT("hi");
  CLEARCANVAS;
  WAIT("0");
ENDLOOP;
```
### Waiting
If you didn't catch the hint in the warning above, the WAIT command orders the system to wait for a custom number of seconds.
```
PRINT("hi");
WAIT("1");
PRINT("hi");
```
### If Statements
To operate an If statement, you need a similar setup to Loops
```
IF("condition");
  EVERYTHING IN BETWEEN WILL RUN IF THE CONDITION IS TRUE;
ENDIF;
```
There are many ways to manipulate a condition, using...
#### Operations used for conditions
##### 1. Check if a string is the same in both sides
To check if a string or number is the same in both sides, use ==
```
EXAMPLE
IF("1==1");
  PRINT("hi");
ENDIF;
```
##### 2. Compare operation and result
To compare an Operation on the left side to a result on the right side, use =
```
EXAMPLE
IF("1+2=3");
  PRINT("hi");
ENDIF;
```
##### 3. Boolean extravaganza
If any other type of operation returns true, it works.
```
EXAMPLE
IF("1<2");
  PRINT("hi");
ENDIF
```
### Manipulating and Creating Variables.
Variables can be useful to store and operate with temporal chunks of data.
To set up a variable, use:
```
CREATEVAR("name");
SETVAR("name","data");
```
You can also modify a variable using
```
SETVAR("name","data");
ADDVAR("name","number"); <- eg. if name is 1 and you add it 1, it becomes 2. Works with decimal and negative numbers
```
#### How to show/use variables
To show/use a variable, you have to write the name of the variable between % in any field.
```
EXAMPLE
CREATEVAR("hi");
SETVAR("hi","2");
PRINT("%hi%");
```
OUTPUT
```
2
```
##Asking
The ASK command is an input command that asks you for a string of text that you must type. Every text you type before pressing enter will be stored in the laslast_answer System API
```
ASK(">");
PRINT("!last_answer!);
```
## System APIs
The system APIs can be useful for making programs that need to communicate with the System directly.

### List of System APIs

·time -> Returns the time and date in HH:MM:SS YYYY/MM/DD

·battery -> Returns the battery percentage

·battery_ch -> Checks if the device is charging currently.

·battery_suc -> Returns the time in seconds the battery will take to run out

·mousex -> Returns the x position of the mouse cursor

·mousey -> Returns the y position of the mouse cursor

·clicked -> Checks if the mouse is down

·last_file -> Returns the status of the last processed file

·last_answer -> Last text introduced to an ASK input

·last_json -> Last JSON object processed

·js -> Last JS script processed

·last_math -> Last math operation processed

·hostbrowser -> The Browser that's running Asier System

·hostos -> The host OS of the computer (precision may vary)

·arch -> Returns if the computer is 32 bit or 64 bit

·core -> Number of CPU cores the computer has

·memory -> Number of GB of the device (only available in Chrome and Desktop)

·desktop -> Returns a boolean that tells if the version of Asier System is desktop or not

·version -> Returns the Version of Asier System

·build -> Returns the build number of Asier System

·width -> Returns the number of pixels that the HTML canvas' width is.

·height -> Returns the number of pixels that the HTML canvas' height is.

·hour -> Returns the current hour

·min -> Returns the current minute

·sec -> Returns the current second

·tz -> Returns the timezone (UTC+x)

·last_fetch -> Returns the last fetched url

### How to use the System APIs
Similar to variables, to show and use System APIs you must write the name of the API between exclamation marks (!)
```
Example:
PRINT("The current time is !time!");

Output:
The current time is 2026-05-24 12:30:06
```
## Mathematics
The MATH command lets you operate with variables, APIs or numbers. It supports addition, substraction, comparison, fractions, multiplication, division, factorials, exponentials, square roots and the constants pi, euler, tau, phi, sqrt2 and sqrt5.

The processed result is stored in the last_math System API.
```
Example:
MATH("pi+1");
PRINT("!last math!");

Output:
4.14159265359
```
