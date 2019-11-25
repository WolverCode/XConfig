# XConfig
Custom Application Configuration Library for .NET programs

XConfig is an easy-to-use library written in C# to save application configuration data of any type. 
It uses both binary and XML serialization to save and load data to and from a configuration file. 

# How to use
To make use of this library, simply add this file to your project or download the release version and add the reference to it, then create a static ConfigManager object to load and save configuration data in your program. 
The ConfigManager class provides methods to get, set and save configuration data to a file. 

# Sample Code

The following program attempts to read a string message stored in the configuration file. If it doesn't exist, the program adds the string message to the configuration file. Run the following program twice to see the results. 

    using System;
    using XConfig;
    class Program
    {
      static ConfigManager configManager;
      public static void Main()
      {
        configManager = new ConfigManager("config.bin", new BSerializer(), true); //Use BSerializer for Binary Serialization 
        //Check if the config db contains a specific data
        if(configManager.Contains("msg"))
        {
          string msg = configManager.Get<string>("msg");
          Console.WriteLine("Message: {0}", msg);
          Console.Read();
          return;
        }
        else
        {
          configManager.Set("msg", "Hello, World!");
          Console.WriteLine("Data saved, restart to load");
          Console.Read();
        }
      }
    }
