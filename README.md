
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


