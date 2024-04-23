---
layout: post
title:  "Phones are a Nightmare"
date:   2024-04-14
categories: ["Shatterstone"]
author: "Mike Tintes"
---

[Last time](https://anmtblog.com/shatterstone/2024/04/07/Shatterstone1.html) we talked about what Project Shatterstone is all about so this time we will talk about something a little more interesteing. Forewarning, I can't guarantee there won't be spoilers, but as I don't have any puzzles drawn out yet and am still designing so outside of revealing the mechanism/tech I hid the puzzle in I think it should be ok. 

Anyway, let's talk about the hellish nightmare that is phones!

A few years ago before Shatterstone, I was sitting around thinking about weird halloween props and was thinking it would be spooky to have a phone that would ring at random. The person might pick up the phone to get a mysterious or scary message. And how spooky would it be if you physically picked up the phone and discovered there was no wire to the wall? So I bought a phone and I stripped all the guts out of it and wired in a raspberry pi. But I never finished it, because phones as it turns out are way tougher than I expected.

Warning: phones are actually dangerous AF so don't just go poking. There area couple very high voltage capacitors in there.

When you open up a phone some stuff is obvious and some stuff isn't. The receiver, the thing you listen and talk to is pretty simple two wires go to the speaker at the top, two go to the microphone at the bottom. You will notice that there is a swtich that gets pushed closed when you put the reciever on it. This is called the hook, thus you 'leave the phone off the hook'. You'll see a couple bells, one bigger than the other, and finally you will see a dial pad with some other boards in there. Pretty simple right?

I am a pretty simple mind when it comes to engineering problem solving. I establish some goal, in this case I want to be able to dial numbers and have the phone ring. I always try to get some little win first, then work my way up to tougher stuff. The reciever seemed like a good idea. Well, just the top half of the reciever really with the audio out. So I bought a rpi3 with and audio hat and I started snipping wires. I found the right wires pretty quick and so boom first task complete. Task 2 was to figure out the hook. The switch for the hook was soldered directly to the board running the phone so I knew that wouldn't work. So I threw a CAD project together and mounted a cherry switch to replace the old switch and wired that to the pi. Couple of quick wins right off the bat and it was going smooth, but then....

People are funny. We have things that we just know. Like cut a piece of paper in the same shape as a dollar and ask someone to close their eyes and find it in a stack of bills. Then spend months on differnt kinds of paper. They will always be able to pick it out. We have touched money our whole life. Well, dialtones are the same way. Off by a pitch? People will know. Dialtones are not just a single tone, they are actually a combination of 2 tones together. 






First, phonelines don't work on your home power. If you had a home line and your power went out, then you can still make a phone call. That is because phones are powered at the source. In this case the phone company or an intermediary. This has a lot to do with how phones started and well it worked so we didn't need more. Doesn't mean that you didn't need to plug your phone in, but really you only needed to do that for the extra stuff on the phone (lcd screen etc). OK, that is the generic history of phones. Let's keep moving since that isn't going to move us forward much. 


