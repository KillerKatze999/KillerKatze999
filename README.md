## 🧰 DevProfile CLI

A small CLI - style representation of my developer profile, built with C#.


```csharp
using System;
using System.Collections.Generic;

namespace DeveloperProfile
{
  class Program
  {
    static DeveloperProfile BuildProfile()
    {
      DeveloperProfile niklas = new DeveloperProfile();

      niklas.CodingLanguages.Add("C#", "Intermediate");
      niklas.CodingLanguages.Add("JavaScript", "Intermediate");
      niklas.CodingLanguages.Add("HTML", "Intermediate");

      niklas.Tools.Add("Visual Studio");
      niklas.Tools.Add(".NET");
      niklas.Tools.Add("ASP.NET");

      niklas.Architecture.Add("Layered Architecture");
      niklas.Architecture.Add("REST APIs");

      return niklas;
    }

    static void Main(string[] args)
    {

      DeveloperProfile niklas = BuildProfile();

      if (args.Length == 0)
      {
        PrintHelp();
        return;
      }

      string command = args[0].ToLower();

      switch (command)
      {
        case "show":
          ShowProfile(niklas);
          break;

        case "skills":
          ShowSkills(niklas);
          break;

        case "tools":
          ShowTools(niklas);
          break;

        case "architecture":
          ShowArchitecture(niklas);
          break;

        case "help":
          PrintHelp();
          break;

        default:
          Console.WriteLine("❌ Unknown command");
          PrintHelp();
          break;
      }
    }

    static void ShowProfile(DeveloperProfile profile)
    {
      Console.WriteLine("👤 Niklas");
      Console.WriteLine("🚀 Always learning, always building\n");

      ShowSkills(profile);
      ShowTools(profile);
      ShowArchitecture(profile);
    }

    static void ShowSkills(DeveloperProfile profile)
    {
      Console.WriteLine("💻 Skills:");
      foreach (KeyValuePair<string, string> lang in profile.CodingLanguages)
      {
        Console.WriteLine($"- {lang.Key}: {lang.Value}");
      }
      Console.WriteLine();
    }

    static void ShowTools(DeveloperProfile profile)
    {
      Console.WriteLine("🧰 Tools:");
      foreach (string tool in profile.Tools)
      {
        Console.WriteLine($"- {tool}");
      }
      Console.WriteLine();
    }

    static void ShowArchitecture(DeveloperProfile profile)
    {
      Console.WriteLine("🏗️ Architecture:");
      foreach (string arch in profile.Architecture)
      {
        Console.WriteLine($"- {arch}");
      }
      Console.WriteLine();
    }

    static void PrintHelp()
    {
      Console.WriteLine("DevProfile CLI");
      Console.WriteLine("Usage:");
      Console.WriteLine("  devprofile show");
      Console.WriteLine("  devprofile skills");
      Console.WriteLine("  devprofile tools");
      Console.WriteLine("  devprofile architecture");
    }
  }

  class DeveloperProfile
  {
    public Dictionary<string, string> CodingLanguages { get; set; } = new Dictionary<string, string>();
    public List<string> Tools { get; set; } = new List<string>();
    public List<string> Architecture { get; set; } = new List<string>();
  }
}

```md

```bash

> devprofile hack-the-planet

❌ Unknown command
DevProfile CLI
Usage:
  devprofile show
  devprofile skills
  devprofile tools
  devprofile architecture

> devprofile show

👤 Niklas
🚀 Always learning, always building

💻 Skills:
-C#: Intermediate
- JavaScript: Intermediate
- HTML: Intermediate

🧰 Tools:
- Visual Studio
- .NET
- ASP.NET

🏗️ Architecture:
-Layered Architecture
- REST APIs
