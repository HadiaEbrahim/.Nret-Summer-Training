Student Class
```
using System;
using System.Collections.Generic;
using System.Linq;
using System.Text;
using System.Threading.Tasks;

namespace DAY1
{
    internal class Student
    {
        public string Name {  get; set; }
        public int Grade {  get; set; }
        public List<string> Skills { get; set; }
        public string Department { get; set; }

    }
}
```
String Class 
```
using System;
using System.Collections.Generic;
using System.Linq;
using System.Text;
using System.Threading.Tasks;

namespace DAY1
{
    public static class Stringg
    {
        public static string ReverseText(this string s) { 
               if(string.IsNullOrEmpty(s)) return s;

               char [] chars = s.ToCharArray();
               Array.Reverse(chars);
            return new String(chars);
        
        }
    }
}
```
Program
```
namespace DAY1
{
    internal class Program
    {
        static void Main(string[] args)
        {
            //Question 1 – Where

            List<int> numbers = new()
            {
                5, 10, 15, 20, 25, 30
            };

            var result= from l in numbers 
                        where l >15 
                        select l;
            //Question 2 – Select
            List<Student> students = new()
            {
                new Student { Name = "Ali", Grade = 90 },
                new Student { Name = "Sara", Grade = 70 },
                new Student { Name = "Omar", Grade = 80 }
            };
            var student = students.Select(s => new{ s.Name,s.Grade});

            //Question 3 – SelectMany
            List<Student> students2 = new()
            {
                new Student
                {
                    Name = "Ali",
                    Skills = new List<string> { "C#", "SQL" }
                },
                new Student
                {
                    Name = "Sara",
                    Skills = new List<string> { "HTML", "CSS" }
                }
            };

            var data = students2.SelectMany(s => s.Skills);

            //Question 4 – OrderBy & ThenBy
            List<Student> students3 = new()
            {
                new Student { Name = "Ali", Department = "IT", Grade = 90 },
                new Student { Name = "Sara", Department = "HR", Grade = 80 },
                new Student { Name = "Ahmed", Department = "IT", Grade = 85 },
                new Student { Name = "Omar", Department = "HR", Grade = 75 }
            };
            var res = students3.OrderBy(s => s.Department)
                .ThenBy(s => s.Name);
            //Question 5 – First & Any
            List<Student> students4 = new()
            {
                new Student { Name = "Ali", Grade = 90 },
                new Student { Name = "Sara", Grade = 45 },
                new Student { Name = "Omar", Grade = 80 }
            };

            var first = students4.First(s=>s.Grade>80);
            bool any = students4.Any(s => s.Grade < 80);

            //Question 6 – Count, Sum & Average
            List<Student> students5 = new()
            {
                new Student { Name = "Ali", Grade = 90 },
                new Student { Name = "Sara", Grade = 70 },
                new Student { Name = "Omar", Grade = 80 },
                new Student { Name = "Mona", Grade = 60 }
            };
            int grades=students5.Count(s=>s.Grade>=70);
            int sum=students5.Sum(s=>s.Grade);
            double AVG=students5.Average(s=>s.Grade);

            //Question 7 – Skip & Take
            List<int> numbers2 = new()
            {
                10, 20, 30, 40, 50, 60, 70, 80, 90
            };

            var elements=numbers2.Skip(3).Take(3).ToList();
            //Question 8 – Mixed LINQ Challenge 
            List<Student> students6 = new()
            {
                new Student { Name = "Ali", Department = "IT", Grade = 90 },
                new Student { Name = "Sara", Department = "HR", Grade = 70 },
                new Student { Name = "Omar", Department = "IT", Grade = 80 },
                new Student { Name = "Ahmed", Department = "HR", Grade = 95 },
                new Student { Name = "Mona", Department = "Sales", Grade = 60 }
            };
            var st=from a in students6
                   where a.Grade>=70
                   select a;
            var grades2=students6.OrderByDescending(s=>s.Grade);

            var ress=from a in students6 select new { a.Name, a.Department };
        }
    }
}
```
