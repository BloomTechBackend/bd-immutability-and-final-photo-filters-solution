### Immutable Purchase Orders

**Branch name:** immutabilityandfinal-prework

**RDE workfows:**
* `rde wflow run immutabilityandfinal-prework-purchaseordertest`

Expected time required: 15 min

The premise of this activity is that the purchase order is generated at a particular time, and is not changeable
thereafter. The user should be able to retrieve the purchase order, and even make some simple calculations based on
the instance variables, but attempts to modify any elements in the purchase order once initially made will not be
successful. Your task will involve proper use of the `final` keyword as well as other practices described in the Lesson
to ensure that the instance variables (both immutable and mutable) and the class behavior are preserved once created. 

Please update the `PurchaseOrder` class found in this java package to turn it into an immutable class with: 

**Constructor**
* Use the arguments on the constructor to initialize the instance variables.
* **NOTE:** some of these instance variables are mutable. For these variables, use defensive copying in the constructor.

**Instance Variables:** 
* `ZonedDateTime orderDate`: The date the order was created
* `BigDecimal subtotal`: The subtotal cost of the order not including taxes
* `String vendor`: The vendor selling the items
* `List<String> items`: The list of items being purchased

**Methods:**
* getters for all instance variables
  * **NOTE:** some of these instance variables are mutable. For these variables, use defensive copying in the getters.
* `BigDecimal determineBillableCost(Double taxRate)`: returns `(1 + taxRate) * subtotal`

All tests in run by the `immutabilityandfinal-prework-purchaseordertest` workflow should pass when `PurchaseOrder`
is immutable. There is no 'main' method to run.


HINTS:
* [The tests involving the getters are failing and I don't know why!](./hints/hint-00.md)
* [I still can't get the getter tests to pass!](./hints/hint-01.md)
* [The tests involving the constructor are failing and I don't know why!](./hints/hint-02.md)
* [I still can't get the constructor tests to pass!](./hints/hint-03.md)
