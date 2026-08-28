Program
```
using System.ComponentModel.DataAnnotations;
using System.Security.Cryptography;

namespace ConsoleApp1
{
    public class point
    {
        public int x {  get; set; }
        public int y { get; set; }
        public int z { get; set; }

        public point():this(0,0,0)
        { }
        public point (int x,int y): this(x,y,0)
        {
        }
        public point(int x, int y, int z)
        {
            this.x = x;
            this.y = y;
            this.z = z;
        }
        public void Display()
        {
            Console.WriteLine($" points : {x}, {y}, {z}");
        }

        public void CalculateDistance( point p1,  point p2)
        {
            int distance= p1.x - p2.x;
            if (distance < 0) distance *= -1;
            Console.WriteLine($"distance={distance}");
        }
        public static bool operator == (point p1,point p2)
        {
            return (p1.x == p2.x) && (p1.y == p2.y) && (p1.z == p2.z);
        }
        public static bool operator !=(point p1, point p2)
        {
            return (p1.x == p2.x) && (p1.y == p2.y) && (p1.z == p2.z);
        }

        public override string ToString()
        {
            return $" points : {x}, {y}, {z}";
        }
        public override bool Equals(object? obj)
        {
            if(obj is point p)
            {
                return x==p.x && y==p.y && z==p.z;
            }
            else
            {
                return false;
            }
        }
        public static void display(point[] arr)
        {
            if(arr == null || arr.Length == 0)
            {
                Console.WriteLine("Array is empty");
                return;
            }
            else
            {
                foreach(point p in arr) { Console.WriteLine(p); }
            }
        }
    }

    public class Fraction
    {
        public double a {  get; set; }
        public double b { get; set; }

        public Fraction(double A,double B)
        {
            a= A; b= B;
        }
        public void DDisplay()
        {
            Console.WriteLine($"Fraction1={a},Fraction2={b}");
        }
        public void ADD(Fraction f1, Fraction f2)
        {
            double add1 = f1.a+f1.b;
            double add2 = f2.a+f2.b;
            Console.WriteLine(add1); Console.WriteLine(add2);

        }
        public static Fraction operator +(Fraction f1, Fraction f2) { 
               Fraction res=new Fraction(0,0);
               res.a= f1.a+f2.a;
               res.b= f1.b+f2.b;
            return res;
        }

        public static implicit operator Fraction(int n)
        {
            return new Fraction(n,0);
        }
        public static explicit operator int(Fraction f) { 
               return (int)f.a;
        }
    }
    internal class Program
    {
        static void Main(string[] args)
        {
            point p1=new point(1,2,3);
            point p2= new point() {x=5,y=15,z=25};

            point p3 = new point(4, 5, 6);
            point p4 = new point(4,5,6);

            bool eq=point.Equals(p3,p4);
            Console.WriteLine(eq);
            bool eq2=p1==p2;
            Console.WriteLine(eq2);
            /**Fraction f1= new Fraction(1.5,2.5);
            Fraction f2 = new Fraction(3.5, 4.5);
            f1.DDisplay();
            f2.DDisplay();
            f1.ADD(f1, f2); **/
            Person[] people = new Person[] {
                new Employee
                {
                    Name="hadia",NID=5,age=50,Address=new Address{city="Egypt",street="Tahrir",ZIPcode=20},
                    salary=1500
                    
                },
                 new Trainee
                {
                    Name="hadia",NID=5,age=50,Address=new Address{city="Egypt",street="Tahrir",ZIPcode=20},
                    
                }

            };
            }
        }
    }

```
Employee
```
using System;
using System.Collections.Generic;
using System.Linq;
using System.Text;
using System.Threading.Tasks;

namespace ConsoleApp1
{
    internal class Employee:Person
    {
        
        public int NID { get; set; }
        public int salary { get; set; }

        public Employee () { }

        public override string ToString()
        {
            return $"NID:{NID},Salary:{salary} ";
        }
        public override Person Clone()
        {
            Employee coped=(Employee)this.MemberwiseClone();
            return coped ;
        }
    }
}
```
Address
```
using System;
using System.Collections.Generic;
using System.Linq;
using System.Text;
using System.Threading.Tasks;

namespace ConsoleApp1
{
    internal class Address
    {
        public string city {  get; set; }
        public string street { get; set; }
        public int ZIPcode { get; set; }

        public Address() { }

        public override string ToString()
        {
            return $"City:{city},Street:{street},ZIPcode:{ZIPcode}";
        }
    }
}
```
Person
```
using System;
using System.Collections.Generic;
using System.Linq;
using System.Runtime.CompilerServices;
using System.Text;
using System.Threading.Tasks;

namespace ConsoleApp1
{
    internal abstract class Person
    {
        public String Name { get; set; }
        public int age { get; set; }
        public Address Address { get; set; }

        public Person() { }

        public override string ToString()
        {
            return $" Name:{Name},Age:{age},Address{Address}";
        }

        public abstract Person Clone();

        public static void display(Person[] arr)
        {
            if (arr==null || arr.Length == 0)
            {
                Console.WriteLine("Array is empty");
                return;
            }
            else
            {
                foreach (Person p in arr) { Console.WriteLine(p); }
            }
        }
    }
}
```
Trainee
```
using System;
using System.Collections.Generic;
using System.Linq;
using System.Text;
using System.Threading.Tasks;

namespace ConsoleApp1
{
    internal class Trainee:Person
    {
        public int NID { get; set; }
        public int IntakeNumber { get; set; }

        public Trainee() { }

        public override string ToString()
        {
            return $"NID:{NID},IntakeNumber{IntakeNumber}";
        }
        public override Person Clone()
        {
            Trainee coped = (Trainee)this.MemberwiseClone();
            return coped;
        }
    }
}
```
