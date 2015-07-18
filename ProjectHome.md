The cppgenmodel is a model driven generator for C++ code. It provides a C++ metamodel which allows you to create C++ code in a model to model transformation. It is designed to replace model to text transformations in situations where you can not write a straightforward xpand template. It does not provide a complete C++ metamodel. Instead it focuses on structural elements like classes, methods etc. The source code of method bodies is not covered by the meta model and is represented by simple  list of strings.

It provides a xtend library (libCPP) which makes it easy to create classes. The following example shows a simple xtend snippet which creates a single class:
```
CPPModel helloWorldModel () :
	let c = createClass("HelloWorld") : 
		c.add (createConstructor().
			add ("// this is a comment")) ->		
		c.add (createVirtualDestructor()) ->
		// add include for printf in method body
		c.sourceFile.prolog.add ("#include <stdio.h>") ->
		c.add (createMethod("sayHello").
			add("printf (\"Hello World!\\n\");")) ->
	cppModel() 
;
```

You don't have to think of header and source files anymore. The generator takes care what belongs to header and source files. The example above will result in a header and source file for the HelloWorld class.

**Update Site**: http://hg.codespot.com/a/eclipselabs.org/cppgenmodel/org.eclipse.cppgenmodel.update