# Timer
using HTML , CSS and JAVASCRIPT


Here are a few things the timer does that we’ll be covering in this post:
    
    Displays the initial time remaining
    Converts the time value to a MM:SS format
    Calculates the difference between the initial time remaining and how much time has passed
    Changes color as the time remaining nears zero
    Displays the progress of time remaining as an animated ring
    
Step 1: Start with the basic markup and styles
    
    Let’s start with creating a basic template for our timer. We will add an svg with a circle 
    element inside to draw a timer ring that will indicate the passing time and add a span to show the remaining 
    time value. Note that we’re writing the HTML in JavaScript and injecting into the DOM by targeting the #app element. 
    Sure, we could move a lot of it into an HTML file, if that’s more your thing.
    
Now that we have some markup to work with, let’s style it up a bit so we have a good visual to start with. Specifically, 
we’re going to:

    Set the timer’s size
    Remove the fill and stroke from the circle wrapper element so we get the shape but let the elapsed time show through
    Set the ring’s width and color

Step 2: Setting up the time label
    
    As you probably noticed, the template includes an empty <span> that’s going to hold the time remaining. 
    We will fill that place with a proper value. We said earlier that the time will be in MM:SS format. 
    To do that we will create a method called formatTimeLeft
   
Step 3: Counting down
    
    Let’s think about what we need to count down the time. Right now, we have a timeLimit value that 
    represents our initial time, and a timePassed value that indicates how much time has passed once 
    the countdown starts.

    What we need to do is increase the value of timePassed by one unit per second and recompute the timeLeft 
    value based on the new timePassed value. We can achieve that using the setInterval function.

    Let’s implement a method called startTimer that will:

        Set counter interval
        Increment the timePassed value each second
        Recompute the new value of timeLeft
        Update the label value in the template
 
 Step 4: Cover the timer ring with another ring
 
      To visualize time passing, we need to add a second layer to our ring that handles the animation. 
      What we’re doing is essentially stacking a new green ring on top of the original gray ring so that 
      the green ring animates to reveal the gray ring as time passes, like a progress bar.
      
 Step 5: Animate the progress ring
 
    Let’s see how our ring will look like with different stroke-dasharray values:
    What we can see is that the value of stroke-dasharray is actually cutting our remaining time ring into 
    equal-length sections, where the length is the time remaining value. That is happening when we set the value 
    of stroke-dasharray to a single-digit number (i.e. 1-9).

    The name dasharray suggests that we can set multiple values as an array. Let’s see how it will behave if we 
    set two numbers instead of one; in this case, those values are 10 and 30.
    
    That sets the first section (remaining time) length to 10 and the second section (passed time) to 30. We can use 
    that in our timer with a little trick. What we need initially is for the ring to cover the full length of the circle, 
    meaning the remaining time equals the length of our ring.
    
 Step 6: Change the progress color at certain points of time
 
      First, we need to add two thresholds that will indicate when we should change to the warning and alert states 
      and add colors for each of that states. We’re starting with green, then go to orange as a warning, followed 
      by red when time is nearly up.
