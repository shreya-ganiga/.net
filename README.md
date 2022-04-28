    
# .net
** Amicable numbers**
using System;<br>

namespace Excercises<br>
{
    class AmicableNumber<br>
    {
        static void Main(String[] args)<br>
        {
            int num1, num2, sum1 = 0, sum2 = 0;<br>
            Console.WriteLine("\n...AMICABLENUMBERS...\n");<br>
            Console.Write("\nenter the first number");<br>
            num1 = Convert.ToInt32(Console.ReadLine());<br>
            Console.Write("\nEnter the second number:");<br>
            num2 = Convert.ToInt32(Console.ReadLine());<br>
            for (int i = 1; i < num1; i++)<br>
            {
                if (num1 % i == 0)<br>
                {
                    sum1 +=i;
   
                }
            }
            for (int i = 1; i < num2; i++)<br>
            {
                if (num2 % i == 0)<br>
                {
                    sum2 += i;<br>
                }
          }
            if (sum1 == num2 && sum2 == num1)<br>
            {
                Console.WriteLine("\nthe numbers {0} and {1} are amicable", num1, num2);<br>

            }
            else<br>
            {
                Console.WriteLine("\nthe numbers {0} and {1} are not amicable", num1, num2);<br>
            }
        }
    }
}
** output**
![image](https://user-images.githubusercontent.com/98379636/152292399-7fadfbb8-0f6f-4402-a150-d1f65bd0719c.png)
  
    
**   volume**
using System;
namespace Exercises
{
 class Box
    {
        float width;
        float height;
        float length;
        public float Volume
        {
            get {return width*height*length;}
        }
        public Box(float width,float height,float length)
        {
            this.width = width;
            this.height = height;
            this.length = length;
        }
        public static float operator+ (Box box1,Box box2)
        {
            return box1.Volume+box2.Volume;
        }
        public override String ToString()
        {
            return "box with width" + width +",height" + height +"and length"+ length;
        }
    }
    class OperatorOverloading
    {
        public static void Main()
        {
            Box box1 = new Box(10, 20, 30);
            Box box2 = new Box(25, 32, 15);
            Console.WriteLine("volume of {0} is:{1}", box1,box1.Volume);
            Console.WriteLine("volume of{0} is:{1}", box2,box2.Volume);
            Console.WriteLine("volume after adding boxes:{0}", box1+box2);
        }
    }
}
<br>
**  output **


![image](https://user-images.githubusercontent.com/98379636/152475266-4348153d-0015-4262-a63a-c5505976fc99.png)



**  multilevel inheritance**
using System;
namespace exercises
{
    class PersonalDetails
    {
        string name;
        int age;
        string gender;
        public PersonalDetails(string name, int age, string gender)
        {
            this.name = name;
            this.age = age;
            this.gender = gender;
        }
        public virtual void Display()
        {
            Console.WriteLine("\n______PERSONAL DETAILS____\n");
            Console.WriteLine("Name       :" + name);
            Console.WriteLine("Age         :" + age);
            Console.WriteLine("Gender     :" + gender);
        }
    }
    class CourseDetails : PersonalDetails
    {
        int regNO;
        String Course;
        int semester;
        public CourseDetails(string name, int age, string gender, int regNo, string course, int semester) : base(name, age, gender)
        {
            this.regNO = regNo;
            this.Course = course;
            this.semester = semester;
        }
        public override void Display()
        {
            base.Display();
            Console.WriteLine("\n-----COURSE DETAILS-----\n");
            Console.WriteLine("Register Number:" + regNO);
            Console.WriteLine("Course    :" + Course);
            Console.WriteLine("semester     :" + semester);
        }

    }
    class MarksDetails : CourseDetails
    {
        int[] marks = new int[5];
        int total;
        float average;
        string grade;
        int flagFail;
        public MarksDetails(string name, int age, string gender, int regNo, string course, int semester, int[]marks): base(name, age, gender, regNo, course, semester)
        {
            total = 0;
            for (int i = 0; i < 5; i++)
            {
                this.marks[i] = marks[i];
                total += marks[i];
                if (marks[i] < 35)
                {
                    flagFail = 1;
                }
            }
            Calculate();
        }
        private void Calculate()
        {
            average = total / 5;
            if (flagFail == 1 || average < 40)
                grade = "Fail";
            else if (average >= 70)
                grade = "Distinction";
            else if (average >= 60)
                grade = "First Class";
            else if (average >= 50)
                grade = "Second Class";
            else
                grade = "Pass Class";
        }
        public override void Display()
        {
            base.Display();
            Console.WriteLine("\n-----MARKS DETAILS____\n");
            Console.Write("Marks in 5 subjects:");
            for (int i = 0; i < 5; i++)
                Console.Write(marks[i] + "  ");
            Console.WriteLine();
            Console.WriteLine("Total     :" + total);
            Console.WriteLine("Average     :" + average);
            Console.WriteLine("Grade     :" + grade);
        }

    }
    class MulitiLevel
    {
    public static void Main(string[] args)
    {
        MarksDetails Student1 = new MarksDetails("Abhijith", 22, "male",20190001, "MCA", 5, new int[] { 77, 80, 98, 95, 90 });
        Student1.Display();
    }
}
}
<br>
**  output**



![image](https://user-images.githubusercontent.com/98379636/152481048-5eb4df7d-1223-475a-8e64-111b6deb2496.png)



**implement principles of Delegates**
using System;
namespace Exercises
{
    class Delegates
    {
        delegate string UppercaseDelegate(string input);
        static string UppercaseFirst(string input)
        {
            char[] buffer = input.ToCharArray();
            buffer[0] = char.ToUpper(buffer[0]);
            return new string(buffer);
        }
        static string UppercaseLast(string input)
        {
            char[] buffer = input.ToCharArray();
            buffer[buffer.Length-1]= char.ToUpper(buffer[buffer.Length-1]);
            return new string(buffer);
        }
        static string UppercaseAll(string input)
        {
            return input.ToUpper();
        }
        static void WriteOutput(string input,UppercaseDelegate del)
        {
            Console.WriteLine("Input String:{0}", input);
            Console.WriteLine("Output String:{0}", del(input));
        }
        static void Main()
        {
            WriteOutput("tom", new UppercaseDelegate(UppercaseFirst));
            WriteOutput("tom", new UppercaseDelegate(UppercaseLast));
            WriteOutput("tom", new UppercaseDelegate(UppercaseAll));
        }
    }
}
<br>
**output**


![image](https://user-images.githubusercontent.com/98379636/152483992-50b4a41d-42f0-46b4-bcb7-5880bc62cc82.png)

**staic constructor**
using System;

namespace exercises
{
    class RegisterNum
    {
        int regNo;
        static int startNum;
        static RegisterNum()
        {
            startNum = 20210000;
        }
        RegisterNum()
        {
            regNo = ++startNum;
        }
        public static void Main(string[] args)
        {
            for(int i=0;i<100;i++)
            {
                RegisterNum Student = new RegisterNum();
                Console.WriteLine("Student{0}:{1}", i+1, Student.regNo);
            }
        }

    }
}
<br>
  
**output** 

![image](https://user-images.githubusercontent.com/98379636/152486291-ffa03e60-af10-458c-92b7-1f0017fcb07a.png)

![image](https://user-images.githubusercontent.com/98379636/152486702-e0307771-2345-440f-a2bf-d81a849666db.png)

![image](https://user-images.githubusercontent.com/98379636/152486781-8be62ead-9afc-4b89-8d57-bf5fe3a2eae9.png)

![image](https://user-images.githubusercontent.com/98379636/152486878-6a6da3bc-f1c5-465d-b5e4-ec43c45fbe3d.png)



**frequency of word**
using System;

namespace exercises
{
    class FrequencyIS
    {
        static void Main(string[] args)
        {
            int count = 0;
            string inputString;
            Console.WriteLine("\n    Frequency of word 'is'      ");
            Console.Write("\nenter the input string:");
            inputString = Console.ReadLine();
            char[] seperator = {',',' ','.','!','\n' };
            string testString = inputString.ToLower();
            String[] outcomes = testString.Split(seperator);
            foreach(String s in outcomes)
            {
                Console.WriteLine(s);
                if (s == "is")
                    count++;
            }
            Console.WriteLine("\nNumber of 'is'in" + inputString + "is:" + count);

        }
    }
}
<br>
**output**


![image](https://user-images.githubusercontent.com/98379636/152489925-26288167-4084-4819-87b8-33a2f0659163.png)


   *sumofvaluesondiagonalmatrix***
   using System;
namespace Excercises
{
    class SumOfDiagonals
    {
        static void Main(String[] args)
        {
            int MaxRow, Maxcol, sum = 0;
            int[,] Matrix;
            Console.WriteLine("\n_____SUM OF DIAGONAL OF MATRIX_______\n");
            Console.WriteLine("\nenter the number of rows:");
            MaxRow = Convert.ToInt32(Console.ReadLine());
            Console.Write("\nenter the number of coloumns:");
            Maxcol = Convert.ToInt32(Console.ReadLine());
            if(MaxRow!=Maxcol)
            {
                Console.WriteLine("\nthe dimensions entered are not of squarematrix");
                Console.WriteLine("\nexiting the program");
                return;
            }
            Matrix = new int[MaxRow, Maxcol];
            for(int i=0;i<MaxRow;i++)
            {
                for(int j=0;j<MaxRow;j++)
                {
                    Console.Write("\nenter the({0},{1})th element of the matrix:",(i + 1),(j + 1));
                     Matrix[i, j] = Convert.ToInt32(Console.ReadLine());
                }
            }
            Console.WriteLine("\nthe entered matrix is");
            for(int i=0;i<MaxRow;i++)
            {
                for(int j=0;j<Maxcol;j++)
                {
                   Console.Write(" "+ Matrix[i,j]);
        

                    if(i==j)
                    {
                        sum += Matrix[i,j];
                    }
                }
                Console.WriteLine();

            }
            Console.WriteLine("\nthe sum of diagonal is"  +sum);

        }
    }
}
<br>
**output**


![image](https://user-images.githubusercontent.com/98379636/154421283-aae70eb0-d342-4a9d-bbe2-2365c083533a.png)

![image](https://user-images.githubusercontent.com/98379636/154421781-fbe390bf-f2fd-43db-af2f-89dcf87a434b.png)

**check the existence of the file**
using System;
namespace Excercises
{
    class FileRead
    {
        public static void Main()
        {
            string filename;
            while (true) 
            {
                Console.WriteLine("\n_____menu__\n");
                Console.WriteLine("\n1.create a file");
                Console.WriteLine("\n2.existence of the file");
                Console.WriteLine("\n3.Read the contents of the file");
                Console.WriteLine("\n4.exit");
                Console.Write("\nenter your choice:");
                int ch = int.Parse(Console.ReadLine());
                switch(ch)
                {
                    case  1: Console.Write("enter the filename to create:");
                filename = Console.ReadLine();
                Console.WriteLine("\nwrite the contents of the file");
                string r = Console.ReadLine();
                        using (StreamWriter filestr = File.CreateText(filename))
                        {
                            filestr.WriteLine(r);
                        }
                    Console.WriteLine("file is created");
                            break;
                    case 2: Console.Write("\nenter the filename");
                    filename = Console.ReadLine();
                    if(File.Exists(filename))
                    {
                        Console.WriteLine("file exists");
                    }
                    else
                    {
                        Console.WriteLine("file does not exist in the current directory");
                    }
                    break;
                    case 3:Console.Write("enter the filename to read the contents:\n");
                    filename = Console.ReadLine();
                    if(File.Exists(filename))
                    {
                        using(StreamReader sr=File.OpenText(filename))
                        {
                            string s = "  ";
                            Console.WriteLine("here is the content of the file:");
                            while((s=sr.ReadLine())!=null)
                            {
                                Console.WriteLine(s);
                            }
                            Console.WriteLine("  ");
                        }
    {
                        Console.WriteLine("file does not exists");
                    }
                    break;
                    case 4:Console.WriteLine("\n exiting...");
                    return;
                    default:Console.WriteLine("\ninvalid choice");
                    break;

                    
                }
                }
            }

        }
    }
    <br>

**output**


![image](https://user-images.githubusercontent.com/98379636/154620994-bb709605-f476-402e-be65-e898f7bd4007.png)

![image](https://user-images.githubusercontent.com/98379636/154622965-74eee68a-103f-49cb-b786-e6e0cc9a7a8d.png)

![image](https://user-images.githubusercontent.com/98379636/154623056-8eb5e175-381e-465d-bf85-8df4f2b59e23.png)

**program to perform file comparision**
using System;
using System.IO;
namespace Excercises
{
    class FileRead
    {
        public static void Main()
        {
            string file1;
            string file2;
            Console.Write("enter the first file path:");
            file1 = Console.ReadLine();
            Console.WriteLine("enter the second file path:");
            file2 = Console.ReadLine();
            if(!File.Exists(file1))
            {
                Console.WriteLine("first file does not exist!");
            }
            else if(!File.Exists(file2))
            {
                Console.WriteLine("second file does not exist!");
            }
            else if(File.ReadAllText(file1)==File.ReadAllText(file2))
            {
                Console.WriteLine("both file contatin the same contents:");
            }
            else
            {
                Console.WriteLine("contents of files are not same:");
            }
        }
    }
}
<br>
**output**


![image](https://user-images.githubusercontent.com/98379636/154625795-617c45bf-94b0-4912-b6f5-ce91defce0c0.png)

![image](https://user-images.githubusercontent.com/98379636/154626059-7fb2382a-29aa-4646-94a4-ac3c10aa47d5.png)


**impement icomparable interface**
using System;
namespace Excercises
{
    class Fraction:IComparable
    {
        int z, n;
        public Fraction(int z,int n)
        {
            this.z = z;
            this.n = n;
        }
        public static Fraction operator +(Fraction a,Fraction b)
        {
            return new Fraction(a.z * b.n + a.n * b.z, a.n * b.n);

        }
        public static Fraction operator *(Fraction a,Fraction b)
        {
            return new Fraction(a.z * b.z, a.n * b.n);
        }
        public int CompareTo(object obj)
        {
            Fraction f = (Fraction)obj;
            if ((float)z /n <(float)f.z / f.n)
                return -1;
            else if ((float)z / n > (float)f.z / f.n)
                return 1;
            else
                return 0;
        }
        public override string ToString()
      
            {
                return z + "/" + n;


            }
        }
        class ICompInterface
        {
            public static void Main()
            {
                Fraction[] a = {
                               new Fraction(5,2),
                              new Fraction(29, 6),
                               new Fraction(4, 5),
                               new Fraction(10, 8),
                               new Fraction(34, 7)
                           };
        Array.Sort(a);
            
                Console.WriteLine("implementing the IComparableInterface in"+"Displaying Fractions:");
                foreach(Fraction f in a)
            {
                Console.WriteLine(f + "  ");
            }
            Console.WriteLine();
              Console.ReadLine();
            }
        }
    }

    
<br>
**output**


![image](https://user-images.githubusercontent.com/98379636/154630890-2ec8cd8c-0b03-4231-b4e1-b0aa0cf673f0.png)

**threadpools**
using System;
using System.Threading;
namespace Excercises
{
    class Threadpoolprog
    {
        public void ThreadFun1(object obj)
        {
            int loop;
            for(loop=0;loop<=4;loop++)
            {
                Console.WriteLine("thread1 is executing:");
            }
        }
        public void ThreadFun2(object obj)
        {
            int loop = 0;
            for(loop=0;loop<=4;loop++)
            {
                Console.WriteLine("thread2 is executing:");
            }
        }
        public static void Main()
        {
            Threadpoolprog TP = new Threadpoolprog();
            for(int i=0;i<2;i++)
            {
                ThreadPool.QueueUserWorkItem(new WaitCallback(TP.ThreadFun1));
                ThreadPool.QueueUserWorkItem(new WaitCallback(TP.ThreadFun2));
            }
            Console.ReadKey();
        }
    }
}
<br>
**output**

![image](https://user-images.githubusercontent.com/98379636/154633466-a0bd6bf1-fee6-4e8f-a28f-4bcdff0a1540.png)


**demonstrate exceptionhandling**
using System;

namespace Excercises
{
    class ExceptionHandling
    {
        static void Main(string[] args)
        {
            Age a = new Age();
            try
            {
                a.displayAge();
            }
            catch (AgeIsNegativeException e)
            {
                Console.WriteLine("AgeIsNegativeException:{0}",e.Message);
            }
            finally
            {
                Console.WriteLine("execution of finally block is done");
            }
        }
    }
}
public class AgeIsNegativeException:Exception
{
    public AgeIsNegativeException(string message):base(message)
    {

    }
}
public class Age
{
    int age = -5;
    public void displayAge()
    {
        if(age<0)
        {
            throw (new AgeIsNegativeException("Age cannot be negative"));
        }
        else
        {
            Console.WriteLine("Age is:{0}", age);
        }
    }
}
<br>
**output**


![image](https://user-images.githubusercontent.com/98379636/155660271-4cd82008-d46f-4e33-960f-1e274b31be8c.png)

**fibonacci number**
using System;
public class FibonacciExample
{
    public static void Main(string[] args)
    {
        int n1 = 0,n2 = 1,n3,i,number;
        Console.WriteLine("enter the number of elements:");
        number = int.Parse(Console.ReadLine());
        Console.Write(n1 + " " + n2 + " ");
        for(i=2;i<number;i++)
        {
            n3 = n1 + n2;
            Console.Write(n3 + " ");
            n1 = n2;
            n2 = n3;
        }
    }
}
<br>
**output**


![image](https://user-images.githubusercontent.com/98379636/155662294-d0050b36-53ad-4bec-8aa5-aec903bffa64.png)
<br>

**to check prime number**
using System;
public class primeNumberExample
{
    public static void Main(String[] args)
    {
        int n, i, m = 0, flag = 0;
        Console.Write("enter the number to check prime:");
        n = int.Parse(Console.ReadLine());
        m = n / 2;
        for(i=2;i<=m;i++)
        {
            if(n%i==0)
            {
                Console.Write("number is not prime");
                flag = 1;
                break;
            }
        }
        if (flag == 0)
            Console.Write("number is prime");
    }
}
<br>
**output**

![image](https://user-images.githubusercontent.com/98379636/155663839-d5f33df1-8e2c-4e3e-bd09-c027d74f594b.png)

![image](https://user-images.githubusercontent.com/98379636/155663866-686db3b2-6c63-41a2-ba6a-8491b5d29c4b.png)

<br>
**check pallindrome or not**
using System;using System;<br>
public class pallindromeExample<br>
{<br>
    public static void Main(String[] args)<br>
    {<br>
        int n, r, sum = 0, temp;<br>
        Console.Write("enter the number:");<br>
        n = int.Parse(Console.ReadLine());<br>
        temp = n;<br>
        while(n>0)<br>
        {<br>
            r = n % 10;<br>
            sum = (sum * 10) + r;<br>
            n = n / 10;<br>
        }<br>
        if (temp == sum)<br>
            Console.Write("number is pallindrome");<br>
        else<br>
            Console.Write("number is not pallindrome");<br>
    }<br>
}<br>

**output**


![image](https://user-images.githubusercontent.com/98379636/155665421-0ff97220-a1cb-4d67-8d5f-53df4ac6f318.png)

![image](https://user-images.githubusercontent.com/98379636/155665472-96e3aaf8-0909-456b-a473-b7994ddab5a3.png)


  **factorial of a number**
  using System;
public class FactorialExample
{
    public static void Main(String[] args)
    {
        int i, fact = 1, number;
        Console.Write("enter anu number:");
        number = int.Parse(Console.ReadLine());
        for(i=1;i<=number;i++)
        {
            fact = fact * i;
        }
        Console.Write("factorial of" +number+ "is:"+fact);
    }
}
<br>
**output**


![image](https://user-images.githubusercontent.com/98379636/155667177-5ed9d53b-772f-4b5f-8257-7bb1c66b07e8.png)

**check armstrong number**
using System;
public class ArmstrongExample
{
    public static void Main(String[] args)
    {
        int n, r, sum = 0, temp;
        Console.Write("enter the number=");
        n = int.Parse(Console.ReadLine());
        temp = n;
        while(n>0)
        {
            r = n % 10;
            sum = sum+(r*r*r);
            n = n / 10;

        }
        if (temp == sum)
            Console.Write("Armstrong number");
        else
            Console.Write("not armstrong number:");
    }
}<br>
**output**


![image](https://user-images.githubusercontent.com/98379636/155668415-aae4ef39-a111-4d2a-b7c6-dfe800c569a0.png)

![image](https://user-images.githubusercontent.com/98379636/155668442-990b5348-6f3e-4285-a5d1-3abe944bd0b6.png)


  **sum of digits**
  using System;
public class SumExample
{
    public static void Main(String[] args)
    {
        int n, sum = 0, m;
        Console.Write("enter a number:");
        n = int.Parse(Console.ReadLine());
        while(n>0)
        {
            m = n % 10;
            sum = sum + m;
            n = n / 10;
        }
        Console.Write("sum is=" + sum);
    }
}
<br>
**output**

![image](https://user-images.githubusercontent.com/98379636/155669511-9cbf6e4c-6630-426c-9ab5-fab2b5103100.png)


**reverse of a number**
using System;
public class ReverseExample
{
    public static void Main(String[] args)
    {
        int n, reverse = 0, rem;
        Console.Write("enter a number:");
        n = int.Parse(Console.ReadLine());
        while(n!=0)
        {
            rem = n % 10;
            reverse = reverse * 10 + rem;
            n /= 10;
        }
        Console.Write("reversed number:" + reverse);
    }
}
<br>
**output**


![image](https://user-images.githubusercontent.com/98379636/155670861-035ebbdc-ac36-483d-9c3f-6311ef9d1098.png)


**binary triangle**
using System;

namespace Excercises
{
    class BinaryTriangle
    {
        static void Main(String[] args)
        {
            int number, digit = 1;
            Console.WriteLine("\nenter the number of lines");
            number = Convert.ToInt32(Console.ReadLine());
            for(int i=1;i<=number;i++)
            {
                for(int space=number-i;space>0;space--)
                {
                    Console.Write("  ");
                }
                for(int j=0;j<i;j++)
                {
                    Console.Write(digit + " ");
                    digit = (digit == 1) ? 0 : 1;
                }
                Console.Write("\n");
            }
        }
    }
}
<br>
**output**


![image](https://user-images.githubusercontent.com/98379636/156502265-7466f55f-d047-450d-88fa-db6f8c27e410.png)

**create a Graycode**
using System;
namespace Excercises
{
    class Graycode
    {
        static int getGray(int n)
        {
            return n ^ (n >> 1);
        }
        static void Main(String[] args)
        {
            int InputNum, GrayNum;
            Console.Write("\nenter the decimal number:");
            InputNum = Convert.ToInt32(Console.ReadLine());
            Console.WriteLine("\nbinary equvailent of {0}:{1}", InputNum, Convert.ToString(InputNum, 2));
            GrayNum = getGray(InputNum);
            Console.WriteLine("\n Gray code equivalent of {0}:{1}", InputNum, Convert.ToString(GrayNum, 2));
        }
    }
}
<br>

**ouput**


![image](https://user-images.githubusercontent.com/98379636/156503859-9f569d6b-ed9a-4f42-9dd5-4a9ac569b4a4.png)


**program that benchmarks 2D,jagged array allocation**
using System;
using System.Diagnostics;
namespace Exrecises
{
    class BenchmarkAllocation
    {
        const int _max = 100000;
        static void Main(string[] args)
        {
            var Arr2D = new int[100, 100];
            var ArrJagged = new int[100][];
            for (int i = 0; i < 100; i++)
            {
                ArrJagged[i] = new int[100];
            }
            var Stopwatch2D = Stopwatch.StartNew();
            for (int i = 0; i < _max; i++)
            {
                for (int j = 0; j < 100; j++)
                {
                    for (int k = 0; k < 100; k++)
                    {
                        Arr2D[j, k] = k;
                    }
                }
            }
            Stopwatch2D.Stop();
            var StopwatchJagged = Stopwatch.StartNew();
            for (int i = 0; i < _max; i++)
            {
                for (int j = 0; j < 100; j++)
                {
                    for (int k = 0; k < 100; k++)
                    {
                        ArrJagged[j][k] = k;
                    }
                }
            }
            StopwatchJagged.Stop();
            Console.Write("\n Time taken for allocation in case of 2D array:");
            Console.WriteLine(Stopwatch2D.Elapsed.TotalMilliseconds + "millisecods");
            Console.Write("\n Time taken for allocation in case of Jagged array:");
            Console.WriteLine(StopwatchJagged.Elapsed.TotalMilliseconds + "milliseconds");
        }
    }
}
<br>

**output**


![image](https://user-images.githubusercontent.com/98379636/156510180-170a8728-67fb-4d7c-9069-1082bd310696.png)


**perform reversal padding and trimming operations**
using System;
using System.Collections.Generic;
using System.ComponentModel;
using System.Data;
using System.Drawing;
using System.Linq;
using System.Text;
using System.Threading.Tasks;
using System.Windows.Forms;

namespace WindowsFormsApp13
{
    public partial class Form1 : Form
    {
        public Form1()
        {
            InitializeComponent();
        }

        private void button1_Click(object sender, EventArgs e)
        {
            string inputstring, revstr = " ";
            int Length;
            inputstring = txtInput.Text;
            Length = inputstring.Length - 1;
            while(Length>=0)
            {
                revstr = revstr + inputstring[Length];
                Length--;
            }
            MessageBox.Show("reverse string is:" + revstr, "Result");
        }

        private void button2_Click(object sender, EventArgs e)
        {
            string inputstring;
            inputstring = txtInput.Text;
            MessageBox.Show("the string after Trimming:" + inputstring.Trim(), "Result");
        }

        private void button3_Click(object sender, EventArgs e)
        {
            string inputstring;
            inputstring = txtInput.Text;
            inputstring = inputstring.PadLeft(10, '*');
            inputstring = inputstring.PadRight(15, '*');
            MessageBox.Show("string after padding:" + inputstring, "Result");
        }
    }
}
<br>
**output**
![image](https://user-images.githubusercontent.com/98379636/158942819-ff27c963-2959-4df3-83ff-664f26bba98d.png)
![image](https://user-images.githubusercontent.com/98379636/158942905-99abb3a9-e346-4fb4-9293-8def417124de.png)

**program to create progressbar control**
using System;
using System.Collections.Generic;
using System.ComponentModel;
using System.Data;
using System.Drawing;
using System.Linq;
using System.Text;
using System.Threading;
using System.Windows.Forms;

namespace WindowsFormsApp14
{
    public partial class Form1 : Form
    {
        public Form1()
        {
            InitializeComponent();
        }

        private void Form1_Load(object sender, EventArgs e)
        {
            backgroundWorker1.WorkerReportsProgress = true;
            backgroundWorker1.RunWorkerAsync();

        }

        private void backgroundWorker1_DoWork(object sender, DoWorkEventArgs e)
        {
            for(int i=1;i<=100;i++)
            {
                Thread.Sleep(50);


                backgroundWorker1.ReportProgress(i);
            }

        }

        private void backgroundWorker1_ProgressChanged(object sender, ProgressChangedEventArgs e)
        {
            progressBar1.Value = e.ProgressPercentage;
            this.Text = "progress:" + e.ProgressPercentage.ToString() + "%";

        }
    }
}
<br>
**output**
![image](https://user-images.githubusercontent.com/98379636/158943370-a4b4a9a3-10f4-46a8-bff7-b1df3439f8de.png)


**develop appplication to create a flat clock**
using System;
using System.Collections.Generic;
using System.ComponentModel;
using System.Data;
using System.Drawing;
using System.Linq;
using System.Text;
using System.Threading.Tasks;
using System.Windows.Forms;

namespace WindowsFormsApp15
{
    public partial class Form1 : Form
    {
        public Form1()
        {
            InitializeComponent();
            timer1.Start();

        }

        private void Form1_Load(object sender, EventArgs e)
        {
            System.Timers.Timer timer = new System.Timers.Timer();
            timer.Interval = 1000;
            timer.Elapsed += Timer_Elapsed;
            timer.Start();


        }
        private void Timer_Elapsed(object sender, System.Timers.ElapsedEventArgs e)
        {
            circularProgressBar1.Invoke((MethodInvoker)delegate
            {
                circularProgressBar1.Text = DateTime.Now.ToString("hh:mm:ss");
                circularProgressBar1.SubscriptText = DateTime.Now.ToString("tt");

            });
    }
}

}
<br>
**output**
![image](https://user-images.githubusercontent.com/98379636/158943749-c0399b8e-a50c-4255-99b8-ab5c0bc6aeda.png)

**convert digit to words**
using System;
using System.Collections.Generic;
using System.ComponentModel;
using System.Data;
using System.Drawing;
using System.Linq;
using System.Text;
using System.Threading.Tasks;
using System.Windows.Forms;

namespace WindowsFormsApp4
{
    public partial class Form1 : Form
    {
        public Form1()
        {
            InitializeComponent();
        }

        private void button1_Click(object sender, EventArgs e)
        {
            label1.Text = NumtoWord(long.Parse(textBox1.Text));
            label1.Visible = true;
        }
        public string NumtoWord(long number)
        {
            string word = " ";
            if(number==0)
            {
                return "zero";
            }
            if(number<0)
            {
                return "Minus"+Math.Abs(number);
            }
            if(number/10000000>0)
            {
                word += NumtoWord(number / 100000) + "lacs";
                number %= 100000;
            }
            if(number/1000>0)
            {
                word += NumtoWord(number / 1000) + "thousand";
                number %= 1000;
            }
            if(number/100>0)
            {
                word += NumtoWord(number / 100) + "hundrend";
                number %= 100;
            }
            if (number > 0)
            {
                string[] units = new string[] { "zero", "one", "two", "three", "four", "five", "six", "seven", "eight", "nine","ten", "eleven", "twelve", "thirteen", "fourteen", "fifteen", "sixteen", "seventeen", "eighteen", "nineteen" };
                string[] Tens = new string[] { "zero", "TEN", "twenty", "thirty", "fourty", "fifty", "sixty", "seventy", "eighty", "ninty" };
                if(number<20)
                {
                    word += units[number];
                }
                else
                {
                    word += Tens[number / 10];
                    if(number%10>0)
                    {
                        word += units[number % 10];
                    }
                }
            }
            return word;
        }
    }
}
<br>
**output**
![image](https://user-images.githubusercontent.com/98379636/158945317-a60cbb17-409a-4800-9a4a-90cab31321d3.png)

**create a notepad**
using System.IO;<br>
using System.Windows.Forms;<br>
using System.Drawing;<br>
namespace notepad<br>
{<br>
    class NotepadForm : Form<br>
    {<br>
        private string fileName;<br>
        private RichTextBox txtContent;<br>
        private ToolBar toolBar1;<br>
        internal NotepadForm()<br>
        {<br>
            fileName = null;<br>
            initializeComponents();<br><br>
        <br>}
        void initializeComponents()<br>
        {<br>
            this.Text = "My notepad";<br>
        
            this.MaximizeBox = true;<br>
            toolBar1 = new ToolBar();<br>
            toolBar1.Font = new Font("Arial", 16);<br>
            toolBar1.Padding = new Padding(4);<br>
            toolBar1.ButtonClick += new ToolBarButtonClickEventHandler(toolBar1Clicked);<br>
            ToolBarButton toolBar1Button1 = new ToolBarButton();<br>
            ToolBarButton toolBar1Button2 = new ToolBarButton();<br>
            ToolBarButton toolBar1Button3 = new ToolBarButton();<br>
            toolBar1Button1.Text = "New";<br>
            toolBar1Button2.Text = "Open";<br>
            toolBar1Button3.Text = "Save";<br>
            toolBar1.Buttons.Add(toolBar1Button1);<br>
            toolBar1.Buttons.Add(toolBar1Button2);<br>
            toolBar1.Buttons.Add(toolBar1Button3);<br>
            txtContent = new RichTextBox();<br>
            txtContent.Size = this.ClientSize;<br>
            txtContent.Height = toolBar1.Height;<br>
            txtContent.Top = toolBar1.Height;<br>
            txtContent.Anchor = AnchorStyles.Left | AnchorStyles.Right | AnchorStyles.Top | AnchorStyles.Bottom;<br>
            txtContent.Font = new Font("Arial", 16);<br>
            txtContent.AcceptsTab = true;<br>
            txtContent.Padding = new Padding(8);<br>
            this.Controls.Add(toolBar1);<br>
            this.Controls.Add(txtContent);<br>
        }<br>
        private void toolBar1Clicked(object sender, ToolBarButtonClickEventArgs e)<br>
        {
            saveFile();<br>
            switch (toolBar1.Buttons.IndexOf(e.Button))<br>
            {<br>
                case 0:<br>
                    this.Text += "My notepad";<br>
                    txtContent.Text = string.Empty;<br>
                    fileName = null;<br>
                    break;<br>
                case 1:<br>
                    OpenFileDialog openDlg = new OpenFileDialog();<br>
                    if (DialogResult.OK == openDlg.ShowDialog())<br>
                    {<br>
                        fileName = openDlg.FileName;<br>
                        txtContent.LoadFile(fileName);<br>
                        this.Text = "My notepad" + fileName;<br>
                    }<br>
                    break;<br>
            }<br>
        }<br>
        void saveFile()<br>
        {<br>
            if (fileName == null)<br>
            {<br>
                SaveFileDialog saveDlg = new SaveFileDialog();<br>
                if (DialogResult.OK == saveDlg.ShowDialog())<br>
                {<br>
                    fileName = saveDlg.FileName;<br>
                    this.Text += " " + fileName;<br>
                }<br>
            }<br>
            else<br>
            {<br>
                txtContent.SaveFile(fileName, RichTextBoxStreamType.RichText);<br>
            
            
            }<br>
        }<br><br>
        private void NotepadClosing(object sender, FormClosingEventArgs e)<br>
        {<br>
            saveFile();<br>
        }<br><br>
        static void Main(string[] args)<br>
        {<br>
            Application.Run(new NotepadForm());<br><br>
        }<br>
    }<br>
}<br>

**output**
![image](https://user-images.githubusercontent.com/98379636/165692087-879c7e96-0fd7-46c9-8d63-5511a44c84ee.png)


**develop an applicatio to construct a graphical binary tree where you need to create add search and remove nodes**
using System;<br>
using System.Collections.Generic;<br>
using System.ComponentModel;<br>
using System.Data;<br>
using System.Drawing;<br>
using System.Linq;<br>
using System.Text;<br>
using System.Threading.Tasks;<br>
<br>
using System.Windows.Forms;<br>
using System.Drawing.Drawing2D;<br>

namespace reversepaddingtrimming<br>
{<br>
    public partial class Form1 : Form<br>
    {<br>
        private Node root;<br>
        public Form1()<br>
        {<br>
            InitializeComponent();<br>
            this.root = null;<br>
            test();<br>
        }<br>
        void test()<br>
        {<br>
            textBox1.Text = "5";<br>
            btnAdd_Click(btnAdd, null);<br>
            textBox1.Text = "3";<br>
            btnAdd_Click(btnAdd, null);<br>
            textBox1.Text = "2";<br>
            btnAdd_Click(btnAdd, null);<br>
            textBox1.Text = "1";<br>
            btnAdd_Click(btnAdd, null);<br>
            textBox1.Text = "4";<br>
            btnAdd_Click(btnAdd, null);<br>
            textBox1.Text = "7";<br>
            btnAdd_Click(btnAdd, null);<br>
            textBox1.Text = "6";<br>
            btnAdd_Click(btnAdd, null);<br>
            textBox1.Text = "8";<br>
            btnAdd_Click(btnAdd, null);<br>
        }<br>
        private void btnAdd_Click(object sender, EventArgs e)<br>
        {<br>
            int value = int.Parse(textBox1.Text);<br>
            if (root == null)<br>
                root = new Node(value);<br>
            else<br>
            {<br>
                if (root.Add(value) == false)<br>
                    MessageBox.Show("The value already exists!");<br>
            }<br>
            drawTree();<br>


        }<br>

        private void button3_Click(object sender, EventArgs e)<br>
        {<br>
            root = null;<br>
            pictureBox1.Image = null;<br>
        
    }<br>
    
    

        private void button2_Click(object sender, EventArgs e)<br>
        {<br>
            int value = int.Parse(textBox1.Text);<br>
            if (root != null)<br>
            {<br>
                bool status = root.Remove(value, root, ref root);<br>
                if (status == false)<br>
                {<br>
                    MessageBox.Show("the value does not exists");<br>
                }<br>
                
                
            }<br>
            drawTree();<br>      
    }<br>

        private void button4_Click(object sender, EventArgs e)<br>
        {<br>
            string msg;<br>
            int value = int.Parse(textBox1.Text);<br>
            if (root == null)<br>
            {<br>
                msg = "Tree is empty";<br>
            }<br>
            else<br>
            {<br>
                if (root.Exists(value))<br>
                {<br>
                    msg = "Value found";<br>
                }<br>
                else<br>
                {<br>
                    msg = "Value not found";<br>
                }<br>
            }<br>
            MessageBox.Show(msg);<br>
        }<br>
        void drawTree()<br>
        {<br>
            if (root != null)<br>
                pictureBox1.Image = root.Draw();<br>
            else<br>
                pictureBox1.Image = null;<br>
            this.Update();<br>
        }<br>
    }<br>
}<br>
class Node<br>
{<br>
    internal Node left { get; set; }<br>
    internal Node right { get; set; }<br>
    internal int value;<br>
    internal int center = 12;<br>
    private static Bitmap nodeBg = new Bitmap(30, 25);<br>
    private static Font font = new Font("Arial", 14);<br>
    internal Node(int value)<br>
    {<br>
        this.value = value;<br>
    }<br>
    internal bool Add(int value)<br>
    {<br>
        Node node = new Node(value);<br>
        if (value < this.value)<br>
        {<br>
            if (this.left == null)<br>
            {<br>
                this.left = node;<br>
                return true;<br>
            }<br>
            else<br>
                return this.left.Add(value);<br>
        }<br>
        else if (value > this.value)<br>
        {<br>
            if (this.right == null)<br>
            {<br>
                this.right = node;<br>
                return true;<br>
            }<br>
            else<br>
                return this.right.Add(value);<br>
        }<br>
        return false;<br>
    }<br>
    internal bool Remove(int value, Node parent, ref Node root)<br>
    {<br>
        if (value < this.value)<br>
        
        {<br>
            if (left != null)<br>
            {<br>
                return left.Remove(value, this, ref root);<br>
            }<br>
        }<br>
        else if (value > this.value)<br>
        {<br>
            if (right != null)<br>
            {<br>
            {<br>
                return right.Remove(value, this, ref root);<br>
             
            }<br>
        }<br>
        else if (value == this.value)<br>
        {<br>
            bool isLeft = (this == parent.left);<br>
            if (left == null && right == null)<br>

            {<br>
                if (root == this)<br>
                    root = null;<br>
                else<br>
                if (isLeft) parent.left = null; else parent.right = null;<br>
            }<br>
            else if (right == null)<br>
            {<br>
                if (isLeft) parent.left = left; else parent.right = left;<br>
                if (root == this)<br>
                    root = left;<br>
            }<br>
            else<br>
            {<br>
                if (right.left == null)<br>
                {<br>
                    right.left = left;<br>
                    if (isLeft) parent.left = right;<br>
                    else<br>
                        parent.right = right;<br>
                    if (root == this)<br>
                        root = right;<br>
                }<br>
                else<br>
                {<br>
                    Node node = right;<br>
                    while (node.left.left != null)<br>
                        node = node.left;<br>
                    Console.WriteLine("Node: " + node.value);<br>
                    this.value = node.left.value;<br>
                    Console.WriteLine("here");<br>
                    node.left = null;<br>
                }<br>
            }<br>
            return true;<br>
        }<br>
        return false;<br>
    }<br>
    public Image Draw()<br>
    {<br>
        Size lSize = new Size(nodeBg.Width / 2, 0);<br>
        Size rSize = new Size(nodeBg.Width / 2, 0);<br>
        Image lNodeImg = null;<br>
        Image rNodeImg = null;<br>
        int lCenter = 0, rCenter = 0;<br>

        if (this.left != null)<br>
            {
            lNodeImg = left.Draw();<br>
            lSize = lNodeImg.Size;<br>
            this.center = lSize.Width;<br>
            lCenter = left.center;<br>
        }<br>
            if (this.right != null)<br>
            {<br>
            rNodeImg = right.Draw();<br>
            rSize = rNodeImg.Size;<br>
            rCenter = right.center;<br>
        }<br>
        int maxHeight = (lSize.Height < rSize.Height) ? rSize.Height : lSize.Height;<br>
            if (maxHeight > 0) maxHeight += 35;<br>
        Size resultSize = new Size(lSize.Width + rSize.Width, nodeBg.Size.Height +
maxHeight);<br>
        Bitmap result = new Bitmap(resultSize.Width, resultSize.Height);<br>

        Graphics g = Graphics.FromImage(result);<br>
        g.SmoothingMode = SmoothingMode.HighQuality;<br>
        g.FillRectangle(Brushes.White, new Rectangle(new Point(0, 0), resultSize));<br>
        g.DrawImage(nodeBg, lSize.Width - nodeBg.Width / 2, 0);<br>
        string str = "" + value;<br>
        g.DrawString(str, font, Brushes.Black, lSize.Width - nodeBg.Width / 2 + 7,
       nodeBg.Height / 2f - 12);<br>
        Pen pen = new Pen(Brushes.Black, 1.2f);<br>
        float x1 = center;<br>
        float y1 = nodeBg.Height;<br>
        float y2 = nodeBg.Height + 35;<br>
        float x2 = lCenter;<br>
        var h = Math.Abs(y2 - y1);<br>
        var w = Math.Abs(x2 - x1);<br>
            if (lNodeImg != null)<br>
            {<br>
            g.DrawImage(lNodeImg, 0, nodeBg.Size.Height + 35);<br>
            var points1 = new List<PointF><br>
{<br>
                new PointF(x1, y1), new PointF(x1 - w / 6, y1 + h / 3.5f), new PointF(x2 + w / 6, y2 - h / 3.5f), new PointF(x2, y2), };
            g.DrawCurve(pen, points1.ToArray(), 0.5f);<br>
        }<br>
        if (rNodeImg != null)<br>
        {<br><br>
            g.DrawImage(rNodeImg, lSize.Width, nodeBg.Size.Height + 35);<br>
            x2 = rCenter + lSize.Width;<br>
            w = Math.Abs(x2 - x1);<br>
            var points = new List<PointF><br>
{<br><br>
new P<br><br>ointF(x1, y1), new PointF(x1 + w/6, y1 + h/3.5f), new PointF(x2 - w/6, y2 - h/3.5f), new PointF(x2, y2) };
            g.DrawCurve(pen, points.ToArray(), 0.5f);<br>
        }<br><br>
        return result;<br>
    }<br>
    public bool Exists(int value)<br>
    {<br>
        bool res = value == this.value;<br>
        if (!res && left != null)<br>
            res = left.Exists(value);<br>
        if (!res && right != null)<br>
            res = right.Exists(value);<br>
        return res;<br>
    }<br>
}<br>
    
    **output**
    ![image](https://user-images.githubusercontent.com/98379636/165696151-195fab88-e7fa-4d21-8a7a-8e0eabcd8773.png)
![image](https://user-images.githubusercontent.com/98379636/165696312-9b8e5641-3ae9-41fe-bbbc-3f5084cb8cae.png)
![image](https://user-images.githubusercontent.com/98379636/165696435-5173b95d-e115-4a08-a4d9-3e67558664b7.png)
![image](https://user-images.githubusercontent.com/98379636/165696559-4de52046-5920-4fff-ae69-8c06808e8689.png)
















    
    






