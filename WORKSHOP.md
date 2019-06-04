# Max 8 Beginner Workshop

Hi. This is an up-and-running workshop about Max 8, the visual programming language for music and multimedia. It does not assume any knowledge of Max, but it also moves at a relatively fast pace. Hopefully, this will inspire new users, but also give seasoned pros some new reasons to explore the newest version of Max. Instead, it might simply be the wrong fit for everyone. The advantage of being a github repo is that we can always make it better later.

## What is Max 8

Max 8 is a visual programming language. That means that instead of writing lines of code, you connect together functional blocks called objects. Some people find this a more intuitive way to describe the kinds of computation common to interactive, multimedia systems. Max is especially good for trying out new ideas, and for connecting together different forms of input and output, like video to audio, or gesture to video.

The fundamental rule of Max—and indeed computer art in general—is that anything can be turned into a number, and numbers can be turned into anything else. As you can imagine, this is a very large creative space.

## What can you do with Max?

People use Max for all kinds of things. Some especially popular projects include audio-reactive visuals, new musical instruments, and live electronics. Here's a smattering of some cool stuff:

- https://www.youtube.com/watch?v=U9v-4VrSglE Leafcutter John is a musician working with Max. This piece uses a number of light sensors, along with some flashing handheld lights, to create a new musical instrument.
- https://www.youtube.com/watch?v=gvUpkknryaY Daito Manabe is an artist working on installations, compositions, and choreography, using as many new technologies as possible. Particles is a piece that uses Max to map the positions of a number of rolling physical components to various sound events.
- https://www.youtube.com/watch?v=BXlaSBo0KXs This piece, written for the reopening of the St. Pauli Elbtunnel in Hamburg, uses Max to coordinate the performance of 144 musicians all along the length of the tunnel.

## Getting started

Let's start by opening up Max. When you do that, you'll be greeted by this big blank canvas. You can do anything you want! So what should we do?

First, let's make a button. You can press b to make a button. Drag the button around to reposition it. Normally, this is the place where I talk about locking and unlocking the patch. You lock the patch to press the button, and unlock it to drag the button around. In Max 8 there's a swanky new feature called "Operate While Unlocked." In this mode, you hold down shift when you want to drag stuff around. It's totally up to you which one you want to use. 

Cool let's do something with that. Make an object called [random 50]. You press n to make a new object. This generates random numbers between 0 and 50. Now let's make an integer box. Press i to make this. Connect them all up. Now you can push the button to get a random number.

Let's also go up into the Debug menu and turn on Event Probe and Signal Probe. These will make our lives much easier later. You can hover over patchcords to see the most recent message that they sent.

Okay, let's do something with these random numbers. Let's hear some freaking sound already. Make an object called tri~. This is an oscillator, it generates an antialised triangle wave. Now make a floating point box (press f) and connect it to the tri~ object. Now let's make a scope~ (all of the objects that handle audio have yellow patch cables and are followed by the tilde) and connect it. Finally, turn on DSP by clicking on the little control in the bottom-right. You should see a wave displayed in the scope~. You can activate automatic mode, which may make it look better, but you might not be able to see when the frequency changes since the scope will adjust automatically.

Now connect the random number generator to the frequency box, and let's make some random frequencies. It doesn't work!? How come? Or at least, it sounds very low. Why is that? Let's fix it by converting MIDI to frequency. We can find the objec that does that by using search, which is way better in Max 8 than it was in other versions of Max.

Next we can add a kslider, which will let us pick a note in some way other than randomly.

## Spreading tones, making textures.

Up to now, this is more or less where a lesson teaching Max 7 would have gone. Now we get to depart radically from that and do some really cool stuff. First, we gotta change some of the objects in our original patch into multichannel objects. So all of the objects that end with ~ are audio objects. If you prefix any of these with mc., they become multichannel audio objects. They will use bright blue patch cords, which can handle any number of channels.

You'll also need an mc.stereo~. Don't forget autogain, and don't forget the signal~ for pan. You might want to save this as a snippet, which can be handy.

Okay, now we can add the @chans attribute to tri~, which lets us specify how many channels of audio we want. Let's start with @chans 8. Now try sending the following messages:

"increment 75 220"
"harmonic 0.1 330"
"harmonic 1 55"
"deviate 50 330"

What do they sound like? Each of these creates a different distribution of frequencies 