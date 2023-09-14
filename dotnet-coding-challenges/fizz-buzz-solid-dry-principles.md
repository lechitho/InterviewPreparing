# Writing a the programm "Fizz Buzz" follow SOILD and DRY principles

Can you Write a program that prints the integers from 1 to 100 inclusive.<br>
But:<br>
- For multiples of three, print "Fizz" instead of the number<br>
- For multiples of five, print "Buzz" instead of the number<br>
- For multiples of both three and five, print "Fizz Buzz" instead of the number<br>

should be apply SOLID and DRY principles to the program
<br>

================================================================
## Answer
```
public interface IFizzBuzzRule
    {
        bool Check(int number);
        string GetResult(int number);
    }

    class FizzRule : IFizzBuzzRule
    {
        public bool Check(int number) => number % 3 == 0;
        public string GetResult(int number) => "Fizz";
    }

    class BuzzRule : IFizzBuzzRule
    {
        public bool Check(int number) => number % 5 == 0;
        public string GetResult(int number) => "Buzz";
    }

    class FizzBuzzRule : IFizzBuzzRule
    {
        public bool Check(int number) => number % 3 == 0 && number % 5 == 0;
        public string GetResult(int number) => "Fizz Buzz";
    }

    class DefaultRule : IFizzBuzzRule
    {
        public bool Check(int number) => true;
        public string GetResult(int number) => number.ToString();
    }

    class FizzBuzz
    {
        private readonly IFizzBuzzRule[] rules;

        public FizzBuzz()
        {
            rules = new IFizzBuzzRule[]
            {
				new FizzBuzzRule(),
				new FizzRule(),
				new BuzzRule(),
				new DefaultRule()
            };
        }

        public string GetResult(int number)
        {
            foreach (var rule in rules)
            {
                if (rule.Check(number))
                    return rule.GetResult(number);
            }
            return number.ToString();
        }
    }
    internal class Program
    {
        static void Main(string[] args)
        {
            FizzBuzz fizzBuzz = new FizzBuzz();

            for (int i = 1; i <= 100; i++)
            {
                Console.WriteLine(fizzBuzz.GetResult(i));
            }
        }

    }
```

In this program, the **SOLID** principles are applied by using an interface **IFizzBuzzRule** to define the different rules, and each rule class (**FizzRule**, **BuzzRule**, **FizzBuzzRule**, **DefaultRule**) implements this interface. This allows for easy extension and modification of rules without affecting the existing code.<br>

The **DRY** principle is followed by separating the logic for checking and getting the result for each rule into their respective classes, avoiding repetition of code. The **FizzBuzz** class encapsulates the rules and provides a method for obtaining the result based on the input number. This separation of concerns makes the code more maintainable and flexible.