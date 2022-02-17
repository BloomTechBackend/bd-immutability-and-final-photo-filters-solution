`items` is a mutable variable. There are tests that access its value then modify it, and assert that the class isn't 
modified.
You can get these tests to pass using defensive copying, that involves returning a new instance of the field variable 
type, using the field variable as input.
