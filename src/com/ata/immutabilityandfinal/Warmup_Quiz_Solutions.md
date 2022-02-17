# Warmup Quiz

### Question 1
Consider the following code snippet.

```
    public String convertToUppercase(final String input) {
        input = input.toUpperCase(); 
        return input;
    }
```
    
Will the code compile? Why or why not?

### Question 1: Answer
No. The `input` parameter is marked as `final`, which tells the compiler that the re-assignment of `input` is illegal.
The method `toUpperCase()` returns a new object which we are trying to reassign `input` to. This is not allowed.

### Question 2

Consider the following code snippet.

```
    public void appendMystery(final StringBuilder sb) {
        sb.append("Mystery");
    }
```

Will the code compile? Why or why not?

### Question 2: Answer

Yes.  The `sb` parameter is marked as `final`, which tells the compiler that the re-assignment of `sb` is illegal.
We do not reassign `sb` here, but we do mutate the object. Remember: `final` is not the same as immutable.

### Question 3

Consider the following code snippets.

```
    public final class CustomerSingleItemOrder {
        private final long customerID;
        private final String product;
        private final BigDecimal orderAmount;
        private final Date orderDate;
    
        public CustomerSingleItemOrder(long customerID, String product,
                BigDecimal orderAmount, Date orderDate) {
            this.customerID = customerID;
            this.product = product;
            this.orderAmount = orderAmount;
            this.orderDate = orderDate;
        }
        
        public Date getOrderDate() {
            return new Date(orderDate);
        }
    }
```
```
    public class EmergencyOrderer {
    
        public static void main(String[] args) {
            // Creates the current date
            Date date =  new Date();
            CustomerSingleItemOrder toiletPaperOrder1 = new CustomerSingleItemOrder(
                3456723, "toilet paper", new BigDecimal(3.99), date);
            
            // Update date to tomorrow
            date.setTime(date.getTime() + 86400000);
            CustomerSingleItemOrder toiletPaperOrder2 = new CustomerSingleItemOrder(
                3456723, "toilet paper", new BigDecimal(3.99), date);
        }
    }
```

Draw a memory diagram for the code in the main method.
How many `Date` objects do you have?

### Question 3: Answer

#### Sample memory diagram:
![Sample_memory_diagram](../../../../../../resources/motivate_defensive_copying.png)

We have only 1 `Date` object that is shared by both of the  `CustomerSingleItemOrder` objects. Defensive copying would
prevent this sharing. If we utilized defensive copying, we would have 3 `Date` objects on the heap after we created the
`CustomerSingleItemOrder` objects. 

### Question 4

Immutable objects are automatically thread-safe?

A. true
B. false


### Question 4: Answer
A. true

### Question 5

Consider the following code snippet.

```
    public BigDecimal addFour(final BigDecimal input) {
        return input.add(new BigDecimal(4));
    }
```

Will the code compile? Why or why not?

### Question 5: Answer

The code will compile. The method parameter `input` is marked `final` and so we cannot reassign it. We do not ever 
attempt to reassign it in the code sample. An example of code that wouldn't compile would be:
```
input = input.add(new BigDecimal(4));
return input;
```

The call to `add()` returns a new `BigDecimal` object.

### Question 6

Consider the following class diagram. [plantuml source](https://plantuml.corp.amazon.com/plantuml/form/encoded.html#encoded=NP1B2i8m54NdMKM6IkCAAbBQKd3WI3SGshI69dcIlE90tBlvQ3_E7lU4-qdXa5kSj2AjuixHHidXZYN0ACr0NuGU5FYZdHo25lRSvLwweWsq1TDBgpbAC0dK70NjeqKuWrJAeHQjr5nH1EIg0eT1l_37CVamkhmvULE7fHLyxE1fSa9ejgcqMvgmlm9ibSoMCBQrtFlmB6uQ15QpsIxgts61RAmJZUiyQ-QOfAycUdhx1IVeToQ_LOT0tgGGflCV_m40)

Which fields are immutable?

Which need to be defensively copied?

### Question 6: Answer

**Immutable**
- customerId
- confirmationId
- totalCost

**Defensively copy**
- flightDate
- costBreakdown
