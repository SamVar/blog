---
layout: post
author: "Samvel Vardanyan"
title: "Typing Test"
date: 2020-11-06 01:15:00 -0700
categories: jekyll update
permelink: /:categories/:year/:month/:day/:title
---

This week I am going to make a `Typing Test` web app using `JavaScript` for my CIT 384 class. This assignment was due 2 days ago. This is web based application and that's why we first need to write HTML and CSS before writing the logic in JS. I am not going to get into details of writing HTML and CSS, assuming those are the easiest parts of this assignment, instead I will go deep into writing the logic of the web app in JavaScript.

**Requirements**

- Code editor (I use VS Code)
- Basic knowledge of HTML CSS and JavaScript

**Actual Code**

{% highlight ruby %}
const testWrapper = document.querySelector(".test-wrapper");
const testArea = document.querySelector("#test-area");
const originText = document.querySelector("#origin-text p").innerHTML;
const resetButton = document.querySelector("#reset");
const theTimer = document.querySelector(".timer");

var intervalID;

//Timer function starts when keyboard is pressed
function timer() {
var minutes = 0,
seconds = 0,
miliSeconds = 0;

intervalID = setInterval(function() {
miliSeconds++;

    if (miliSeconds == 100) {
      miliSeconds = 0;
      seconds++;
    }
    if (seconds == 60) {
      seconds = 0;
      minutes++;
    }

    //Adds leading 0 to minutes and seconds
    if (minutes < 10) {
      if (seconds < 10) {
        theTimer.innerHTML =
          "0" + minutes + ":" + "0" + seconds + ":" + miliSeconds;
      } else {
        theTimer.innerHTML = "0" + minutes + ":" + seconds + ":" + miliSeconds;
      }
    } else {
      if (seconds < 10) {
        theTimer.innerHTML = minutes + ":" + "0" + seconds + ":" + miliSeconds;
      } else {
        theTimer.innerHTML = minutes + ":" + seconds + ":" + miliSeconds;
      }
    }

}, 10);
}

//Adding Event Listeners

// Event listener to start timer when keyboard is pressed
testArea.addEventListener("keypress", keyboardEvent);

//This function executed when keyboard is pressed
function keyboardEvent() {
timer();
eventListenerRemover();
}

//Removes event listener for keypress
function eventListenerRemover() {
testArea.removeEventListener("keypress", keyboardEvent);
}

//Adding Event Listener for Reset Button
resetButton.addEventListener("click", function() {
clearInterval(intervalID);
theTimer.innerHTML = "00:" + "00:" + "00";
testArea.value = "";
testWrapper.style.borderColor = "grey";
testArea.addEventListener("keypress", keyboardEvent);
});

// Event listener to check keyboard input with original text

testArea.addEventListener("keyup", function() {
var testAreaLength = testArea.value.length;

var j = 0;
for (let i = 0; i < testAreaLength; i++) {
if (testArea.value[i] == originText[i]) {
testWrapper.style.borderColor = "green";

      j++;
    } else {
      testWrapper.style.borderColor = "red";
    }

    if (j == originText.length) {
      clearInterval(intervalID);
    }

}

if (testAreaLength == 0) {
testWrapper.style.borderColor = "grey";
}
});
{% endhighlight %}

\
**This is how the final result needs to look**

\
![image](/blog/assets/images/typing-test.png)

Once we start typing the timer starts automatically and the gray borders around the text area turn green if we type correctly, if we type something incorrect the borders turn red. Once we done typing everything correctly into text area the timer stops automatically. Once we done we can push `Start Over` button it will reset the timer to zero, the borders to gray and will delete the text we typed.

\
**The Logic Behind The Code**

First we need a timer function which is responsible for seconds minutes and miliseconds. Everytime a user starts typing something in the text area the function `Timer` gets called and starts timing untill user resets it or types everything correctlly. Second thing we need to do is to add event listener so if user presses any key on the keyboard the timer function gets called and starts timeing. Next thing we need to do is to create a function that checks user's input with original text. If everything matches this function stops the timer and text area border turns green but if text entered does not match with original text border turns red and timer does not stop. Timer stops only if enetered text matches with original text. Last thing we need is to create a function that's responsible for button `Start Over`. If this button is pressed `StartOver` function gets called it sets the timer to zero, deletes all the inputs in text area and turns the text area border to gray.
You can check my final project [here](https://cit384-time-typing-test-sv.glitch.me/).
