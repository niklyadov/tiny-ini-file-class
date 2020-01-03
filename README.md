
# tiny-ini-file-class
A simple tiny class on C# learn your program to read/write ini files..

## **Example usage #1 (write):**

````csharp
IniFile file = new IniFile("settings.ini");
            
file.Write("hello", "world", "main");
file.Write("2020", "Happy New Year!", "main");
````
This code creates file (settings.ini), and creates 2 lines under block [main]

````ini
[main]
hello=world
2020=Happy New Year!
````

## **Example usage #2 (read):**

In file `settings.ini`:
````ini
[main]
hello=world
2020=Happy New Year!
````
Write this code:
````csharp
IniFile file = new IniFile("settings.ini");

if(file.KeyExists("2020", "main"))
     Console.WriteLine(file.Read("2020", "main"));
````
This code write in console `Happy New Year!`


## **Example usage #3 (delete key):**

Also, you can delete all line (key && value), for example:

````csharp
IniFile file = new IniFile("settings.ini");

if(file.KeyExists("hello", "main"))
     file.DeleteKey("hello", "main");
````

File `settings.ini` before operation
````ini
[main]
hello=world
2020=Happy New Year!
````

File `settings.ini` after operation
````ini
[main]
2020=Happy New Year!
````

## **Example usage #4 (delete section):**

Also, you can delete all values in section (block), for example:

````csharp
IniFile file = new IniFile("settings.ini");

file.DeleteSection("main");
````

File `settings.ini` before operation
````ini
; Comment
; Comment2
[main]
hello=world
2020=Happy New Year!
````

File `settings.ini` after operation (all block `main` has been removed)
````ini
; Comment
; Comment2
````

## **Example usage #5 (file access):**

Default access for file - it's a `Read And Write`, but you can set access  manually in code to `ReadOnly` or `WriteOnly`. For example, if try write to file without rules, you can't do it and program was generated a new exceprion.

````csharp

// read & write (default access)
IniFile fileFullAccess = new IniFile("settings.ini", FileAccess.ReadWrite);

// only read access
IniFile fileReadOnlyAccess = new IniFile("settings.ini", FileAccess.Read);

// only write access
IniFile fileWriteOnlyAccess = new IniFile("settings.ini", FileAccess.Write);

//exception on write with Readonly access
fileReadOnlyAccess.Write("hello", "world1", "main");

````

# That`s all! Thanks for reading!
