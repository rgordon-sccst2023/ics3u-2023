---
{"dg-publish":true,"permalink":"/topics/databases/making-a-todo-list-app/","dgHomeLink":false}
---

# Making a To-do List App

The purpose of this tutorial is to demonstrate how an app can be transitioned from stored data "in memory" to storing data in a database.

The benefit of storing information in a database is that the data will *persist* between sessions when using the app.

That is, if you close the app, then open it again, the data you created earlier will be retained.

## Re-arrange the project

Following our earlier convention, first organize your project so that there is a group named **Views** which will hold the files that create the user interface of the app.

Create a file named `ListView` which will show the to-do list.

![Screenshot 2023-04-03 at 1.23.33 PM.png](/img/user/Attachments/Screenshot%202023-04-03%20at%201.23.33%20PM.png)

## Create a static interface

As we did when we first learned how to create user interfaces, make a static interface for the app.

The interface should look as shown below.

The start of the code you need is shown – add to this code to create the static interface.

![Screenshot 2023-04-03 at 1.24.54 PM.png](/img/user/Attachments/Screenshot%202023-04-03%20at%201.24.54%20PM.png)

> [!TIP]
> Use the SF Symbols app and a `Label` structure to create the items in the list.

## Make the model

The next step when building an app is to transition to app away from being completely static and to begin using a list.

Create a `TodoItem` structure to serve as the primary model for the data shown in this app:

![Screenshot 2023-04-03 at 1.27.51 PM.png](/img/user/Attachments/Screenshot%202023-04-03%20at%201.27.51%20PM.png)

Then, update the `List` structure to use the array you created just now:

![Screenshot 2023-04-03 at 1.28.41 PM.png](/img/user/Attachments/Screenshot%202023-04-03%20at%201.28.41%20PM.png)

## Add items to the list

The next step is to make it possible to add items to the list.

This involves making the add item button functional.

The first two change out of three changes required are shown below:

![Screenshot 2023-04-03 at 1.30.58 PM.png](/img/user/Attachments/Screenshot%202023-04-03%20at%201.30.58%20PM.png)

The first change has two sub-parts:

1. Add a list marked with the named `todoItems` that holds the list of items to be completed.
   
   It is marked with the `@State` property wrapper because the contents of the list will change while the app is run.
   
   The property wrapper `@State` tells SwiftUI to watch the list for changes, and update the user interface when data in the list is changed.

2. The second major change involves filling in the action that will occur when the **Add** button is tapped by the user.
   
   Review the comments shown to understand each step that is taken. 
   
Now make the final change required – change the name of the array that the `List` structure operates on so that it uses the `todoItems` array:

![Screenshot 2023-04-03 at 1.35.04 PM.png](/img/user/Attachments/Screenshot%202023-04-03%20at%201.35.04%20PM.png)

## Copy the database into the app

At the start of class, we [created a database](https://youtu.be/iN7PSDF65k4) to hold the data for this app.

If you edit the `TodoItem` table structure, it should look like this:

![Screenshot 2023-04-06 at 11.08.49 AM.png|500](/img/user/Attachments/Screenshot%202023-04-06%20at%2011.08.49%20AM.png)

Now drag and drop that file, `db.sqlite`, into the **Model** group in your application.

Be sure that the file is added to the **TodoList** target:

![Screenshot 2023-04-03 at 1.04.29 PM.png](/img/user/Attachments/Screenshot%202023-04-03%20at%201.04.29%20PM.png)

## Add the Blackbird package

We will access our SQLite database via **Blackbird**, a third-party package authored by Marco Arment.

In Xcode, select **File > Add Packages...** from the menus, and in the upper-right corner of the dialog box that appears, copy and paste this address:

	https://github.com/marcoarment/Blackbird

![Screenshot 2023-04-03 at 1.42.27 PM.png](/img/user/Attachments/Screenshot%202023-04-03%20at%201.42.27%20PM.png)

Then press the **Add Package** button.

You will see this secondary dialog – again, press **Add Package**:

![Screenshot 2023-04-03 at 1.43.06 PM.png](/img/user/Attachments/Screenshot%202023-04-03%20at%201.43.06%20PM.png)

## Add the helper code

Every iOS application has a private *sandbox* where files it creates can be saved on a device.

A structure named `AppDatabase` will handle the job of copying our database from the *app bundle* in our Xcode project into the sandbox for our app.

This code will be identical for every app you write that uses Blackbird to access a database.

Therefore, you do not need to write it yourself.

So, just create a group named **Helpers**, then create a Swift file named `AppDatabase.swift`.

Into that file, copy and paste [the code found here](https://gist.githubusercontent.com/russellgordon/cb3f1ff147742a367cb29bc9347fd55f/raw/35128c28f13fa256c1ca0eb7acac8d3173da1e2f/AppDatabase.swift).

## Read data from the database

Now we will make modifications to read information from the database.

First, update your `TodoList` model file with the following changes:

![Screenshot 2023-04-03 at 1.48.04 PM.png](/img/user/Attachments/Screenshot%202023-04-03%20at%201.48.04%20PM.png)

> [!Discussion]
> Examining new steps or syntax:
> 1. The `import Blackbird` statement adds the functionality of the **Blackbird** database-access package to this source code file. Without this statement we could not use the **Blackbird** package and in turn access the database we created earlier.
> 2. We make the `TodoItem` structure conform to the `BlackbirdModel` protocol. This makes it possible to draw rows from the `TodoItem` table in the database and create corresponding instances of the `TodoItem` structure that contain the data from each row.
> 3. We indicate which properties in our structure match up to fields (columns) in the database table. Technically it is possible to have additional properties in our structure that do not correspond to any field in the database table, but that is likely to be a rare occurrence.

Second, update the app entry point file with these changes:

![Screenshot 2023-04-03 at 1.49.02 PM.png](/img/user/Attachments/Screenshot%202023-04-03%20at%201.49.02%20PM.png)

> [!Discussion]
> Examining new steps or syntax:
> 1. This change makes it possible to access the database from all views contained in  our application.
>    
>    `AppDatabase.instance` returns an instance of the `Blackbird.Database` type. This establishes the connection to the `db.sqlite` file we created earlier.
>    
>    Using the `.environment` modifier, this instance of the database is inserted [into the environment](https://www.fivestars.blog/articles/how-to-define-environment-values/) using the `.blackbirdDatabase` environment key.
>    
>    So, what is the *environment* in a SwiftUI application and how is it used? The environment contains information that any view within an app may need to access later on. It is helpful because it allows us to share information between views without having to pass arguments to parameters each time a new instance of a structure is created.
>    
>    The `.blackbirdDatabase` environment key is defined in the `Blackbird` package. We simply use it and provide an instance of `Blackbird.Database` tied to the `db.sqlite` file.

Third, make these changes to the `ListView` structure:

![Pasted image 20230403135045.png](/img/user/Attachments/Pasted%20image%2020230403135045.png)

> [!Discussion]
> Examining new steps or syntax:
> 1. Here we change the array of `todoItems` so that they are read from the database table instead of from an array we previously hard-coded in our app's model.
>    
>    `@BlackbirdLiveModels` is a custom view modifier defined in the **Blackbird** package. It is somewhat like the `@State` view modifier – any time the contents of the table that is connected to this view modifier changes – SwiftUI will automatically *see* the changes and update our app's user interface accordingly.
>    
>    So, what is this?
>    
> 		{ db in
>			try await TodoItem.read(from: db)
>		}
>	This is a closure – a block of code – that identifies what table's data should be read from the database.
>	
>	In this case, we read all data that exists in the `TodoItem` table.
>	
>	The `try` keyword is required because reading from the database may work – or it may not. When code might fail, we must invoke that code using the `try` keyword. We can [handle any errors that occur immediately](https://www.hackingwithswift.com/example-code/language/how-to-use-try-catch-in-swift-to-handle-exceptions) if we use the `try` within a `do-catch` block. Or we can pass the responsibility for handling errors on to whatever code created this instance of `ListView`. Here, since we are not reading from the database within a `do-catch` block, we are passing the responsibility on to the *caller* – the code that created `ListView`.
>	
>	Finally, the `await` keyword is required because reading from the database is an *asynchronous* operation. This means that work can be done alongside other work (like drawing the user interface of the app or responding to taps on the screen from the user). Whenever the read operation from the database is completed, the interface will be re-drawn using the new contents of the `todoItems` property.

Fourth and finally, for now, comment out the code for adding a new item to the list, and then update the line of code that iterates over `todoItems` so that it iterates over `todoItems.results` instead:

![Screenshot 2023-04-03 at 1.52.15 PM.png](/img/user/Attachments/Screenshot%202023-04-03%20at%201.52.15%20PM.png)

> [!Discussion]
> Examining new steps or syntax:
> 1. This change is required because `todoItems`, when populated by the **Blackbird** package, is no longer simply an array of type `TodoItem`. Instead, the `todoItems` property contains additional information that will be useful later on. We can access an array of `TodoItem` instances that reflect the contents of the database table using the `todoItems.results` property instead.

> [!TIP]
> Now continue with [[Topics/Databases/Making a Todo List App, Part 2\|part 2 of this tutorial]].