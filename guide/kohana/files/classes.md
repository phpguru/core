# Classes

Classes are the evolution of elegant programming. The easiest way to really understand why classes are so important to modern development is to give a little history of programming. 

Procedural code is what you learn the first day you sit down to learn to write code. In the typical Hello World example, you have a file such as index.php, you put some echo statements in it, and run it. Anyone who has built or inherited a website created with only procedural code probably knows all too well that it can be a nightmare to maintain, because you can fix something in one place, but that doesn't fix it anywhere else. Copy and paste are the best friends of the procedural coder.

Functions are the most common solution to problems inherent with procedural code. With functions, anytime you need a particular feature, you can write a function and call the function instead. At least with functions, if you need to change something that appears in dozens or hundreds of places on your site, if it's calling a function, changing the way the function works changes the result everywhere that function is called. Functions help you to reuse logic and make your code more compact.

One of the biggest problems with functions is that they don't play well with others. For example, if you write a function area($width, $height) to calculate the area of a rectangle, and someone else writes a function area($radius) for calculating the area of a circle, and you want to work with both rectangles and circles in your project, what do you do? The function names collide, your app throws errors, and you have a problem to deal with. Another issue with functions is that they have to be included from a file every time they're called. For small applications, this isn't a big deal, but the larger the app, the more likely you'll run into challenges trying to load function files properly. Another limitation is that you cannot extend a function and add more features to it in a way that is easily packaged for re-use.

With classes, nearly all of the issues with procedural code and using functions are completely solved. Classes are templates which define how objects should be created and what operations you can perform on them. With a class, you can define the allowed data to be used, and provide an API which other consumers of your class must follow. Classes, by design, provide a name space (not to be confused with Namespaces). Applying our example above, you could create a new Rectangle( ) and call $rectangle->area($w,$h) using your rectangle area calculation function, and create a new Circle( ) and call $circle->area($r) for calculating a circle's area. Even though both classes have an area( ) function (method) the insulation inside of a variable protects the function names. But there's much more to it than that.

Objects are in-memory data structures that encapsulate a set of related information (data, properties) and provide operations (methods) to work with that data. Objects can be extended, and thus provide inheritance. Continuing with our example, we can define a shape object in a shape class, and require that specific future implementations such as rectangle and circle must provide an area method. 

Developing object-oriented code requires careful planning, but makes application code easier to maintain by reducing the amount of overall code you have to write, and encourages code reuse by providing a consistent way of accessing data and calling methods. The Kohana Team has collectively put in thousands of hours toward making the Kohana Framework an elegant collection of the most common features needed by web developers. One of Kohana's greatest strengths is that it is nearly 100% object-oriented code, that provides a rich set of basic features, but is also extremely easy to extend to suit your specific needs. 

Model-View-Controller is a design pattern impemented by many object-oriented frameworks. In Kohana, your [Models](mvc/models) are classes representing rows from your database or business logic, and [Controllers](mvc/controllers) are classes handling web requests. You can also write your own classes and easily include them in your application or in a module. Read their respective pages to learn more.

## Helper or Library?

Kohana 3 does not differentiate between "helper" classes and "library" classes like in previous versions.  They are all placed in the `classes/` folder and follow the same conventions.  The distinction is that in general, a "helper" class is used statically,  (for examples see the [helpers included in Kohana](helpers)), and library classes are typically instantiated and used as objects (like the [Database query builders](../database/query/builder)).  The distinction is not black and white, and is irrelevant anyways, since they are treated the same by Kohana.

## Creating a class

To create a new class, simply place a file in the `classes/` directory at any point in the [Cascading Filesystem](files), that follows the [Class naming conventions](conventions#class-names-and-file-location).  For example, lets create a `Foobar` class.

	// classes/foobar.php
	
	class Foobar {
		static function magic() {
			// Does something
		}
	}
	
We can now call `Foobar::magic()` any where and Kohana will [autoload](autoloading) the file for us.

We can also put classes in subdirectories.

	// classes/professor/baxter.php
	
	class Professor_Baxter {
		static function teach() {
			// Does something
		}
	}
	
We could now call `Professor_Baxter::teach()` any where we want.

For examples of how to create and use classes, simply look at the 'classes' folder in `system` or any module.

## Namespacing your classes

TODO: Discuss namespacing to provide transparent extension functionality in your own classes/modules.
