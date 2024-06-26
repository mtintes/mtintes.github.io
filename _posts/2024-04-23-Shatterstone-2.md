---
layout: post
title:  "Phones are a Nightmare 1" 
date:   2024-04-23
categories: ["Shatterstone"]
author: "Mike Tintes"
---

[Last time](https://anmtblog.com/shatterstone/2024/04/07/Shatterstone1.html) we talked about what Project Shatterstone is all about so this time we will talk about something a little more interesting. Forewarning, I can't guarantee there won't be spoilers, but as I don't have any puzzles drawn out yet and am still designing so outside of revealing the mechanism/tech I hid the puzzle in I think it should be ok. 

Anyway, let's talk about the hellish nightmare that is phones!

A few years ago before Shatterstone, I was sitting around thinking about weird halloween props and was thinking it would be spooky to have a phone that would ring at random. A person might pick up the phone to get a mysterious or scary message. We could kick up the spookiness even more if they physically picked up the phone and discovered there was no wire to the wall? So I bought a phone and I stripped all the guts out of it and wired in a raspberry pi. But I never finished it, because phones as it turns out are way tougher than I expected.

Warning: phones are actually dangerous AF so don't just go poking around. There are a couple very high voltage capacitors in there.

When you open up a phone some stuff is obvious and some stuff isn't. The receiver, the thing you listen and talk to is pretty simple two wires go to the speaker at the top, two go to the microphone at the bottom. You will notice that there is a swtich that gets pushed closed when you put the receiver on it. This is called the hook, thus you 'leave the phone off the hook'. You'll see a couple bells, one bigger than the other, and finally you will see a dial pad with some other boards in there. Pretty simple right?

I am a pretty simple mind when it comes to engineering problem solving. I establish some goal, in this case I want to be able to dial numbers and have the phone ring, then pick a place to start. I always try to get some little win first, then work my way up to tougher stuff. The receiver seemed like a good starting point. Well, just the top half of the reciever really, namely the audio out. So, I bought a rpi3 with an audio hat and I started snipping wires. I found the right wires pretty quick and so screwed them to a 3.5mm terminal and boom, first task complete. Task 2 was to figure out the hook. The switch for the hook was soldered directly to the board running the phone so I knew that wouldn't work. So I threw a CAD project together and mounted a cherry switch to replace the old switch and wired that to the pi. Couple of quick wins right off the bat and it was going smooth, but then....

People are funny. We have things that we just know. Like cut a piece of paper in the same shape as a dollar and ask someone to close their eyes and find it in a stack of bills. You could spend months trying differnt kinds of paper and they will always be able to pick it out. We have touched money our whole life so everyone just knows what that feels like. Well, phone noises are the same way. Off by a pitch? People will know. Phone tones are not just a single tone, they are actually a combination of 2 tones together. Their official definition is Dual Tone Multi Frequency (DTMF). If you dial a number 1 for instance that is 697Hz mixed with 1209Hz. Pretty simple! The trick comes down to how you write software to do this. I am not a Python expert. I admit I would do just about anything to avoid that snake. I tried writing this program in JS and Go before I gave in. I was loosing time and interest, so I dived in.

When trying to make a phone work like a phone you have to think of it more like a music track than a bunch of individual noises. A oerson could leave the phone off the hook for any amount of time. The same with dialing numbers at any speed and order. So I found a python library that would allow me to generate a stream and then I could just alter the audio. Beep Bop Boop, a little garbage code later and I had the audio streaming<sup>1</sup>. Then the number pad. That was a little trickier cuz I was unaware at the time that to save some wires they set up a little matrix. A number pad on a phone looks a little like:

|1|2|3|
|-|-|-|
|4|5|6|
|7|8|9|
|*|0|#|

This means that there are 4 rows (4 wires) and 3 columns (3 wires) so 7 wire can represent 12 numbers instead of 24 (positive and negative) wires. I wired all the rows and columns to the respective outputs (honestly I can't remember exactly how) and that was working as well. The code is a mess, but if you want it then you can find it [here](https://github.com/mtintes/phone/blob/master/phone_run.py). And after all that, I only had/have one problem left, getting the bloody bells to ring. You see, of all the things on a phone that require just the right amount of precision it is the bells. These can vary in their setup, but for my phone there is a small actuator inset into each bell. When you put current through one end it strikes the one side, and vice versa. This is what causes the phone to ring, but since most phones don't really have a brain this has to happen on a circuit that can occilate. You also need a lot of power to do so as far as I am aware. It might be possible to do what I need in the sorftware, but honestly I found a much easier way with dealing with phones overall. 

Now maybe you are wondering why I even touched on theis since it has little to do with Shatterstone. Well, knowledge is a very funny thing. The more I learn, the more I find that knowing anything leads to learning something else. I think that this project was the first inkling I had towards something bigger. It truely took me a ton of time to get anywhere on it, but it also taught me to keep pushing and take little steps towards the bigger goal.

So anyway, that's where we leave it for now. We will come back to phones and a much more robust solution soon.

Take care!

---

<sup>1</sup>I say "a little garbage code later", but what I mean is countless weeks of trial and error and giving up and trying again.
