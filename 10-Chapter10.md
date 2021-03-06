# **Little Brother**

**Cory Doctorow**

**[doctorow@craphound.com](mailto:doctorow@craphound.com)**

**Chapter 10**

_This chapter is dedicated to Anderson's Bookshops, Chicago's legendary kids' bookstore. Anderson's is an old, old family-run business, which started out as an old-timey drug-store selling some books on the side. Today, it's a booming, multi-location kids' book empire, with some incredibly innovative bookselling practices that get books and kids together in really exciting ways. The best of these is the store's mobile book-fairs, in which they ship huge, rolling bookcases, already stocked with excellent kids' books, direct to schools on trucks -- voila, instant book-fair!_

_[Anderson's Bookshops](http://www.andersonsbookshop.com/search.php?qkey2=doctorow+little+brother&sid=5156&imageField.x=0&imageField.y=0): 123 West Jefferson, Naperville, IL 60540 USA +1 630 355 2665_

What would you do if you found out you had a spy in your midst? You could denounce him, put him up against the wall and take him out. But then you might end up with another spy in your midst, and the new spy would be more careful than the last one and maybe not get caught quite so readily.

Here's a better idea: start intercepting the spy's communications and feed him and his masters misinformation. Say his masters instruct him to gather information on your movements. Let him follow you around and take all the notes he wants, but steam open the envelopes that he sends back to HQ and replace his account of your movements with a fictitious one. If you want, you can make him seem erratic and unreliable so they get rid of him. You can manufacture crises that might make one side or the other reveal the identities of other spies. In short, you own them.

This is called the man-in-the-middle attack and if you think about it, it's pretty scary. Someone who man-in-the-middles your communications can trick you in any of a thousand ways.

Of course, there's a great way to get around the man-in-the-middle attack: use crypto. With crypto, it doesn't matter if the enemy can see your messages, because he can't decipher them, change them, and re-send them. That's one of the main reasons to use crypto.

But remember: for crypto to work, you need to have keys for the people you want to talk to. You and your partner need to share a secret or two, some keys that you can use to encrypt and decrypt your messages so that men-in-the-middle get locked out.

That's where the idea of public keys comes in. This is a little hairy, but it's so unbelievably elegant too.

In public key crypto, each user gets two keys. They're long strings of mathematical gibberish, and they have an almost magic property. Whatever you scramble with one key, the other will unlock, and vice-versa. What's more, they're the _only_ keys that can do this -- if you can unscramble a message with one key, you _know_ it was scrambled with the other (and vice-versa).

So you take either one of these keys (it doesn't matter which one) and you just _publish_ it. You make it a total _non-secret_. You want anyone in the world to know what it is. For obvious reasons, they call this your "public key."

The other key, you hide in the darkest reaches of your mind. You protect it with your life. You never let anyone ever know what it is. That's called your "private key." (Duh.)

Now say you're a spy and you want to talk with your bosses. Their public key is known by everyone. Your public key is known by everyone. No one knows your private key but you. No one knows their private key but them.

You want to send them a message. First, you encrypt it with your private key. You could just send that message along, and it would work pretty well, since they would know when the message arrived that it came from you. How? Because if they can decrypt it with your public key, it can _only_ have been encrypted with your private key. This is the equivalent of putting your seal or signature on the bottom of a message. It says, "I wrote this, and no one else. No one could have tampered with it or changed it."

Unfortunately, this won't actually keep your message a _secret_. That's because your public key is really well known (it has to be, or you'll be limited to sending messages to those few people who have your public key). Anyone who intercepts the message can read it. They can't change it and make it seem like it came from you, but if you don't want people to know what you're saying, you need a better solution.

So instead of just encrypting the message with your private key, you _also_ encrypt it with your boss's public key. Now it's been locked twice. The first lock -- the boss's public key -- only comes off when combined with your boss's private key. The second lock -- your private key -- only comes off with your public key. When your bosses receive the message, they unlock it with both keys and now they know for sure that: a) you wrote it and b) only they can read it.

It's very cool. The day I discovered it, Darryl and I immediately exchanged keys and spent months cackling and rubbing our hands as we exchanged our military-grade secret messages about where to meet after school and whether Van would ever notice him.

But if you want to understand security, you need to consider the most paranoid possibilities. Like, what if I tricked you into thinking that _my_ public key was your boss's public key? You'd encrypt the message with your private key and my public key. I'd decrypt it, read it, re-encrypt it with your boss's _real_ public key and send it on. As far as your boss knows, no one but you could have written the message and no one but him could have read it.

And I get to sit in the middle, like a fat spider in a web, and all your secrets belong to me.

Now, the easiest way to fix this is to really widely advertise your public key. If it's _really_ easy for anyone to know what your real key is, man-in-the-middle gets harder and harder. But you know what? Making things well-known is just as hard as keeping them secret. Think about it -- how many billions of dollars are spent on shampoo ads and other crap, just to make sure that as many people know about something that some advertiser wants them to know?

There's a cheaper way of fixing man-in-the-middle: the web of trust. Say that before you leave HQ, you and your bosses sit down over coffee and actually tell each other your keys. No more man-in-the-middle! You're absolutely certain whose keys you have, because they were put into your own hands.

So far, so good. But there's a natural limit to this: how many people can you physically meet with and swap keys? How many hours in the day do you want to devote to the equivalent of writing your own phone book? How many of those people are willing to devote that kind of time to you?

Thinking about this like a phonebook helps. The world was once a place with a lot of phonebooks, and when you needed a number, you could look it up in the book. But for many of the numbers that you wanted to refer to on a given day, you would either know it by heart, or you'd be able to ask someone else. Even today, when I'm out with my cell-phone, I'll ask Jolu or Darryl if they have a number I'm looking for. It's faster and easier than looking it up online and they're more reliable, too. If Jolu has a number, I trust him, so I trust the number, too. That's called "transitive trust" -- trust that moves across the web of our relationships.

A web of trust is a bigger version of this. Say I meet Jolu and get his key. I can put it on my "keyring" -- a list of keys that I've signed with my private key. That means you can unlock it with my public key and know for sure that me -- or someone with my key, anyway -- says that "this key belongs to this guy."

So I hand you my keyring and provided that you trust me to have actually met and verified all the keys on it, you can take it and add it to your keyring. Now, you meet someone else and you hand the whole ring to him. Bigger and bigger the ring grows, and provided that you trust the next guy in the chain, and he trusts the next guy in his chain and so on, you're pretty secure.

Which brings me to keysigning parties. These are _exactly_ what they sound like: a party where everyone gets together and signs everyone else's keys. Darryl and I, when we traded keys, that was kind of a mini-keysigning party, one with only two sad and geeky attendees. But with more people, you create the seed of the web of trust, and the web can expand from there. As everyone on your keyring goes out into the world and meets more people, they can add more and more names to the ring. You don't have to meet the new people, just trust that the signed key you get from the people in your web is valid.

So that's why web of trust and parties go together like peanut butter and chocolate.

\#

"Just tell them it's a super-private party, invitational only," I said. "Tell them not to bring anyone along or they won't be admitted."

Jolu looked at me over his coffee. "You're joking, right? You tell people that, and they'll bring _extra_ friends."

"Argh," I said. I spent a night a week at Jolu's these days, keeping the code up to date on indienet. Pigspleen actually paid me a non-zero sum of money to do this, which was really weird. I never thought I'd be paid to write code.

"So what do we do? We only want people we really trust there, and we don't want to mention why until we've got everyone's keys and can send them messages in secret."

Jolu debugged and I watched over his shoulder. This used to be called "extreme programming," which was a little embarrassing. Now we just call it "programming." Two people are much better at spotting bugs than one. As the cliche goes, "With enough eyeballs, all bugs are shallow."

We were working our way through the bug reports and getting ready to push out the new rev. It all auto-updated in the background, so our users didn't really need to do anything, they just woke up once a week or so with a better program. It was pretty freaky to know that the code I wrote would be used by hundreds of thousands of people, _tomorrow_!

"What do we do? Man, I don't know. I think we just have to live with it."

I thought back to our Harajuku Fun Madness days. There were lots of social challenges involving large groups of people as part of that game.

"OK, you're right. But let's at least try to keep this secret. Tell them that they can bring a maximum of one person, and it has to be someone they've known personally for a minimum of five years."

Jolu looked up from the screen. "Hey," he said. "Hey, that would totally work. I can really see it. I mean, if you told me not to bring anyone, I'd be all, 'Who the hell does he think he is?' But when you put it that way, it sounds like some awesome 007 stuff."

I found a bug. We drank some coffee. I went home and played a little Clockwork Plunder, trying not to think about key-winders with nosy questions, and slept like a baby.

\#

Sutro baths are San Francisco's authentic fake Roman ruins. When it opened in 1896, it was the largest indoor bathing house in the world, a huge Victorian glass solarium filled with pools and tubs and even an early water slide. It went downhill by the fifties, and the owners torched it for the insurance in 1966\. All that's left is a labyrinth of weathered stone set into the sere cliff-face at Ocean Beach. It looks for all the world like a Roman ruin, crumbled and mysterious, and just beyond them is a set of caves that let out into the sea. In rough tides, the waves rush through the caves and over the ruins -- they've even been known to suck in and drown the occasional tourist.

Ocean Beach is way out past Golden Gate park, a stark cliff lined with expensive, doomed houses, plunging down to a narrow beach studded with jellyfish and brave (insane) surfers. There's a giant white rock that juts out of the shallows off the shore. That's called Seal Rock, and it used to be the place where the sea lions congregated until they were relocated to the more tourist-friendly environs of Fisherman's Wharf.

After dark, there's hardly anyone out there. It gets very cold, with a salt spray that'll soak you to your bones if you let it. The rocks are sharp and there's broken glass and the occasional junkie needle.

It is an awesome place for a party.

Bringing along the tarpaulins and chemical glove-warmers was my idea. Jolu figured out where to get the beer -- his older brother, Javier, had a buddy who actually operated a whole underage drinking service: pay him enough and he'd back up to your secluded party spot with ice-chests and as many brews as you wanted. I blew a bunch of my indienet programming money, and the guy showed up right on time: 8PM, a good hour after sunset, and lugged the six foam ice-chests out of his pickup truck and down into the ruins of the baths. He even brought a spare chest for the empties.

"You kids play safe now," he said, tipping his cowboy hat. He was a fat Samoan guy with a huge smile, and a scary tank-top that you could see his armpit- and belly- and shoulder-hair escaping from. I peeled twenties off my roll and handed them to him -- his markup was 150 percent. Not a bad racket.

He looked at my roll. "You know, I could just take that from you," he said, still smiling. "I'm a criminal, after all."

I put my roll in my pocket and looked him levelly in the eye. I'd been stupid to show him what I was carrying, but I knew that there were times when you should just stand your ground.

"I'm just messing with you," he said, at last. "But you be careful with that money. Don't go showing it around."

"Thanks," I said. "Homeland Security'll get my back though."

His smile got even bigger. "Ha! They're not even real five-oh. Those peckerwoods don't know nothin'."

I looked over at his truck. Prominently displayed in his windscreen was a FasTrak. I wondered how long it would be until he got busted.

"You got girls coming tonight? That why you got all the beer?"

I smiled and waved at him as though he was walking back to his truck, which he should have been doing. He eventually got the hint and drove away. His smile never faltered.

Jolu helped me hide the coolers in the rubble, working with little white LED torches on headbands. Once the coolers were in place, we threw little white LED keychains into each one, so it would glow when you took the styrofoam lids off, making it easier to see what you were doing.

It was a moonless night and overcast, and the distant streetlights barely illuminated us. I knew we'd stand out like blazes on an infrared scope, but there was no chance that we'd be able to get a bunch of people together without being observed. I'd settle for being dismissed as a little drunken beach-party.

I don't really drink much. There's been beer and pot and ecstasy at the parties I've been going to since I was 14, but I hated smoking (though I'm quite partial to a hash brownie every now and again), ecstasy took too long -- who's got a whole weekend to get high and come down -- and beer, well, it was all right, but I didn't see what the big deal was. My favorite was big, elaborate cocktails, the kind of thing served in a ceramic volcano, with six layers, on fire, and a plastic monkey on the rim, but that was mostly for the theater of it all.

I actually like being drunk. I just don't like being hungover, and boy, do I ever get hungover. Though again, that might have to do with the kind of drinks that come in a ceramic volcano.

But you can't throw a party without putting a case or two of beer on ice. It's expected. It loosens things up. People do stupid things after too many beers, but it's not like my friends are the kind of people who have cars. And people do stupid things no matter what -- beer or grass or whatever are all incidental to that central fact.

Jolu and I each cracked beers -- Anchor Steam for him, a Bud Lite for me -- and clinked the bottles together, sitting down on a rock.

"You told them 9PM?"

"Yeah," he said.

"Me too."

We drank in silence. The Bud Lite was the least alcoholic thing in the ice-chest. I'd need a clear head later.

"You ever get scared?" I said, finally.

He turned to me. "No man, I don't get scared. I'm always scared. I've been scared since the minute the explosions happened. I'm so scared sometimes, I don't want to get out of bed."

"Then why do you do it?"

He smiled. "About that," he said. "Maybe I won't, not for much longer. I mean, it's been great helping you. Great. Really excellent. I don't know when I've done anything so important. But Marcus, bro, I have to say. . ." He trailed off.

"What?" I said, though I knew what was coming next.

"I can't do it forever," he said at last. "Maybe not even for another month. I think I'm through. It's too much risk. The DHS, you can't go to war on them. It's crazy. Really actually crazy."

"You sound like Van," I said. My voice was much more bitter than I'd intended.

"I'm not criticizing you, man. I think it's great that you've got the bravery to do this all the time. But I haven't got it. I can't live my life in perpetual terror."

"What are you saying?"

"I'm saying I'm out. I'm going to be one of those people who acts like it's all OK, like it'll all go back to normal some day. I'm going to use the Internet like I always did, and only use the Xnet to play games. I'm going to get out is what I'm saying. I won't be a part of your plans anymore."

I didn't say anything.

"I know that's leaving you on your own. I don't want that, believe me. I'd much rather you give up with me. You can't declare war on the government of the USA. It's not a fight you're going to win. Watching you try is like watching a bird fly into a window again and again."

He wanted me to say something. What _I_ wanted to say was, _Jesus Jolu, thanks so very much for abandoning me! Do you forget what it was like when they took us away? Do you forget what the country used to be like before they took it over?_ But that's not what he wanted me to say. What he wanted me to say was:

"I understand, Jolu. I respect your choice."

He drank the rest of his bottle and pulled out another one and twisted off the cap.

"There's something else," he said.

"What?"

"I wasn't going to mention it, but I want you to understand why I have to do this."

"Jesus, Jolu, _what_?"

"I hate to say it, but you're _white_. I'm not. White people get caught with cocaine and do a little rehab time. Brown people get caught with crack and go to prison for twenty years. White people see cops on the street and feel safer. Brown people see cops on the street and wonder if they're about to get searched. The way the DHS is treating you? The law in this country has always been like that for us."

It was so unfair. I didn't ask to be white. I didn't think I was being braver just because I'm white. But I knew what Jolu was saying. If the cops stopped someone in the Mission and asked to see some ID, chances were that person wasn't white. Whatever risk I ran, Jolu ran more. Whatever penalty I'd pay, Jolu would pay more.

"I don't know what to say," I said.

"You don't have to say anything," he said. "I just wanted you to know, so you could understand."

I could see people walking down the side trail toward us. They were friends of Jolu's, two Mexican guys and a girl I knew from around, short and geeky, always wearing cute black Buddy Holly glasses that made her look like the outcast art-student in a teen movie who comes back as the big success.

Jolu introduced me and gave them beers. The girl didn't take one, but instead produced a small silver flask of vodka from her purse and offered me a drink. I took a swallow -- warm vodka must be an acquired taste -- and complimented her on the flask, which was embossed with a repeating motif of Parappa the Rapper characters.

"It's Japanese," she said as I played another LED keyring over it. "They have all these great booze-toys based on kids' games. Totally twisted."

I introduced myself and she introduced herself. "Ange," she said, and shook my hand with hers -- dry, warm, with short nails. Jolu introduced me to his pals, whom he'd known since computer camp in the fourth grade. More people showed up -- five, then ten, then twenty. It was a seriously big group now.

We'd told people to arrive by 9:30 sharp, and we gave it until 9:45 to see who all would show up. About three quarters were Jolu's friends. I'd invited all the people I really trusted. Either I was more discriminating than Jolu or less popular. Now that he'd told me he was quitting, it made me think that he was less discriminating. I was really pissed at him, but trying not to let it show by concentrating on socializing with other people. But he wasn't stupid. He knew what was going on. I could see that he was really bummed. Good.

"OK," I said, climbing up on a ruin, "OK, hey, hello?" A few people nearby paid attention to me, but the ones in the back kept on chatting. I put my arms in the air like a referee, but it was too dark. Eventually I hit on the idea of turning my LED keychain on and pointing it at each of the talkers in turn, then at me. Gradually, the crowd fell quiet.

I welcomed them and thanked them all for coming, then asked them to close in so I could explain why we were there. I could tell they were into the secrecy of it all, intrigued and a little warmed up by the beer.

"So here it is. You all use the Xnet. It's no coincidence that the Xnet was created right after the DHS took over the city. The people who did that are an organization devoted to personal liberty, who created the network to keep us safe from DHS spooks and enforcers." Jolu and I had worked this out in advance. We weren't going to cop to being behind it all, not to anyone. It was way too risky. Instead, we'd put it out that we were merely lieutenants in "M1k3y"'s army, acting to organize the local resistance.

"The Xnet isn't pure," I said. "It can be used by the other side just as readily as by us. We know that there are DHS spies who use it now. They use social engineering hacks to try to get us to reveal ourselves so that they can bust us. If the Xnet is going to succeed, we need to figure out how to keep them from spying on us. We need a network within the network."

I paused and let this sink in. Jolu had suggested that this might be a little heavy -- learning that you're about to be brought into a revolutionary cell.

"Now, I'm not here to ask you to do anything active. You don't have to go out jamming or anything. You've been brought here because we know you're cool, we know you're trustworthy. It's that trustworthiness I want to get you to contribute tonight. Some of you will already be familiar with the web of trust and keysigning parties, but for the rest of you, I'll run it down quickly --" Which I did.

"Now what I want from you tonight is to meet the people here and figure out how much you can trust them. We're going to help you generate key-pairs and share them with each other."

This part was tricky. Asking people to bring their own laptops wouldn't have worked out, but we still needed to do something hella complicated that wouldn't exactly work with paper and pencil.

I held up a laptop Jolu and I had rebuilt the night before, from the ground up. "I trust this machine. Every component in it was laid by our own hands. It's running a fresh out-of-the-box version of ParanoidLinux, booted off of the DVD. If there's a trustworthy computer left anywhere in the world, this might well be it.

"I've got a key-generator loaded here. You come up here and give it some random input -- mash the keys, wiggle the mouse -- and it will use that as the seed to create a random public- and private key for you, which it will display on the screen. You can take a picture of the private key with your phone, and hit any key to make it go away forever -- it's not stored on the disk at all. Then it will show you your public key. At that point, you call over all the people here you trust and who trust you, and _they_ take a picture of the screen with you standing next to it, so they know whose key it is.

"When you get home, you have to convert the photos to keys. This is going to be a lot of work, I'm afraid, but you'll only have to do it once. You have to be super-careful about typing these in -- one mistake and you're screwed. Luckily, we've got a way to tell if you've got it right: beneath the key will be a much shorter number, called the 'fingerprint'. Once you've typed in the key, you can generate a fingerprint from it and compare it to the fingerprint, and if they match, you've got it right."

They all boggled at me. OK, so I'd asked them to do something pretty weird, it's true, but still.
