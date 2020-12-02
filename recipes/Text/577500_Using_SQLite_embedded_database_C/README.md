## Using SQLite as an embedded database with C# instantly  
Originally published: 2010-12-15 01:20:32  
Last updated: 2010-12-15 01:24:06  
Author: Stephen Akiki  
  
http://akiscode.com/articles/sqlite-csharp.shtml


There are a few libaries that every programmer loves and knows because they either:

* Saves you a ton of time coding
* Does something that you don't know how to do yourself


Examples include cURL, SQLite, or even the .NET library itself. Many of us have to create CRUD (Create, Read, Update, Delete) projects on a semi-regular routine. SQLite is nice in the fact that it handles all the CRUD-y stuff (bad pun I know) in a simple, small and standalone package. But because SQLite is so nice to use (when compared to say XML), the Gods have cursed SQLite to cause many headaches if you are a new to it on C# to balance the world karma (or something like that). Also note that i'm not going to explain what any of the code does as its pretty self explanatory. Anyway, here is a complete example on how to setup an embedded SQLite database, insert some data into it, and then update a listview with only certain columns from the database:

**The Fun Stuff**

1. **NOTE: I've made a demo project that you can download [here](http://akiscode.com/articles/Akiscode-SQLiteTest.zip). It includes the DLLs and everything that i've talked about below. **

2. Download the setup from [these guys](http://sqlite.phxsoftware.com/) and install it.

3. Start a new Project in Visual C# Studio (I'm using version 2010 Express). Make it a Windows Forms Application. Save it anywhere. For this example, I will save it on the Desktop and call the project "Akiscode-SQLiteTest. At the time I was doing this, the SQLite dll only worked with a program targeted at .NET version 3.5. To learn how to change that go [here](http://msdn.microsoft.com/en-us/library/bb772098\(v=vs.90\).aspx).

4. Go to the Solutions Explorer on the top right of your VC setup. Right click references and select "Add Reference". Go to the ".NET" tab and find the entry named "System.Data.SQLite". Not "System.Data.Sql", not "System.Data.SqlXml", NOT "MySql.Data". Just find "System.Data.SQLite". If you can't find it, sort the list by name. If you still can't find it, restart VC and try this process again. Still can't find it? Run the installer and do it all over again. Still not there? Well I can't really help you, hand in your programming badge on the way out.

5. Once you added "System.Data.SQLite", right click it and select properties. Set "Copy Local" to true.

6. Ok type at the top "using "using System.Data.SQLite;" without the quotes.

7. Go back to the form designer. Add a listview component. In the properties window (bottom right) make sure the property view is set to "Details". Then right click on the listview and add columns. For this example I added two called "First Name" and "Last Name"

8.Ok now for some copy and paste coding (my favorite): Double click the form to make a "Form1_Load" function appear and paste the following in it: