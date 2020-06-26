---
title: "How to Remove ads on spotify client windows"
date: 2020-06-26T10:40:08+07:00
draft: false
comments: true
---

hi guys, hope we safe. during this pandemic stay home its better and when staying home it will be nice while hearing music. if you using spotify but your premium subs has ended, here some trick to block a banner ads on spotify client windows pc (if you using linux i will be uumm give it to you too on below) and yeah the ads will be gone. <br> before we go i wanna say thanks to my bro Harry Elric on facebook for give me a clue about this. 

here some depedencies after we start the tutorial (you must install this first)
* [Scoop](https://scoop.sh/)
* curl (install using scoop, on power shell type this command scoop install curl)
* [spicetify](https://github.com/khanhas/spicetify-cli/wiki/Installation#with-powershell-pre-built-binary) 
<br>

and if you finish for installing three depedencies above lets follow this step.<br>
1. goto C:\Windows\System32\drivers\etc copy hosts file to another directory and open up host file then insert this line at the bottom
127.0.0.1			https://d5ecgvacntsb3.cloudfront.net <br>
127.0.0.1			https://www.spotify.com/premium?utm_source=Spotify_premiumupsell <br>
127.0.0.1			https://spclient.wg.spotify.com/ads/* <br>
127.0.0.1			https://spclient.wg.spotify.com/ad-logic/* <br>

as the result will be like this pict:
{{< image src="/remove_ads_spotify/1.PNG" alt="result" position="center" style="border-radius: 8px;" >}}<br>

2. and put back edited hosts file to C:\Windows\System32\drivers\etc just replace it!
3. goto powershell and type 
```
spicetify (hit enter)
spicetify backup apply enable-devtool
```
<br>

4. it will be open up a spotify, for example goto liked song and if you see banner ad just right click on it then select inspect element
{{< image src="/remove_ads_spotify/2.png" alt="Liked Song" position="center" style="border-radius: 8px;" >}} <br>

5. search this element (ctrl+f)
```
<div id="wiew-leaderboard-ad" 
and this
<div id="view-billboard-ad" class="billboard"
```
and delete that two things, just right click on the element then hit the delete element. like this pict :
for ```<div id="wiew-leaderboard-ad"```
{{< image src="/remove_ads_spotify/3.png" alt="wiew-leaderboard-ad" position="center" style="border-radius: 8px;" >}} <br>

and for ```<div id="view-billboard-ad" class="billboard"```
{{< image src="/remove_ads_spotify/4.png" alt="view-billboard-ad" position="center" style="border-radius: 8px;" >}}
<br>

6. yups, your done! the banner ads has been gone.. enjoy it!
{{< image src="/remove_ads_spotify/5.png" alt="ads gone!" position="center" style="border-radius: 8px;" >}}<br>

but you can still hearing the audio advertisement like:
{{< image src="/remove_ads_spotify/6.png" alt="audio ads" position="center" style="border-radius: 8px;" >}}<br>

7. if you close and open it again the ads will be back, to delete it again just repeat step number 5 ONLY!

yay, that how to remove ads without premium subs. its for education only, no anymore! and if you using a linux you can follow this [links](https://github.com/abba23/spotify-adblock-linux) also you can follow my tutorial tho. dont forget to leave comments if you wanna ask about this tutorial.