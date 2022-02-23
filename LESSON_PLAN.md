# Lesson Plan

Make sure you have the solution available to reference.

Follow the README through the Code Walkthrouhg. Feel free to open the classes and talk through the various points that are made in the README. 

At a high level, the classes that you'll be more interested in are the Converter implenentations (GreyscaleConverter, InversionConverter, and SepiaConverter) and the models (PrimePhoto, Pixel, and RGB). Essentailly, you'll want to make their variables final so that they must be copied (instead of referenced) if you make a change.

Start with the models and explain that accessing the same item in different threads can lead to issues. This code is trying to be careful, but a more secure way of handling this is to use `final` with variables. This forces any changes to occur as copies instead of references. Some methods within these models may need to be updated (`PrimePhoto`'s constructor and `getPixel` should change to copy the list, `RGB` should return an object in its converstion methods).

With the models update, you'll need to make some updates elsewhere that use these models. Each of the converters will need to assign the result of the converstion (e.g. the result of `toSepia` should be saved in teh `rbg` variable).

Run the tests and see the resultling images to see if it all worked.

