# Classes

Object-oriented programming (OOP) is arguably the evolution of elegant software design. Effectively using and writing Classes is the gateway to OOP. The easiest way to explain why classes are so important to modern development is to review a little history of programming. 

#### Procedural Programming

*Procedural code* is what you learn the first day you sit down to learn to program. In the typical *Hello World* example, you have a file such as index.php, you sprinkle some echo statements in it, and run it. Top down execution. Anyone who has built or inherited a website created with only procedural code probably knows all too well that it can be a nightmare to maintain, because you can fix something in one place, but that doesn't fix it anywhere else. Copy and paste are the best friends of the procedural coder.

#### Functions

*Functions* are the most common solution to problems inherent with procedural code. With functions, anytime you need a particular feature, you can write a function and call the function instead. At least with functions, if you need to change something that appears in dozens or hundreds of places on your site, if it's calling a function, changing the way the function works changes the result everywhere that function is called. Functions help you to reuse logic and make your code more compact.

#### Issues with Functions

One of the biggest problems with functions is that they don't play well with others. For example, if you write a <code>function area($width, $height){ }</code> to calculate the area of a rectangle, and someone else writes a <code>function area($radius){ }</code> for calculating the area of a circle, and you want to include their code to work with both rectangles and circles in your project, what do you do? The *function names collide*, your app throws a <code>Fatal error: Cannot redeclare area() (previously declared in /path/to/functions.php:123)</code> error, and you have a problem to deal with. Another issue with functions is that they have to be included either from a file, or worse, copied and pasted, every time they're called. For a single page website, this isn't a big deal, but the larger the app, the more likely you'll run into challenges trying to keep your include functions organized. Another limitation is that you cannot extend a function and add more features to it in a way that is easily packaged for re-use.

#### Classes

With *Classes*, nearly all of the issues with procedural code and using functions are completely solved. Classes are templates which define how objects should be created and what operations you can perform on them. With a class, you can define the allowed data to be used, and provide an API which other consumers of your class must follow. Classes, by design, provide a name space (not to be confused with Namespaces). 

Applying our example above, using classes, you could create a <code>new Rectangle;</code> object and call <code>$rectangle->area($w,$h);</code> using your rectangle area calculation function, and create a <code>new Circle;</code> object and call <code>$circle->area($r);</code> for calculating a circle's area. Even though both classes have an area( ) function (method) the insulation inside of a variable protects the function names. But there's much more to it than that.

#### Objects

Objects are in-memory data structures that encapsulate a set of related information (data, properties) and provide operations (methods) to work with that data. Objects can extend other objects, and thus inherit their functionality and build upon it. For instance, continuing with our example above, we can define a shape object in a shape class, and require that specific future implementations (classes extending our class), such as rectangle and circle, must provide an area method. 

Developing object-oriented code requires careful planning, but the payoff is that it makes application code easier to maintain by reducing the amount of overall code you have to write, and encourages code reuse by providing a consistent way of accessing data and calling methods. Ultimately, OOP saves time when you have to make changes later. 

The Kohana Team has collectively put in thousands of hours toward making the Kohana Framework an elegant, streamlined and efficient collection of classes encapsulating the most common features needed by web developers. One of Kohana's greatest strengths is that it is nearly 100% object-oriented code, it provides a rich set of features, and it's designed in a way that makes it extremely easy to extend it to suit your specific needs. 

To learn more about the history and theory of Object-Oriented Programming, start over at [Wikipedia](http://en.wikipedia.org/wiki/Object-oriented_programming).

#### Classes in Kohana

Model-View-Controller is a design pattern implemented by many object-oriented frameworks, some more strictly than others. In Kohana, your [Models](mvc/models) are classes representing rows from your database or business logic, and [Controllers](mvc/controllers) are classes handling web requests. You can also write your own classes and easily include them in your application or in a [Module](modules). Read their respective pages to learn more.

## Helper or Library?

Kohana 3 does not differentiate between "helper" classes and "library" classes like in previous versions.  They are all placed in the `classes/` folder and follow the same conventions.  The distinction is that in general, a "helper" class is used statically,  (for examples see the [helpers included in Kohana](helpers)), and library classes are typically instantiated and used as objects (like the [Database query builders](../database/query/builder)).  The distinction is not black and white, and is irrelevant anyways, since they are treated the same by Kohana.

## Creating a class

To create a new class, simply place a file in the `classes/` directory at any point in the [Cascading Filesystem](files), that follows the [Class naming conventions](conventions#class-names-and-file-location).  For example, lets create a `Foobar` class.

	// classes/Foobar.php
	
	class Foobar {
		static function magic() {
			// Does something
		}
	}
	
We can now call `Foobar::magic()` any where and Kohana will [autoload](autoloading) the file for us.

We can also put classes in subdirectories.

	// classes/Professor/Baxter.php
	
	class Professor_Baxter {
		static function teach() {
			// Does something
		}
	}
	
We could now call `Professor_Baxter::teach()` any where we want.

For examples of how to create and use classes, simply look at the 'classes' folder in `system` or any module.

## Namespacing your classes

Just as function names can collide in a procedural PHP application, class names can collide in an object-oriented application. The typical scenario is when two different developers create the same class name but the classes don't offer exactly the same api methods, if you'd like to use them both in your project, it can be a real pain to change one class name through a heirarchy of inheritance. Enter [PHP 5.3 Namespaces](http://php.net/manual/en/language.namespaces.php).

Until the following TODO: is done, read [this forum thread on the topic of PSR-0 Support in Kohana 3.3](http://forum.kohanaframework.org/discussion/comment/71039).

TODO: Discuss namespacing to provide transparent extension functionality in your own classes/modules.
