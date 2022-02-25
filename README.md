    q
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
**BINARY TRIANGLE**
using System;<br>
namespace Excercises<br>
{<br><br>
    class BinaryTriangle<br>
        {<br>
 
           static void Main(String[] args)<br>
        { <br>
            
          int number,digit = 1;<br>
            Console.Write("\nEnter the number of lines:");<br>
        number = Convert.ToInt32(Console.ReadLine());<br>
        for (int i = 1; i <= number;i++)<br>

            {<br>
                for (int space = number-i; space > 0; space--)<br>
                {<br>
                    Console.Write("  ");<br><br>
                }<br>


                for (int j = 0; j < i; j++)<br>
                {<br>
                    Console.Write(digit + "  ");<br>
                    digit=(digit== 1) ? 0 : 1;<br>

                }<br>
              Console.Write("\n");<br>
    }<br>
}<br>
}<br>
}<br>
    
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
  
**output**  ![image](https://user-images.githubusercontent.com/98379636/152486291-ffa03e60-af10-458c-92b7-1f0017fcb07a.png)
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


   


    
    






