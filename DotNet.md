# Introduction

### Garbage Collection
* App might slow down or crash without garbage collection
* Garbage collectoin saves us time and effort
* Manually managing memory might sometimes be more effcient

# Collections and Group Obecjts
### Collections
* Store gourped or similar data
* Not a database
* Array and List are common examples
* Over a dozen collections in .NET

### Example - Basic for loop and List
```C#
using System;
using System.Collections.Generic;

namespace LearningDotNet
{
    class Program
    {
        static void Main(string[] args)
        {
            List<String> customers = new List<string>();
            customers.Add("Kim");
            customers.Add("Lin");
            customers.Add("Julien");
            foreach (var customer in customers)
            {
                Console.WriteLine(customer);
            }
            Console.WriteLine("Hello World!");
        }
    }
}
```
