# .net
** Amicable numbers**
using System;<br>

namespace Excercises<br>
{
    class AmicableNumber
    {
        static void Main(String[] args)
        {
            int num1, num2, sum1 = 0, sum2 = 0;
            Console.WriteLine("\n...AMICABLENUMBERS...\n");
            Console.Write("\nenter the first number");
            num1 = Convert.ToInt32(Console.ReadLine());
            Console.Write("\nEnter the second number:");
            num2 = Convert.ToInt32(Console.ReadLine());
            for (int i = 1; i < num1; i++)
            {
                if (num1 % i == 0)
                {
                    sum1 += i;
                }
            }
            for (int i = 1; i < num2; i++)
            {
                if (num2 % i == 0)
                {
                    sum2 += i;
                }
            }
            if (sum1 == num2 && sum2 == num1)
            {
                Console.WriteLine("\nthe numbers {0} and {1} are amicable", num1, num2);

            }
            else
            {
                Console.WriteLine("\nthe numbers {0} and {1} are not amicable", num1, num2);
            }
        }
    }
}
** output**
![image](https://user-images.githubusercontent.com/98379636/152292399-7fadfbb8-0f6f-4402-a150-d1f65bd0719c.png)

