---
layout: post
author: "Samvel Vardanyan"
title: "Viewport Function"
date: 2021-03-11 20:20:00 -0700
categories: jekyll update
permelink: /:categories/:year/:month/:day/:title
---

**Introduction**

This week I am going to talk about how I made a function in javascript that pauses youtube embedded video on your website on user scroll. So, I created this functionality and added to our Senior Project website to make the website more user friendly and easy to use. So, every time when a video playing on a website and user scrolls away the video pauses itself. The user doesn't have to go back to stop the video manually and then scroll away.

\
**HTML**

In order to create this function which I called **Viewport Function** first we need to embed a youtube video into our html. To do that we copy embedded code from youtube and paste it into our website:

{% highlight ruby %}

<iframe
id="player"
width="958"
height="539"
src="https://www.youtube.com/embed/RQxxYJmF0cw"
title="YouTube video player"
frameborder="0"
allow="accelerometer; autoplay; clipboard-write; encrypted-media; gyroscope; picture-in-picture"
allowfullscreen>
</iframe>
 {% endhighlight %}

Before creating the javascript function there is one more step left to do for our HTML code and that is to add youtube API into our youtube link. The way we do it we add : `?enablejsapi=1` at the end of our youtube embedded link and that enables youtube API so we can have control over the iframe video. So, our final **HTML** code is going to be look like this:

{% highlight ruby %}

<iframe
id="player"
width="958"
height="539"
src="https://www.youtube.com/embed/RQxxYJmF0cw?enablejsapi=1"
title="YouTube video player"
frameborder="0"
allow="accelerometer; autoplay; clipboard-write; encrypted-media; gyroscope; picture-in-picture"
allowfullscreen>
</iframe>
 {% endhighlight %}

Notice how we added `?enablejsapi=1` at the end of source link.

\
**Creating JavaScript Function**

First thing we need to do when creating this function is to create Youtube Iframe API instance.

{% highlight ruby %}

var tag = document.createElement("script");
tag.src = "https://www.youtube.com/iframe_api";
var firstScriptTag = document.getElementsByTagName("script")[0];
firstScriptTag.parentNode.insertBefore(tag, firstScriptTag);

var player;
function onYouTubeIframeAPIReady() {
player = new YT.Player("player", {
events: {
onStateChange: onPlayerStateChange,
},
});
}
{% endhighlight %}


\
\
Once we have created Iframe API instance we now have access to video controls. We can now check video's status. And that is what the following function does. It checks the status of the player every time when status changes to keep the track of every single change with video player.

{% highlight ruby %}
function onPlayerStateChange(event) {
getPlayStatus(event.data);
}
{% endhighlight %}

\
\
Next function we need to create is the function that check if the player is in the viewport meaning if the player is visible on the screen 100%.

{% highlight ruby %}
function youtubeVideoViewPoint() {
const playerID = document.getElementById("player");
if (typeof jQuery === "function" && playerID instanceof jQuery)
playerID = playerID[0];
var rect = playerID.getBoundingClientRect();
if (
rect.top >= 0 &&
rect.bottom <=
(window.innerHeight + 1 || document.documentElement.clientHeight + 1)
) {
return true;
} else {
return false;
}
}
{% endhighlight %}

\
\
And lastly we need a function that checks if the player is playing at that moment and if it is 100% visible on the screen. If it is playing and player is not 100% visible on the screen it will pause the video.

{% highlight ruby %}
function getPlayStatus(playerStatus) {
	if (playerStatus === 1) {
		videoPause();
		document.addEventListener("scroll", videoPause);
	}

	
	function videoPause() {
		var inView = youtubeVideoViewPoint();
		if (!inView) player.pauseVideo();
	}
}
{% endhighlight %}

\
\
So, the final code will be this:

{% highlight ruby %}
//If iframe player is playing and user scrolls away player stops
var tag = document.createElement("script");
tag.src = "https://www.youtube.com/iframe_api";
var firstScriptTag = document.getElementsByTagName("script")[0];
firstScriptTag.parentNode.insertBefore(tag, firstScriptTag);

//Youtube iframe API
var player;
function onYouTubeIframeAPIReady() {
	player = new YT.Player("player", {
		events: {
			onStateChange: onPlayerStateChange,
		},
	});
}

//Gets the status of the player
function onPlayerStateChange(event) {
	getPlayStatus(event.data);
}

//Checks if player playing or stopped and adds event listener
function getPlayStatus(playerStatus) {
	if (playerStatus === 1) {
		videoPause();
		document.addEventListener("scroll", videoPause);
	}

	//Checks if player is in viewpoint and pauses video
	function videoPause() {
		var inView = youtubeVideoViewPoint();
		if (!inView) player.pauseVideo();
	}
}

//Checks if player is in view point
function youtubeVideoViewPoint() {
	const playerID = document.getElementById("player");
	if (typeof jQuery === "function" && playerID instanceof jQuery)
		playerID = playerID[0];
	var rect = playerID.getBoundingClientRect();
	if (
		rect.top >= 0 &&
		rect.bottom <=
			(window.innerHeight + 1 || document.documentElement.clientHeight + 1)
	) {
		return true;
	} else {
		return false;
	}
}

{% endhighlight %}