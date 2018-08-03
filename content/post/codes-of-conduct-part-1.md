---
title: Of Codes and Conduct
date: 2018-08-03
---

_This is the first post in a 3 part series. Part 1 introduces CoCs and why they’re contentious, part 2 explains the problems they attempt to solve, and part 3 suggests some steps we can take to bury the hatchet._

There’s a war going on in open source right now. It’s been easy to miss because it doesn’t rage continuously; battles flare up sporadically, every 6 months or so. But what they lack in frequency, they make up for in intensity.

The instigator of these uncivil outbursts? Ironically, Codes of Conduct.

I’ll soon get into what this feud is all about, but first — let’s establish the vocabulary. What is a Code of Conduct? I’m partial to the definition from [this great article](https://techcrunch.com/2016/03/05/how-we-may-mesh/).

> Codes of Conduct boil down to: “a) don’t be an asshole, b) this is how we define ‘asshole’ around these parts”.

If you’re only a member of one or two open-source communities, you may have even seen a flare-up and thought it was an isolated incident. Unfortunately, it’s not, and to those of us paying attention, each battle is depressingly similar. Step one, a community grows to the point that it sees the need for some degree of moderation. Step two, the community leaders devise some rules and system of moderation in the form of a Code of Conduct, or CoC for short. Step three, they announce it to the community and then — the battle begins.

For the Go community, the story started back in 2015 with [a thread on the mailing list](https://groups.google.com/forum/#!msg/golang-nuts/sy-YcVPADjg/bcO6LAr29EIJ) that the project had gotten large enough to possibly benefit from a code of conduct. This prompted the first battle. A few months of research and discussion cuminated in [a formal proposal](https://github.com/golang/proposal/blob/master/design/13073-code-of-conduct.md), and with the specifics the battle resumed. After many loud noises were made, the proposal was eventually accepted with one major change that is called out in the FAQ of the final draft.

> Is behavior outside Go spaces covered by this CoC? An earlier draft of this proposal included a clause that behavior outside Go spaces may affect one’s ability to participate within them. After much community feedback, I removed the clause. It was seen as unnecessarily overreaching and as providing an opportunity for malicious people to oust community members for their behavior unrelated to Go.

Some people were ok with this compromise and many weren’t. Even after it was scaled back, those against CoCs had been shown the hard truth that the Go’s core maintainers didn’t agree with them. That disillusionment was probably for the best and we were all happy to put the fighting behind us and get back to working together. Fast forward two and a half years; It’s may 2018 and the core team just released [this blog post](https://blog.golang.org/conduct-2018) announcing changes to the code of conduct, most notably, extending the scope back to non-official spaces as was the case in the early drafts of the first proposal. Of course, the battle resurrected itself, but with a different tone. The rationale for these changes was clearly outlined in the blog post, and discussions had been had within the internal Go team, but the wider community was not consulted or included in the decision making process this time around. Many saw this as a imposition of Google’s corporate culture on the community and some threatened to leave the community over it. Even those who weren’t as opposed to CoCs were concerned that such a contentious change had been made behind closed doors. On the other hand, we had seen how disruptive the public debate had been last time, and that wasn’t great either. Including the community didn’t make the issue any less disruptive or contentious, and it resulted in a compromise that ultimately didn’t work.

This is but one example in one community, but a version of this has played out in almost every large project that has adopted a CoC. I tell this particular story because it is what inspired me to pen these posts. I believe these discussions are worth having, but every time we try, they never end in any kind of consensus. It’s not even clear that we’re making progress, nevermind approaching resolution. Moving discussion behind closed fixes some problems but replaced them with others. What will we do the next time the CoC needs to be updated? I asked myself, is there a way that we could have this dialog without all the drama?

Let’s take a step back. We’ve all been in online forums with moderation rules. Why would an open source project adopting similar rules be so controversial? For one, the stakes are higher in open source, where being excluded from a project or community could seriously damage a person’s career. And then there’s the bigger problem of trying to define what makes someone a “bad person.” Traits that some see as actively harmful, others see as beneficial.

To see this in action, ask a room of programmers what they think about the leadership style of Linus Torvalds, the BDFL (benevolent dictator for life) of Linux. Linus speaks his mind, and when someone tries to push questionable code into the Linux kernel, he makes it painfully clear exactly how terrible he thinks it is. In some cases, he even goes as far as publicly berating the person who submitted the patch. There are plenty of examples, but I’ll pull a few quotes from [this message](https://lkml.org/lkml/2012/12/23/75) to give you a taste.

> Mauro, SHUT THE FUCK UP!

<!-- -->

> Shut up, Mauro. And I don't _ever_ want to hear that kind of obvious garbage and idiocy from a kernel maintainer again. Seriously.

<!-- -->

> Fix your f\*cking "compliance tool", because it is obviously broken. And fix your approach to kernel programming.

It’s one thing to constructively criticize code, but this criticism is clearly not constructive. Most of us would say that this goes too far. Some would even say **way** too far. Others are idly wondering why Linus censored “f\*cking” but not “FUCK”. But the wisest among us will ask to hear the whole story, since it’s easy to take quotes out of context to make someone look like a dick. So let’s consider some of the other things Linus said in this message.

<!-- -->

> How long have you been a maintainer? And you _still_ haven't learnt the first rule of kernel
> maintenance?
>
> If a change results in user programs breaking, it's a bug in the kernel. We never EVER blame the user programs. How hard can this be to understand?

<!-- -->

> WE DO NOT BREAK USERSPACE!

<!-- -->

> The fact that you then try to make _excuses_ for breaking user space, and blaming some external program that _used_ to work, is just shameful. It's not how we work.

With the context added, the picture gets a bit muddier. We see a project leader standing his ground to protect the all the downstream users and developers that rely on Linux from unnecessary breakage. More importantly, they show Linus trying to instill an important core value into the kernel development community. Not breaking userspace is critical to the continued success of Linux, and a long term maintainer was misinterpreting that prime directive. Not only should Mauro probably have known better, but as a senior dev, he was setting a bad example for everyone else. As the project lead, Linus must not only to correct Mauro’s interpretation, but also make it clear to everyone else that changes like these do indeed count as breaking userspace and are therefore totally unacceptable.

Let’s consider again, did Linus go too far? I’d still say he did, but there’s a very good argument that preserving the critically important culture of not breaking user space is more important than any single dev’s feelings. By making a public example of this code and being painfully honest, Linus may have helped the project overall. Could he have done it with more tact? Absolutely, and yet, some amount of bluntness was required to make the point sufficiently clear.

Now, I didn’t bring this up to vilify or justify Linus Torvalds or his actions, but as a well-respected, politically-incorrect project leader, he makes a great case study. What one person might call “being an asshole” another might call “firm leadership”, and since CoCs are all about how we define and discourage assholery, you can start to see the problem. To understand this further, let's imagine two hypothetical open-source projects — mindwar and safespace — with wildly different dev cultures.

In project mindwar, conflict and criticism are seen as the most important ingredients to success. All devs are encouraged to be even more adversarial than Linus, and all ideas are taken out back and worked over with extreme prejudice. This is how the project weeds the good ideas from the bad. Sometimes it gets messy and personal, but there is no place in this project for hurt feelings. If you can’t take the heat, you are encouraged to leave the kitchen. Many people, including some very talented ones, do leave or are discouraged from joining in the first place. Project leadership sees these losses as unfortunate but necessary. To them, this “culling of the weak” only makes the project stronger in the long run. Those who remain find a way to get along with each other. That isn’t to say that there are no social rules at all, but they are organic and implicit. As time goes on, the people who are comfortable with those rules stay and most others leave, resulting in a somewhat homogeneous group of core developers with very thick skin and very thin patience.

Project safespace takes a very different approach. They believe that a large and diverse community is the critical ingredient to innovation. Ideas are still discussed, but extreme care is taken not to offend anyone, and that makes real debate all but impossible. Valid criticism often goes unsaid as it is hard to criticize anything that someone has worked very hard on without upsetting them. If anyone says or does anything that makes other people even a little uncomfortable, they are immediately kicked out of the community, and project leadership publicly disavows their actions by adding one more rule to the list of bannable offenses. This happens with frightening regularity as it’s very hard to say anything at all in a sufficiently diverse community without offending someone. Sometimes these ex-members were talented individuals, but like project mindwar, leadership sees these losses as unfortunate but necessary for the long term success of the project. Eventually, the only people left are so-called social justice warriors who wield the banhammer with abandon and a very few others who have mastered the art of political correctness.

Although these are purely hypothetical extremes, they highlight some interesting points. Firstly, both of their core beliefs are 100% correct. Mindwar is correct that ideas should be thoroughly and rigorously examined, and safespace is right that diverse communities and mutual respect make for healthier projects. These philosophies only become problems when they are taken to extremes. Also, both projects see themselves as meritocracies (mindwar more than safespace), but they each drive away qualified and talented individuals, so neither really is in the strictest sense.

Mindwar and safespace are both clearly dystopian straw men, but they sound just plausible enough for people to be afraid of them, and that’s a big part of why CoCs are so contentious. The slightest change causes a very real fear that the community you know and love is on a slippery slope towards these extremes, and preventing that is worth fighting for.

So if CoCs are so contentious and ethically fraught, why even bother? The argument for that — in part 2.
