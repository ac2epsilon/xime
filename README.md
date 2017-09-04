# xime
WE BYTE YOUR TIME!

Xlock: new approach to think about time

Terminology

We use X letter to denote everything related to heX (i.e. Hexadecimal) Clock. For example: xime(our time), xlock(our clock), xour(our hour), xinute(our minute). This approach let us not to juggle terms like our hour, old hour, those minutes etc.

Intention

Main intention of xlock is invent smart, reasonable, convenient and logical way shrink time-of-the-day into 1 byte (8 bits), without sacrificing practical usability for 95% of use cases.

Invariants

Invariant is something, which is not changing relating to given operation. For example, orthogonal vectors will be still orthogonal after rotation in space, while some other space deformation can change this relation between them. So xime invariants are:

- Day and night are still day and night. I.e. whole day consists of two equal parts: night&morning and day&evening in such order (thank the Lord!).

- Second remains same second in SI meaning, i.e. periods of radiation blah-blah-blah.This is not the part of minute or hour.

- Also number of seconds in the day still remains, and equal to 60*60*24= 86400 seconds in a whole day.

- We discuss time-of-the-day only. All about years, months and weeks, including any corrections, additional seconds and leap years out of our scope and all of them stay unchanged.

What in xlock is changed?

- Second NOT a part of a minute any more, hour or whatever else. Actually xime have NO hours and minutes, but xours and xinutes instead (as mentioned above X stands for heX, which is 16).

- Whole day consists of 16 xours, each xour consists of 16 xinutes.

- ATTENTION! One xinute consists of different number of seconds. There are short xinute = 225 seconds (3 min 45 sec) and long xinute = 675 seconds (11 min 15 sec). As xour always equals 16 xinutes, there are short xours = 225*16=3600 seconds (which is one old plain hour) and long xour = 10800 seconds (3 former hours).

- Long xours used to represent xime from 0:00 to 6:00 and from 12:00 to 18:00. So in these "slow" zones xinute arm ticks one time in 11 min 45 sec. 
Other time xinute arm ticks every 3 min 45 sec. As you can count night is TWO xours long (instead of six hours) and day is TWO xours long (instead of six hours). This just reflects the fact: morning and evening time is far most important in meaning of time resolution then night and afternoon! (We talk about usual people in usual situations. AND you always have seconds to be more specific)

Notation and implementation


Little discussion

- in these "slow" zones xinute arm ticks one time in 11 min 45 sec. Yes. But really, who cares? Even taking your dinner was from 13:00 to 14:00, now it will be 8x5 (12:56:15) to 8xB (14:03:45). Your business is totally ill-screwed if such change can kill it.

- And what if I want more resolution? Give me seconds back! Ahhh! Uhm.. you have seconds all the time. For example 8xA:450 means 2PM o'clock.

- What the hell with those short xinutes. Well, it's just very simple and convenient way to divide whole day into 16 peaces. If you just divide 86400 seconds by 256 you get 337.5, it's something 5 min 37.5 seconds, which is not fun at all. And plus we feel it's too good resolution for the night and bad resolution for the morning. We also discussed approach with three xinute resolutions - 1 xour for the night, 3 for the day, and 6 for morning and evening, but we decided to make night and day symmetric. And 23+ min for the tick looks too poor resolution even for night time.   

Why this is so important?

There are several reasons to snap for new xlock:

- historical: for what on the Earth do we count to 60 minutes? Yes, I know the answer. Because in such "elegant" way you can divide one hour into three equal parts. And what? Do you say "one third past two"? Nope. We have the complication with no reason. 

- perceptual: do you really think in meaning of minutes? Especially in the night. Do you think "Sonny, you must be at home at 1:23:06". Ups. You rather say "Be at home not too late". And even 11 min resolution is great to explain what those late means.

- economical: how many petabytes of databases do filled with dates, times, data-and-times and things like this? And what bytes do it costs? For example your day-of-the-birth may be written as Oct/2/1994 12:06:40AM. 10 bytes for time with zero relevance. Who cares you may ask. Count on 7 billions persons and on some 100 database entries for every one. But not only this: transactions, inventory, logs (especially logs). And try imaginary replace every time stamp to 1 byte. You will get profit.
- practical: look, you see at clock and see something like 12:33:45AM. Good. And what? Compare to x000 00xx or even 8x3. I guarantee, for this simplicity you will xnow and xlove new xlock in one day!

- informational: how do you think, how many bits refers to AM and PM? Yes, just one. Exactly what xlock offers. First bit says: 0 is AM, 1 is PM. One bit instead, well, two ASCII codes (16 bits if you lucky). Every xour after 8x means PM, okay? It was easy. And 1 byte completely used in every bit. Your CPU will thank you.    

