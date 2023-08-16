---
{"dg-publish":true,"permalink":"/topics/swift-ui/composition-of-views-using-custom-structures/","dgHomeLink":false}
---

# Composition of Views Using Custom Structures

By now you should have six pages in your **FavouriteThings** app:

![Screen Shot 2022-11-06 at 11.36.32 AM.png](/img/user/Attachments/Screen%20Shot%202022-11-06%20at%2011.36.32%20AM.png)

> [!NOTE]
> ∙ To follow this lesson, it is easiest if the format of all your **FavouriteThings** pages match the structure of what is shown above (a title, a photo, some text). 
> ∙ If you wish, you can [download a Zip file of Mr. Gordon's **FavouriteThings** project](https://github.com/lcs-rgordon/FavouriteThings-Fall2021/archive/62c2042480eb1fbaf9e3d9a84bc21a182930b705.zip) as it is shown above.
> ∙ Double-click the Zip file to expand it on your computer, then from the resulting folder, open the blue Xcode project file.
> ∙ After completing this lesson you can try applying the concepts explained here in your own project.

What if we wanted to adjust the way a view looks on each of these pages?

Say, for example, to add a caption and a credit below every photo on every page?

Here's an example of what this could look like for the **Lasagna** page:

![Pasted image 20221106080904.png|300](/img/user/Attachments/Pasted%20image%2020221106080904.png)

Please do this now... make a similar edit to one of the pages in your **FavouriteThings** app:

![Screen Shot 2022-11-06 at 8.36.38 AM.png](/img/user/Attachments/Screen%20Shot%202022-11-06%20at%208.36.38%20AM.png)

> [!NOTE]
> Code that was present before is highlighted above in grey, and the new code is highlighted in blue.

Take note of the use of the _spacing_ and _alignment_ parameters to control the position of elements within the `VStack` structures.

This is a nice and useful change we don't want to lose, so please go ahead and commit and push your changes now:

![Screen Shot 2022-11-06 at 8.37.23 AM.png](/img/user/Attachments/Screen%20Shot%202022-11-06%20at%208.37.23%20AM.png)

If we had to make that same change to each and every page, it would a tedious exercise.

Instead, we can write our own custom structure that conforms to the `View` protocol. 🎉

Once we write a structure, in the future, we can use it just like the built-in structures that Apple provides through the SwiftUI framework, like `VStack`, `HStack`, `ScrollView`, et cetera.

To do this, we'll make use of the Xcode interface to arrange two files side-by-side.

First, hide the Project navigator by pressing `Command-0`:

![Hiding the Project Navigator.gif](/img/user/Attachments/Hiding%20the%20Project%20Navigator.gif)

Then, show only the editor, and add a second editor on the right:

![Showing Two Editor Panels.gif](/img/user/Attachments/Showing%20Two%20Editor%20Panels.gif)

Now we are viewing the same file in both editor windows.

Next we will create a new view named `PhotoCaptionView` and edit that in the space on the left:

![Creating A New View.gif](/img/user/Attachments/Creating%20A%20New%20View.gif)

On the right is our existing view that shows a photo with a caption.

On the left is our new custom view named `PhotoCaptionView`.

Copy and paste the parts of the user interface that we want to re-use from the existing view on the right to our new view on the left:

![Copying Code Over From One View to Another 2.gif](/img/user/Attachments/Copying%20Code%20Over%20From%20One%20View%20to%20Another%202.gif)

Since we finished that step by creating an *instance* of the new view, `PhotoCaptionView` inside of the existing view on the right, everything looks the same as it did before in the user interface:

![Screen Shot 2022-11-06 at 9.17.35 AM.png](/img/user/Attachments/Screen%20Shot%202022-11-06%20at%209.17.35%20AM.png)

This is a good time to commit and push your work, as some nice progress has been made:

![Screen Shot 2022-11-06 at 9.24.08 AM.png](/img/user/Attachments/Screen%20Shot%202022-11-06%20at%209.24.08%20AM.png)

However, as it currently stands, our new `PhotoCaptionView` is not yet very useful.

Can you predict why?

What would happen if we used `PhotoCaptionView` on all six of our existing **FavouriteThings** pages?

Think about this for a moment before scrolling down.

If you answered:

	"Because it will always show the same photo and caption!"

... then you are correct.

In order to make this truly useful on all six of our existing pages, and for any new pages we might author, then when an *instance* of `PhotoCaptionView` is created, it needs to "ask" for some information.

Specifically, it needs to know:
- what photo to show
- what the caption should be
- what the credit is

So, go ahead and make the following edits to `PhotoCaptionView` – look for the blue bars at left to see where new code was added:

![Screen Shot 2022-11-06 at 9.27.12 AM.png](/img/user/Attachments/Screen%20Shot%202022-11-06%20at%209.27.12%20AM.png)

By adding these *stored properties* to `PhotoCaptionView` we are listing some questions, or *parameters*, that need to receive *arguments*, or answers, when we create instances of `PhotoCaptionView`.

That is why we now see the "red bubbles" in our project where `PhotoCaptionView` is being used:

![Screen Shot 2022-11-06 at 9.33.47 AM.png](/img/user/Attachments/Screen%20Shot%202022-11-06%20at%209.33.47%20AM.png)

Use the **Fix** button to insert placeholders:

![Screen Shot 2022-11-06 at 9.35.34 AM.png](/img/user/Attachments/Screen%20Shot%202022-11-06%20at%209.35.34%20AM.png)

Then, replace the placeholders with arguments:

![Screen Shot 2022-11-06 at 9.37.16 AM.png](/img/user/Attachments/Screen%20Shot%202022-11-06%20at%209.37.16%20AM.png)

We are now providing "answers" to the "questions" that `PhotoCaptionView` asks for.

Finally, we need to actually *use* the answers from the stored properties inside our computed property.

The computed property named `body` is what actually shows the photo and caption.

So, make this final set of edits inside the `body` property:

![Screen Shot 2022-11-06 at 9.58.06 AM.png](/img/user/Attachments/Screen%20Shot%202022-11-06%20at%209.58.06%20AM.png)

Now, our new `PhotoCaptionView` structure is all set to be a "helper" view in our project.

This is a good time to save our work. Commit and push your changes:

![Screen Shot 2022-11-06 at 10.02.26 AM.png](/img/user/Attachments/Screen%20Shot%202022-11-06%20at%2010.02.26%20AM.png)

Finally, the new structure can be used to add a photo caption and credit to every existing page.

Here's how this could be done, for example, on the **Blue Jays** page:

![Using PhotoCaptionView on Another Page 2.gif](/img/user/Attachments/Using%20PhotoCaptionView%20on%20Another%20Page%202.gif)

To close the split-screen view, you can just press the ╳ button at the top left of an editor window:

![Closing the Split Screen View 1.gif](/img/user/Attachments/Closing%20the%20Split%20Screen%20View%201.gif)

Finally, here is what the edits would look like for all remaining pages:

> [!NOTE]
> Old code is highlighted in grey, new code is highlighted in blue.

![Screen Shot 2022-11-06 at 10.19.55 AM.png](/img/user/Attachments/Screen%20Shot%202022-11-06%20at%2010.19.55%20AM.png)

![Screen Shot 2022-11-06 at 10.40.30 AM.png](/img/user/Attachments/Screen%20Shot%202022-11-06%20at%2010.40.30%20AM.png)

![Screen Shot 2022-11-06 at 10.40.52 AM.png](/img/user/Attachments/Screen%20Shot%202022-11-06%20at%2010.40.52%20AM.png)

![Screen Shot 2022-11-06 at 10.41.15 AM.png](/img/user/Attachments/Screen%20Shot%202022-11-06%20at%2010.41.15%20AM.png)

![Screen Shot 2022-11-06 at 10.42.25 AM.png](/img/user/Attachments/Screen%20Shot%202022-11-06%20at%2010.42.25%20AM.png)

By adding `PhotoCaptionView` as a "helper" view, there is no need to copy and paste large chunks of code around.

We can just create an instance of `PhotoCaptionView`, answer the questions it asks by providing arguments for the required parameters, and it does the job that we designed it to do – show a photo, a caption, and a credit.

The formal name for the process we've just applied is *abstraction* and we'll be doing this a lot this year – it will soon be second nature to you as an app developer.

## Exercise: Sweating the Details

If you compare the screenshots at the end of this lesson to one another, and then compare them to the original goal shown at the top of this lesson, you may spot some minor layout issues with the captions.

What are these issues? Describe them in a short post [on Spaces](https://ca.spacesedu.com/) in your portfolio.

Then, can you make some edits to `PhotoCaptionView` to correct these issues? It might help to refer to these [excerpts from SwiftUI Views Quick Start](https://drive.google.com/file/d/1KowxWGeBQGdbW6PtuvRxWZ3ayjp8jzXL/view?usp=share_link).

Once you fix the issues, share your solution in another post [on Spaces](https://ca.spacesedu.com/) in your portfolio.