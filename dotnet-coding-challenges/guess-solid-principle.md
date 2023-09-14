# Guess the SOLID principle from the code

The SOLID principles are important to follow when designing a .NET application as it can help reduce dependencies where one area can be changed without affecting others.

Each letter of the SOLID acronym represents one of the five principles. These principles are:

- **S**ingle-responsibility principle <br>
- **O**pen–closed principle<br>
- **L**iskov substitution principle<br>
- **I**nterface segregation principle<br>
- **D**ependency inversion principle<br>

Look at this code:
<br>

```
public abstract class Animal
{
	public abstract int Legs { get; }
}

public class Dog : Animal
{
	public override int Legs { get => 4; }
}

public class Chicken : Animal
{
	public override int Legs { get => 2; }
}
 
public class Leg {
 
	public int CountTotalLegs(Animal[] animals) {
		 
		var legCount = 0;
		 
		foreach (var animal in animals) {    
			legCount += animal.Legs;                    
		}    
		 
		return legCount;
	}
}
```
<br>

We have created a **Animal** abstract class which the **Dog** and **Chicken** classes inherit. The Animal class has an abstract **Legs** property which is overridden in both the **Dog** and **Chicken** class.

In-addition, we have a **Leg** class that has a **CountTotalLegs** method. This passes an array of **Animal** type instances and counts the number of the legs.

Given the design of the code, which SOLID principle do you think we are following?


================================================================
## Answer
We are following the Open-closed principle.

This indicates that software entities should be open for extension but closed for modification.

If we wanted to create a new Animal like a cat, we could create a Cat class, inherit the Animal abstract class and add the number of legs that the Cat has.

As a result, we would not have to make any modifications to the CountTotalLegs method inside the Leg class when adding this animal and still be able to count the total number of legs for all animals.