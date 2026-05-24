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
