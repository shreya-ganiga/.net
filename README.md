# .net
** Amicable numbers**
using System;<br>

namespace Excercises<br>
{<br>
    class AmicableNumber<br>
    {<br>
        static void Main(String[] args)<br>
        {<br>
            int num1, num2, sum1 = 0, sum2 = 0;<br>
            Console.WriteLine("\n...AMICABLENUMBERS...\n");<br>
            Console.Write("\nenter the first number");<br>
            num1 = Convert.ToInt32(Console.ReadLine());<br>
            Console.Write("\nEnter the second number:");<br>
            num2 = Convert.ToInt32(Console.ReadLine());<br>
            for (int i = 1; i < num1; i++)<br>
            {<br>
                if (num1 % i == 0)<br>
                {<br>
                    sum1 +=i;<br>
   
                }<br>
            }<br>
            for (int i = 1; i < num2; i++)<br>
            {<br>
                if (num2 % i == 0)<br>
                {<br>
                    sum2 += i;<br>
                }<br><br><br>
            }<br><br>
            if (sum1 == num2 && sum2 == num1)<br>
            {<br>
                Console.WriteLine("\nthe numbers {0} and {1} are amicable", num1, num2);<br>

            }<br>
            else<br>
            {<br>
                Console.WriteLine("\nthe numbers {0} and {1} are not amicable", num1, num2);<br>
            }<br>
        }<br>
    }<br>
}<br>
** output**
![image](https://user-images.githubusercontent.com/98379636/152292399-7fadfbb8-0f6f-4402-a150-d1f65bd0719c.png)

