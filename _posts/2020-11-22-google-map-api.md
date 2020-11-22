---
layout: post
author: "Samvel Vardanyan"
title: "Google Map API"
date: 2020-11-22 10:30:00 -0700
categories: jekyll update
permelink: /:categories/:year/:month/:day/:title
---

**Introduction**

This week I am going to talk about using google map in our project. So, I have built a small quiz for CSUN map. There are 5 questions and we need to answer all questions correctly in order to get 100%. Basically we have CSUN map and 5 questions asking to find a building on CSUN map and if we find it and double click on it we get correct answer if we don't find the specified building on the map we don't get any points for that questions. The process of answering the questions is timed. This is what it looks like:

\
![image](/blog/assets/images/google-api.png)

\
**The Logic**

I am not going to talk about HTML or CSS and how they are structured for this project but I will briefly go over the logic before talking about google map API integration. We have 5 questions that are highlighted in blue which need to be answered next to it we have google CSUN's map where we can double click on the building that we think corresponds to that question. Underneath of questions we have correct answers displayed every time we correctly answer a question we get 1 point added to this. Next we have timer. It starts automatically when we double click on the map and stops when we click on the map for the 5th time meaning we are answering the last 5th question. The timer stops when all 5 questions are answered, they can be wrong or right answers. If the answers is correct the question turn green as well the corresponding building on the map and if the answer is wrong the question and the building on the map that we clicked turn red.

\
![image](/blog/assets/images/google-api-answered.png)

\
**Set up Google Map**

Once we have our JavaScript code written we need to add `Google's API` for the map to our project. In order to do that we need to go [google map API](https://developers.google.com/maps/documentation/javascript/overview) website and sign up for API. Once we sign up we choose which kind of map API we are interested in. In my case it was `Maps JavaScript API`, we choose that and generate API key. It look something like this: `AIzaSyBxZHa_hgZTdlCQ_C5p9mRhwztquvp7c`. Now we go back to our JavaScript code and write a map function to initialize a map and connect it to API map:

{% highlight ruby %}
function initMap() {
map = new google.maps.Map(document.getElementById("map"), {
center: { lat: 34.238944, lng: -118.5275 },
zoom: 17,
disableDoubleClickZoom: true,
zoomControl: false,
mapTypeControl: false,
draggable: false,
keyboardShortcuts: false,
streetViewControl: false,
mapTypeId: "hybrid"
});
{% endhighlight %}

Next step is to add our API key to our script tags:  
Note: this will go in our HTML file

{% highlight ruby %}

<script defer
    src="https://maps.googleapis.com/maps/api/js?key=YOUR_API_KEY&callback=initMap">
</script>

{% endhighlight %}
Just replace `YOUR_API_KEY` with your API key:

{% highlight ruby %}

 <script
      src="https://maps.googleapis.com/maps/api/js?key=AIzaSyBxZHa_hgZTdlCQ_C5p9mRhwztquvp7c&callback=initMap"
      async
      defer
    ></script>

    {% endhighlight %}

We have successfully integrated Google Map API into our project. The final project is [here](https://cit-384-google-maps-project-sv.glitch.me/).
