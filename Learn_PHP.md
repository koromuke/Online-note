
### PHP
what can php do
/php can generate dynamic page content
/php can create, oren, read, write, delete, and close files on the server
/php can collect form data
/php can send and receive cookies
/php can add, delete, modify data in your database
/php can be used to control useraccess
/php can encryot data

With php you are not limited to output HTML. You can output images, PDF files, and even Flash movies.
you can also output any text, such XHTML and XML.

Why php
/php runs on various platforms(windows, linux. unix. mac os x. etc)
/php is compatible wih almost all servers userd today(apache, iis, etc)
/php supports a wide range of databases
/php is free. Download it from the official php resource
/php is easy to learn and runs efficiently on the server side

What need?
To start using PHP, you can:
/find a web hos with php and mysql support
/install a web server on your own pc, and then install php and mysql

Use a Web host with PHP support

basic php syntax
a php script can be placed anywhere in the document.
a php script starts with <?php and ends with ?>:

<?php
    // php code goes here
?>


the default file extension for php files is ".php".
a php file normally contains HTML tags , and some PHP scripting code.
below, we have an example of a simple PHP file, with a php script that uses a built^-in php function "echo" to output the text "Hello world!" on a web page:

example 
<!DOCTYPE html>
<html>
<body>

<h1>My first php page<h1>

<?php
echo "htllo world";
?>

</body>
</html>

php statement end with a semicolon

comments in php 
A comment in php code is a line that is not read/executed as part of the program. 
Its only purpose is to be read b someone who is looking at the code.

Comments can be used to:
/Let others understand what you are doing
/remind yourself of what you did - Most programmers have wxperioenced coming back to their own work a year or teo later and having to re-figure out what they did.
comments can remind you of what you were thinking whrn you wrote the code/

PHP supports several ways of commenting:
<!DOCTYPE html>
<html>
<body>

<?php
// this is a single-line comment


# this is also a single-line comment

/*
This is a multiple-lines comment blocl
that spans over multiple
lines
*/

// You can also use comments to leave out parts of a code line.
$x = 5 /* + 15 */ + 5;
echo $x;
?>
</body>
</html>

PHP Case Sesitivity
In PHP, all keywords(e.g. if, else, while, echo, etc.), classes, functions, and user-defined functions are NOT case-sensitive

In the example below, all three echo statements below are legal(and equal):
<html>
<body>

<?php
ECHO "Hello World!<br>";
echo "Hello World!<br>";
EcHo "Hello World!<br>";
?>

</body>
</html>

However; all varianle names are case-sensitive.

In the example below, only the first statement will display the value of the $color variable (this is because $coloe, $COLOR, and $coLOR are treated as three different variables
<!DOCTYPE html>
<html>
<body>

<?php
$color = "red";
echo "My car is " . $color . "<br>";
echo "My house is " . $COLOR . "<br>";
echo "My boat is " . $coLOR . "<br>";
?>

</body>
</html>

Variables are "containers" for storing information. 

Creating (Declaring) PHP Variables
In PHP, a variables starts with the $ sign, followed by the name of the varianle:
<?php
$txt = "Hello world!";
$x = 5;
$y = 10.5;
?>

After the execution of the statements above, thevariable $txt will hold the value Hello world!, he variable $x will hold the value 5, and the variable $y wi;; hold the value 10.5

Note: When you assign a text value to a variable, put quotes arount the value.

Note: Ulike other programming languages, PHP has no command for declaring a variable. It si creted the moment you first assign a value to it.
Think of  variables a containers for storing data.

PHP Variables 
A variable can have short name (like x and y) or a more descriptive name (age, carname, total_volume).

Rules for PHP variables:
/A variable starts with the $ sign, followed by the name of the variable
/A variable name must start with a leter or the underscore character
/A variable name cannot start with a number
/A variable name can only contain alpha-numeric characters and underscores(A-z, 0-9, and _)
/variable names are case-sensitive ($age and$AGE are diffirrent variables)

Remember that PHP variable names are case-sinsitive!

Output Variables
The PHP echo statement is often used to output data to the screen.
The following wxample will show hoe to output text and a variable:
<?php
$txt = "W3Schools.com";
echo "I love $txt!";
?>

The following example will produce the same output as the example above:
<?php
$txt = "W3Schools.com";
echo "I love " . $txt . "!";
?>

the following wxample will output the sum of two variables:

<?php
$x = 5;
$y = 4;
echo $x + $y;
?>

Note: Youwill learn more about the echo statement and how to output data to the screen in the next chater.

PHP is a Loosely Typed Language

In the examople above, notice that we did not have to tell PHP whice data type the variable is.

PHP automatically converts the variable to the correct data type, depending on its value.

In other languages such as C, C++ and Java, the programmer must declare the name and type o the variable before using it.

PHp Variales Scope

In PHP , variables can be declared any where in the script.
The scope of a variable is the part of the script where the variable can be referenved / used.

PHP has three different variable scopes:

/local 
/global
/static

Global and Local Scope

A variable declared outside a function has a Global Scope and can only be accessed out side a function.

<?php
$x = 5; // global scope

function myTest() {
    // using x inside this function will generate an error
    echo "<p>Variable x inside function is: $x</p>";
} 
myTest();

echo "<p>Variable x outside function is: $x</p>";
?>

A varible declard within a function has a LOCAL SCOPE and can only be accessed within that function:

<?php
function myTest() {
    $x = 5; // local scope
    echo "<p>Variable x inside function is: $x</p>";
} 
myTest();

// using x outside the function will generate an error
echo "<p>Variable x outside function is: $x</p>";
?>

You can have local variabls with the same name in different functions, because local variables are only recognized by the function in which they are declared.

PHP The global Keyword 

The global keyword is used to access a blobal variable from within a function.
To do this, use the global keyword before the variables (inside the function):

<?php
$x = 5;
$y = 10;

function myTest() {
    global $x, $y;
    $y = $x + $y;
}

myTest();
echo $y; // outputs 15
?>

PHP also stores all global variables in an array calles $GLOBALS[index]. The index holds the name of the variable.
This array is also accessible from within functions and can be used to update global variables directly.

The example above can be rewritten like this: 
<?php
$x = 5;
$y = 10;

function myTest() {
    $GLOBALS['y'] = $GLOBALS['x'] + $GLOBALS['y'];
} 

myTest();
echo $y; // outputs 15
?>

PHP The static Keyword
Normally, when a function is completed/executed , all of its variables are deleted. However, sometimes we want a local variable NOT to be deleted. 
We need it for further job.

To fo this, use the statickeyword whrn you first declare the variable:
<?php
function myTest() {
    static $x = 0;
    echo $x;
    $x++;
}

myTest();
myTest();
myTest();
?>
Then, each time the function is called, that variable will still have the information it contained from the last time the function was called.

Note: the variable is still loval to the fuction.

PHP5 echo and print statement

In PHP there are two basic ways to get output: echo and print.

In this tutorial we use echo (and print) in almost every example. 
So, this chapter contains a little more info about those two output statements.

PHP echo and orint Statements
echo and print are more or less the same. they are both used to output datat to the screen.

the differrences are small:eho has no retur value while print has a retrn value of 1 so it can ve used in wxpressions. 
echo has can take multiple parameters (although such usage is rare) while prnt can take on argument. echo is marginally faster than print.

the PHP echo Statement

The echo statement can be used with or without parentheses: echo or echo()/

Display Text

The folowing example shows how to oput@ut text with the cho comand (notice that the text can contain HTML markup):
<?php
echo "<h2>PHP is Fun!</h2>";
echo "Hello world!<br>";
echo "I'm about to learn PHP!<br>";
echo "This ", "string ", "was ", "made ", "with multiple parameters.";
?>

Display Variables

The following example shows how to output text and variables with the echo statement:
<?php
$txt1 = "Learn PHP";
$txt2 = "W3Schools.com";
$x = 5;
$y = 4;

echo "<h2>" . $txt1 . "</h2>";
echo "Study PHP at " . $txt2 . "<br>";
echo $x + $y;
?>

the PHP print Statement

the print statemen can be used with or without oarentheses: print or print():

Display Text
The folloeing example shows how to output text with the print command (notice that the text can contain HTML markup):
<?php
print "<h2>PHP is Fun!</h2>";
print "Hello world!<br>";
print "I'm about to learn PHP!";
?>
Display Variables
The following wxamle shows how to output text and variables with the print stateent:

<?php
$txt1 = "Learn PHP";
$txt2 = "W3Schools.com";
$x = 5; 
$y = 4;

print "<h2>" . $txt1 . "</h2>";
print "Study PHP at " . $txt2 . "<br>";
print $x + $y:
?>



PHP Data Types

Variables can store data of different types, and different data types can do different thimngs.

PHP suppporrts the folowing data typs :
String 
Integer
Float
Bolean 
Array 
Object
NULL
Resource

PHP Resource
The special resource type is not an actual data type . It is the storing of a reference to fuctions and resource external to PHP.

A common example of using the resource data type is database call.

We will not talk about the resource type here, since it si a advanced topic.
