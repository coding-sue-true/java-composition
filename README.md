## java-composition

### This example
- The PC has a case, has a motherboard, has a monitor

- Font: https://www.adobe.com/devnet/actionscript/learning/oop-concepts/composition-and-aggregation.html

# Composition
- Composition is about expressing relationships between objects. Think about the chair example. A chair has a Seat. A chair has a back. And a chair has a set of legs. The phrase "has a" implies a relationship where the chair owns, or at minimum, uses, another object. It is this "has a" relationship which is the basis for composition.

- Consider the class definitions for each of the chair parts and the chair itself below. Note that for simplicity, each of the chair parts is just an empty object. They would each have properties and methods of their own in a real application.

```
package chairs.parts {
    public class Seat {
        public function Seat() {}
    }
}

package chairs.parts {
    public class Back {
        public function Back() {}
    }
}

package chairs.parts {
    public class Leg {
        public function Leg() {}
    }
}

package chairs {
    import chairs.parts.Back;
    import chairs.parts.Leg;

    public class Chair {

        protected var back:Back;
        protected var seat:Seat;
        protected var legs:Array;

        public function Chair() {
            back = new Back();
            seat = new Seat();

            legs = new Array();
            legs.push( new Leg() );
            legs.push( new Leg() );
            legs.push( new Leg() );
            legs.push( new Leg() );

        }
    }
}
```

- In this example, the Chair object itself is composed of an instance of the Back class, an instance of the Seat class and 4 instances of the Leg class. Each of those objects has its own responsibilities but they are related together in a composition referred to as Chair.

- Using composition does not mean you will never use inheritance. In fact, when you begin composing a new object, you will frequently still need to choose an appropriate super class. Supposing that you wanted to create an OfficeChair class, you might start by extending Chair and then adding an additional component which allows the seat to swivel freely. It would be appropriate to say the OfficeChair is a Chair but it has a swivel.

```
package chairs.parts {
    public class Swivel {
        public function Swivel() {}
    }
}
package chairs {
    import chairs.parts.Swivel;

    public class OfficeChair extends Chair {
        protected var swivel:Swivel;

        public function OfficeChair() {
            super();            
            swivel = new Swivel();
        }
    }
}
```

- In the code above you are visibly using both inheritance and composition to create a new object. This is the most common way you will work when building complex objects.
