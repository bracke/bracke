---
layout: post
title: HoMMII on OSX Mountain Lion
categories: gaming
---
One of the best computer games I have ever played is Heroes of Might and Magic 2 - yes - 2 - not version 5 or 6.
I played it and the expansion pack "Prize of Loyalty" on my Acorn RISC PC for a long time.
[//]: #
I have also tried newer versions but they somehow don't seem as good. Although HoMM3 and HoMM5 were ok.
<br><br>
My main computer is now a MacBookPro and I decided to try to make HoMM2 run on that machine. Amazingly I got it going and it was surprisingly simpel. The following is a recipe for getting HoMM2 running on your OSX machine.<br>


<h3>Prerequisites</h3>
<ul>
<li>The HoMM2 disc or a copy of it.<br>I copied the disc using DiscUtility and simply mount the ISO file every time I want to play.</li>
<li>Wineskin - This utility is used to create a wrapper around the HoMM2 Windows program to make it run on your Mac. You can get it <a href="http://wineskin.urgesoftware.com/tiki-index.php?page=Downloads" target="_blank">here</a>.</li>
</ul>
<br>

<h3>Creating the HoMM2 wrapper</h3>

The following recipe will create a HoMM2 wrapper application which will run HoMM2 using the Wine Windows "emulator".<br>
<ul>
<li>Run the WineSKin Winery app, You will be prompted to select an engine and a wrapper version - simply select the newest ones.</li>
<li>Click on "Create new blank wrapper", this creates a new app in a Wineskin subfolder of your application folder.</li>
<li>Run the app you have just created - this opens a small window with 4 buttons.</li>
<li>Click on the "Install software" button and choose the setup.exe on the HoMM2 CD and start the install. <br>The install will work like it would on a PC</li>
<li>Now click on the second button ("Set Screen Options") and select "Override" instead of "Automatic" and "Rootless (windowed)" instead of "Fullscreen" and click "Done".</li>
<li>Click the third button to get to the advanced options section. Make sure the path to the HoMM2 exe file is correct and is on your harddisc and not on the CD.</li>
<li>Select the tools tab and click on the "Config utility" button.</li>
<li>Select the "Applications" tab and set the "Windows Version" to "Windows 98" and click on "OK".</li>
</ul>
<br>
Now you should have a working version of HoMM2! Click on "Test Run" in the "Advanced"tab to confirm it.
<br>