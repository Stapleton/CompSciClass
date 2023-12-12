# Flow control and Loops   
Forks on Forks on Forks into Roundabouts into more Forks   
# Flow Control   
 --- 
You do this already in normal conversation. It's when you are asked a simple answers. "What is your favourite colour?", "Do you like the Red Sox?", "If you were stranded on an island and could bring a lifetime supply of one food with you, what would it be?"   
   
 --- 
## If Statements (2 Choices)   
 --- 
If statements fork logic based on a condition   ![[image_r.png]]
```
// The fork in the flow is right here.
if (Doug.FavouriteColour.equals("Blue")) {
	System.out.printLn("Doug likes Blue.");
} else {
	System.out.printLn("Doug does not like Blue.");
}

```
If-else statements exist, by chaining another if statement onto the previous if statements else keyword. These are cool for specific uses but perform worse than using a switch.   
```
if (Doug.FavouriteColour.equals("Blue")) {
	System.out.printLn("Doug likes Blue.");
} else if (Doug.FavouriteColour.equals("Red")) {
	System.out.printLn("Doug likes Red.");
} else {
	System.out.printLn("Doug does not like Blue or Red.");
	System.out.printLn("Doug's favourite colour is " + Doug.FavouriteColour + ".");
}
```
   
 --- 
## Switch Statements (3+ Choices)   
 --- 
Switch statements filter logic based on the condition. This is for handling different values for a single condition.   
The state of a connection can be `CLOSED, CLOSING, OPEN, OPENING, ERRORED, or WAITING` which is a lot more than 2.![[image_k.png]]
```
switch(Doug.FavouriteColour) {

    case "Blue":
        System.out.printLn("Blue is beautiful like the sky.");
        break;

    case "Yellow":
        System.out.printLn("Do you like sunflowers too?");
        break;

    case "Brown":
        System.out.printLn("Are there other earthy colours you like?");
        break;

    case "Red":
        System.out.printLn("Red Rain. Red Rain. Red Rain.");
        break;

    case "Pink":
        System.out.printLn("GigaChad.");
        break;

    default:
        System.out.printLn("Wow " + Doug.FavouriteColour + " is my favourite colour too!");
}

```
   
 --- 
# Loops   
 --- 
Repeating yourself in person is lame, and so is repeating the same code. If your program will have to do the exact same task multiple times, a loop is perfect for you. Instead of writing the same code 6 times to ask the user a question 6 times, ask it once, wrap a loop around it, limit the loop to 6 times, done. You are trying to accomplish the same thing with less work.   
   
## For Loops   
This code will never get longer past the `OutputPriorities()` as you can just add colours to the top array to extend the list.
   
```
let FavouriteColours = ["Blue", "Red", "Yellow", "Brown", "Pink"];
let Output = [];

function OutputPriorities() {

    for (let ColourIndex = 0; ColourIndex < FavouriteColours.length; ColourIndex++) {
		
        let item = `${ColourIndex+1} -  ${FavouriteColours[ColourIndex]}`;
        Output.push(item);
    }

    console.log(Output.join("\n"));
}

OutputPriorities();
```
This is the equivalent without using a loop. Can you see the problem starting? 5 more list entries means 5 more lines of code.
   
```
function OutputPriorities() {
	console.log("1 - Blue");
	console.log("2 - Red");
	console.log("3 - Yellow");
	console.log("4 - Brown");
	console.log("5 - Pink");
}

OutputPriorities();
```
> This is 20 list items without a loop   

```
function OutputPriorities() {
    console.log("1 - Blue");
    console.log("2 - Red");
    console.log("3 - Yellow");
    console.log("4 - Brown");
    console.log("5 - Pink");
    console.log("6 - Blue");
    console.log("7 - Red");
    console.log("8 - Yellow");
    console.log("9 - Brown");
    console.log("10 - Pink");
    console.log("11 - Blue");
    console.log("12 - Red");
    console.log("13 - Yellow");
    console.log("14 - Brown");
    console.log("15 - Pink");
    console.log("16 - Blue");
    console.log("17 - Red");
    console.log("18 - Yellow");
    console.log("19 - Brown");
    console.log("20 - Pink");
}
OutputPriorities();

```
> This is 20 list items with a loop   

```
let FavouriteColours = ["Blue", "Red", "Yellow", "Brown", "Pink", "Blue", "Red", "Yellow", "Brown", "Pink", "Blue", "Red", "Yellow", "Brown", "Pink", "Blue", "Red", "Yellow", "Brown", "Pink"];
let Output = [];

function OutputPriorities() {

    for (let ColourIndex = 0; ColourIndex < FavouriteColours.length; ColourIndex++) {
        let item = `${ColourIndex+1} - ${FavouriteColours[ColourIndex]}`;
        Output.push(item);
    }

    console.log(Output.join("\n"));
}

OutputPriorities();

```
   
Using loops also has an interesting benefit of being able to make better use of variables allowing customizability.   
> This is the first example again but with an options object used to let us change how the end result looks   

```
let options = {
    separator: " - ",
    joiner: "\n",
    listoffset: 1;
    liststart: 12;
    listlimit: 10;
}

let FavouriteColours = ["Blue", "Red", "Yellow", "Brown", "Pink", "Blue", "Red", "Yellow", "Brown", "Pink", "Blue", "Red", "Yellow", "Brown", "Pink", "Blue", "Red", "Yellow", "Brown", "Pink"];

let Output = [];

function OutputPriorities() {
    for (let ColourIndex = 0; ColourIndex < options.listlimit; ColourIndex++) {

        let item = `${options.liststart + ColourIndex + options.listoffset}${options.separator}${FavouriteColours[ColourIndex]}`;
        // Yes I know ^^ Thats ugly, its expanded further down.

        Output.push(item);
    }
    console.log(Output.join(options.joiner));
}
OutputPriorities();


// Expanding on item
let item = `${options.liststart + ColourIndex + options.listoffset}${options.separator}${FavouriteColours[ColourIndex]}`


`this is words in the string, that [>> ${JSHere} <<] is an escape template, meant to escape the string`
// ^^ This is a string template in Javascript. Its a special string letting you directly put variables in the string without concatenation.

`${options.liststart + ColourIndex + options.listoffset}`;
// ^^ Using the template, we can add 3 numbers together and get the result back as a string

`${options.separator}`
// ^^ This substitutes in the separator defined in our settings

`${FavouriteColours[ColourIndex]}`
// ^^ Substitudes in the value in the array at the current ColourIndex in the loop

// Put it all together and we have absolutely nothing that resembles our result output logic wise anymore, but instead we have taught the computer how to make the list entries and join them.



```
   
