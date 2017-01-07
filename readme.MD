#VueJS timecard
For Kassia to calculate her hours worked, rounded to the quarter hour as per the policy at her employer.

This is my second time using VueJS, and is based on my first project called [first-vuejs](https://github.com/jeremy21212121/first-vuejs), which is a to-do list.

This is the first time I've had to write a non-trivial function in a VueJS project, and it took me a while. The function in question is calcTime() and it takes user entered time strings, parses them into decimal format and finds the difference, which is the number of hours worked. It then rounds to the nearest quarter hour, which is what they do at the workplace this is intended to be used at.

Writing the function was actually easy and fun. I figured out all the pieces in the browser JS console, then put them together and tested the function to find the bugs. I put a bunch of console.log's in the function to output intermediate values so I could manually verify them. I found a mistake where the hundredths of an hour were off by exactly two orders of magnitude this way.

I spent at least an hour trying to figure out a render error when I tried to display hours worked using calcTime(). I had used the name of the vue instance ('app') in the function, instead of 'this'. I did this in my [first-vuejs](https://github.com/jeremy21212121/first-vuejs) methods for some reason, and it worked then, but did not work with this function as 'app' was still undefined at that time. After reading the docs a lot and trying many different things, i replaced two uses of 'app.items[index]...' with 'this.items[index]...' and voila, it worked. I had been looking for "bigger" errors, due to my unfamiliarity with vuejs.

Next I'm going to try to figure out how to use some sort of cookie or localStorage so the data entered will persist even if the tab is closed.

## Update
localStorage works great for this purpose. I implemented an auto backup everytime the list is changed, and auto restore on load if localStorage.backup is found.

Next I want to make something server side to store data and possibly support multiple users.
