---
{"dg-publish":true,"permalink":"/tasks/trading-cards/","tags":["ics3u"],"dgHomeLink":false}
---

# Trading Cards
## Objective

Create the look and feel of trading cards for sports, games, or other areas of interest.

![Screenshot 2023-01-12 at 10.07.50 AM.png](/img/user/Attachments/Screenshot%202023-01-12%20at%2010.07.50%20AM.png)

## Purpose

A second opportunity to demonstrate your understanding of key concepts from the first thread of this course. Specifically, using structures to:

- describe related data
- build user interfaces

In the next half of this task (to be shared soon) this will be your first opportunity to demonstrate understanding of a key concept from the second thread of this course. Specifically:

- use of lists as a data structure

## Success criteria and exemplar
1. Made a rough plan where you have identified how various structures (`VStack`, `HStack`, `ZStack`, `Image`, et cetera) might be used to create part of your design.
   
   For example:
   
   ![Pasted image 20230112102153.png](/img/user/Attachments/Pasted%20image%2020230112102153.png)
   
   And:
   
   ![Pasted image 20230112102253.png](/img/user/Attachments/Pasted%20image%2020230112102253.png)
   
2. Created a static layout where the look and feel of a trading card is reproduced.
   
   ![Screenshot 2023-01-12 at 10.24.42 AM.png](/img/user/Attachments/Screenshot%202023-01-12%20at%2010.24.42%20AM.png)
   
3. Created a structure named `TradingCard` (or similar) using appropriate property names, capitalization, and selection of data types that will allow you to store the data shown on your card's static layout.
   
   ![Screenshot 2023-01-12 at 10.26.01 AM.png|325](/img/user/Attachments/Screenshot%202023-01-12%20at%2010.26.01%20AM.png)
   
4. Created instances of your structure to hold information for cards.
   
   Here is one example:
   
   ![Screenshot 2023-01-12 at 10.32.18 AM.png|600](/img/user/Attachments/Screenshot%202023-01-12%20at%2010.32.18%20AM.png)
   
> [!IMPORTANT]
> **UPDATE – Friday January 13**: You can stop here on this task – we will complete items 5 and 6 next week in class together. *– Mr. Gordon*
   
5. Applied abstraction by converting your static layout to use a property named `card` (or similar) that accepts an instance of your `TradingCard` structure.
   
   To demonstrate even more mastery of abstraction, use *helper views* to make the layout more concise and easier to understand:
   
   ![Screenshot 2023-01-12 at 10.28.46 AM.png](/img/user/Attachments/Screenshot%202023-01-12%20at%2010.28.46%20AM.png)
   
   ==NOTE==: You used helper views to draw the buttons on the Stopwatch app interface in thread 1.
   
6. Made use of a SwiftUI `List` structure to allow for navigation down to several different cards:
   
   ![Screenshot 2023-01-12 at 10.38.25 AM.png](/img/user/Attachments/Screenshot%202023-01-12%20at%2010.38.25%20AM.png)
   
7. Written code that is well-formatted and easy to read.
   
8. You have used source control well by [committing and pushing your work](https://www.russellgordon.ca/cs/source-control/introduction/using-source-control.pdf) to a remote on GitHub at regular intervals.
   
   ![Screenshot 2023-01-12 at 10.39.33 AM.png|500](/img/user/Attachments/Screenshot%202023-01-12%20at%2010.39.33%20AM.png)
   
   ==NOTE:== You would likely have more commits than are shown in this example.

## What you'll need to begin
- [ ] Xcode
- [ ] the [SF Symbols App](https://developer.apple.com/sf-symbols/) installed on your computer, also for reference
- [ ] a copy of [SwiftUI Views Quick Start](https://drive.google.com/file/d/19q9TiI0C3TJW7SGUavhA0sezGZceDNBH/view?usp=share_link) downloaded to your computer, so you can look up examples as needed
      
## Getting started

1. Create a new iOS app:
   
   ![Screenshot 2023-01-12 at 9.18.08 AM.png|700](/img/user/Attachments/Screenshot%202023-01-12%20at%209.18.08%20AM.png)
   
2. Name the app `TradingCards`:
   
   ![Screenshot 2023-01-12 at 9.18.22 AM.png|700](/img/user/Attachments/Screenshot%202023-01-12%20at%209.18.22%20AM.png)
   
3. Save the app in your Computer Studies folder, ensuring that source control is enabled:
   
   ![Screenshot 2023-01-12 at 9.18.37 AM.png|700](/img/user/Attachments/Screenshot%202023-01-12%20at%209.18.37%20AM.png)
   
4. Then create a public remote on GitHub:
   
   ![Screenshot 2023-01-12 at 10.06.32 AM.png|400](/img/user/Attachments/Screenshot%202023-01-12%20at%2010.06.32%20AM.png)
   
5. Now work to complete each item described above in the [[Tasks/Trading Cards#Success criteria and exemplar\|success criteria]].
   
   ==Please remember to commit and push your work regularly.==

## Progress and due date

The task is due by 11 PM this Sunday, January 15, 2023.

Prior to the final deadline, [on Spaces](https://ca.spacesedu.com/) :
- [ ] Share progress regularly in your private portfolio space
	- [ ] Be sure to post screenshots
	- [ ] ==Be sure to post the address of your GitHub remote at some point==

> [!NOTE]
> Your work is not considered as handed in until the GitHub remote has been shared *and* you have [committed and pushed](https://www.russellgordon.ca/cs/source-control/introduction/using-source-control.pdf) all your work.

## Further examples

Here are some examples of possible layouts that you could aim to reproduce, or use as inspiration for a similar layout:

![Trading Card Template Examples-7 (dragged).png|400](/img/user/Attachments/Trading%20Card%20Template%20Examples-7%20(dragged).png)

![Trading Card Template Examples-3 (dragged).png|400](/img/user/Attachments/Trading%20Card%20Template%20Examples-3%20(dragged).png)

![Trading Card Template Examples-2 (dragged).png|400](/img/user/Attachments/Trading%20Card%20Template%20Examples-2%20(dragged).png)

![Trading Card Template Examples-1 (dragged).png|400](/img/user/Attachments/Trading%20Card%20Template%20Examples-1%20(dragged).png)

![Trading Card Template Examples-4 (dragged).png|400](/img/user/Attachments/Trading%20Card%20Template%20Examples-4%20(dragged).png)

![Trading Card Template Examples-5 (dragged).png|400](/img/user/Attachments/Trading%20Card%20Template%20Examples-5%20(dragged).png)

![Trading Card Template Examples-6 (dragged).png|400](/img/user/Attachments/Trading%20Card%20Template%20Examples-6%20(dragged).png)

![Trading Card Template Examples-8 (dragged).png|400](/img/user/Attachments/Trading%20Card%20Template%20Examples-8%20(dragged).png)

![Trading Card Template Examples-9 (dragged).png|400](/img/user/Attachments/Trading%20Card%20Template%20Examples-9%20(dragged).png)