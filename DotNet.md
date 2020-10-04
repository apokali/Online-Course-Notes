# Introduction
* One great feature about C# is that it has a grabage collector, that you dont 
  need to free up the memories you allocated

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

### Example - Dictionary
Starting from this example, the main function will will ignored
```C#
Dictionary<Strnig, String> config = new Dictionary<string, string>();
config.Add("resolutioin", "1920x1080");
config.Add("title", "Mywebsite");

Console.WriteLine(config["title"]);

foreach (var setting in config)
{
    Console.WriteLine(setting.Value);
}
```
```
