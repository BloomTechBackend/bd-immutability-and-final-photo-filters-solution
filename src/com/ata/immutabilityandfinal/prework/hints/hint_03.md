`items` is a mutable variable. There are tests that verify that it is handled properly in the constructor, and then 
assert that the class isn't modified after the mutable objects are changed.
You can get these tests to pass using defensive copying in the constructor, that involves returning a new instance of 
the field variable type, using the field variable as input.
