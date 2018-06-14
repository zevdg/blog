---
title: Codes of Conduct need to learn from OSS Licenses
date: 2018-06-12
summary: Codes of conduct, or CoCs, are one of the most contentius topics in open source right now. Every time a project considers adopting or changing their CoC, the discussion inevitably devolves into a heated debate about whether codes of conduct are universally good or evil. This happened recently when the Go programming language changed its CoC to cover behavior outside of their official forums. As a member Go community with an interest in community consensus, I found myself compelled to really understand what was driving this conflict.
---

_**Disclosure:** I'm a fan of codes of conduct, but I've done my best to present both sides fairly._  
_**Prerequisites:** This post assumes that you already know a bit about codes of conduct and the conflict around them. If you don't, go read [this article](https://techcrunch.com/2016/03/05/how-we-may-mesh/) right now._

Codes of conduct, or CoCs, are one of the most contentius topics in open source right now. Every time a project considers adopting or changing their CoC, the discussion inevitably devolves into a heated debate about whether codes of conduct are universally good or evil. This happened recently when the Go programming language [changed its CoC](https://blog.golang.org/conduct-2018) to cover behavior outside of their official forums. As a member Go community with an interest in community consensus[^1], I found myself compelled to really understand what was driving this conflict.

Now if you just want to participate in a never ending flame war, don't let me stop you. You can choose between spaces vs tabs, vim vs emacs, and [Newcomb's paradox](https://en.wikipedia.org/wiki/Newcomb%27s_paradox). In all 3 of these debates, we're making good progress towards finding the _right_ answer.

![/sarcasm](/img/spongebob-meme-sarcasm.jpg)

Seriously though, I do hope that someday we can all come to an agreement on CoCs, but I'm not holding my breath. In the meantime, this toxic culture war is driving wedges into our communities. Every time a community updates their moderation procedures the debate resurfaces and the wedges are driven deeper. In order to break this cycle, **we need to have a discussion about if and when it's acceptable to change the rules of a community**. That's something that we can make real progress on, and it would help avoid these harmful flame wars. I came to this realization by noticing the similarities and differences between CoCs and open-source software (OSS) licences. We'll walk through that comparison together, but first we need a little background on both of those topics.

### Software Licences

In the OSS world, there are two categories of software license: copyleft and permissive. Copyleft licences, such as the [GPL](https://en.wikipedia.org/wiki/GNU_General_Public_License), place some restrictions on the software developer in the pursuit of what is best for users and the community at large. The ideology behind these kinds of licences, known as [free (or libre) software](https://en.wikipedia.org/wiki/Free_software), asserts that users should be free to inspect, modify, redistribute, and run the software on their machines for any purpose. Permissive licences, such as [MIT](https://en.wikipedia.org/wiki/MIT_License) or [Apache](https://en.wikipedia.org/wiki/Apache_License), place significantly fewer restrictions on other software developers. They mimic software in the [public domain](https://en.wikipedia.org/wiki/Public-domain_software), except they usually require that credit be given to the original authors.

![open-source xkcd](https://imgs.xkcd.com/comics/open_source.png")
_Speaking of giving credit: https://xkcd.com/225_

Much like CoCs, licences lay out rules that contributors need to follow, and there are two camps in disagreement on what those rules should be. Sometimes licence choice is a technical decision informed by the specific needs of a project, but more often it is a purely ideological choice by the project's original authors. If they believe in the tenets of free software, they will prefer copyleft licenses for all their projects. Conversely, if they believe that developer freedom is more important than user freedom, they will universally prefer permissive licenses. While there is the occasional debate about which class of licence is generally "better", they are much more civil than the debates about CoCs. The copyleft and permissive licence camps mostly just agree to disagree, and even find common ground in true open source fashion by using and contributing to each other's projects.

### Codes of Conduct

The term "code of conduct" means different things to different people. To avoid confusion, I'm going to invent and define some terms I'll be using in the rest of this post.

1.  A **code of ethics** is a document that outlines how individuals in a community should behave.
2.  A **code of conduct** or CoC is a code of ethics that provides additional clarity on at least some of the following:

    - examples of encouraged and discouraged behavior
    - the scope, that is the places in which a violation is relevant
    - the enforcement process
      - the processes for reporting a potential violation
      - the processes for investigating the validity of a violation
      - any resolution or mediation processes
      - potential punishments for a confirmed violation

    Examples: The [Contributor Covenant](https://www.contributor-covenant.org/) is the de-facto OSS CoC, but it is commonly used only as a starting point and then customized for each community.

3.  An **anti-code of conduct** or anti-CoC is a code of ethics that is intentionally vague about the items listed above that a CoC attempts to clarify.  
    Examples: The [NCoC](https://github.com/domgetter/NCoC) and Linux's [Code of Conflict](https://www.kernel.org/doc/html/v4.13/process/code-of-conflict.html) are the most famous anti-CoCs.

These definitions focus only on the _what_. The _why_ is out of scope for this post, but [this article](https://modelviewculture.com/pieces/the-new-normal-codes-of-conduct-in-2015-and-beyond) thoroughly covers the motivations of both sides. In short, the pro-CoC group believes that CoCs make project communities more welcoming, particularly to historically marginalized groups. The anti-CoC crowd believes that the CoC cure is worse than the disease.

Lastly, I should mention that the most contentious part of CoCs relate to their scope. CoCs that only consider your actions within official group spaces (mailing lists, forums, conventions, pull requests, etc.) are significantly less contentious than CoCs that include other public forums like twitter.

### Comparison

So in both licences and CoCs, we have 2 camps of programmers with different beliefs about what is best for their projects' communities. The copyleft and pro-CoC camps both choose to impose a few more rules on their members because they believe it will be better for the community as a whole. The permissive licence and anti-CoC camps believe that placing fewer restrictions on their members is best. So why can the licence camps agree to disagree, but the CoC debates always devolve into a shitshow? I see two possible reasons. Firstly, the debate over CoCs is dangerously close to political party lines. Terms like "microaggression" and "gender identity" sometimes used in CoCs are trigger words that carry political baggage. If this is the main reason for the vitriol, then there's not much we can do besides wait for the winds of politics to change. But that isn't the only difference between software licences and codes of ethics.

### The secret 3rd licence

So far, I've presented OSS licences as if it was a choice between copyleft and permissive. However, we can't ignore the default state of a project: no-licence. Fortunately, software licensing has been around long enough that the lack of a licence in an open-source project is a legally well-defined state. You might think that code published online with no licence would be in the public domain, but you'd be wrong. The no-licence state is implicitly _all rights reserved_. In other words, if you publish some code on the interwebs without a licence, and anyone else uses that code in almost any way, you can sue their ass.

![oprah lawsuit](/img/oprah-lawsuit.jpg)

That's not too unreasonable for code written by a single person, but it's batshit crazy for a project with multiple contributors. In that case, none of the authors actually has the rights to do anything with the full codebase. Each of them can only legally run the parts of the code that they wrote themselves. Obviously this is a terrible state for an open-source project to be in, so you all agree to add a licence. That's great, so long as you all can agree on the same licence.

That's more important than you might think because, the process for changing the licence of a piece of software is also legally well-defined. It requires agreement from _all_ of the authors. If any non-trivial contributor doesn't agree to re-licence their code, the project must remove all the code contributed by that author before they can change the licence of the whole project. As a result, tools like github and `npm init` encourage projects to add a licence before they even make their first commit.

This all may seem like lunacy, but in practice, it works out pretty well now that we all know and agree on the rules. A junior developer occasionally creates an open-source project without a licence, but this is almost always noticed and fixed before it becomes a problem.

Now, consider the alternative. Imagine a world where software licences could be changed on the whim of a project's BDFL (benevelent dictator for life), or maybe by a majority vote. If that were the case, then you could pour your blood, sweat, and tears into an open-source project for years, and then wake up one day to find that the licence had been changed to prevent you from using new versions of the very software that you helped create.

<div style="display:flex;justify-content:center"><video width="400" height="400" playsinline autoplay muted loop><source src="/img/racoon-cotton-candy.mp4" type="video/mp4"></video></div>

Most people agree that would be be wrong. Look how sad that racoon got when his project slipped from his adorable little fingers! I digress, but that's basically why software relicensing requires unanimous support. However as a result, it is prohibitively difficult to re-licence any sufficiently large open source project unless every contributor signed away their rights in advance. That's the price we pay for peace in the software licensing wars.

### The secret 3rd code of ethics

Like software licences, projects don't start out with a code of ethics. The problem is that unlike licences, this state isn't even close to well-defined. At the end of the day, it boils down to this. Whoever has the power to moderate the community can do whatever they want. The BDFL is judge, jury, and executioner. In practice, this consolidation of power is mostly unavoidable. It's just not feasible for most communities to have a full fledged judicial system. It's always going to be about one or more people with authority making a judgement call. The only real choice here is how transparent your project is about who those people are and what their process is.

But that isn't why you should always have a code of ethics. The _real_ problem here is that when your project doesn't have a code of ethics, it's not clear to people who are contributing to your project which camp the maintainers fall into. A common assumption is that a project without a code of ethics is implicitly anti-CoC, but that's as wrong as thinking that unlicensed code is implicitly public domain. In reality, programmers are just notoriously good at putting off documentation, and they simply haven't gotten around to it yet. The values of these communities can fall anywhere on the anti-CoC to pro-CoC spectrum. By not including a CoC or an anti-CoC, the maintainers are implicitly _reserving the right_ to choose whatever code of ethics they want at a later date. This sounds similar to the no-licence state, but this right isn't reserved individually for each contributor. Instead, it's reserved for whoever has the power. Even worse, this ability to unilaterally change the code of ethics isn't just reserved until a code is chosen. It remains true forever. Any project can change their code of ethics at any time for any reason.

![rabble rabble rabble](/img/south-park-pitchforks.jpg)

Woah there! Put down those pitchforks. The maintainers already have the power to change the codebase at any time for any reason. They've earned that privilege, and they wield it wisely. We trust them to know their domain and make well informed decisions. Why is this any different? Surely the power to change the moderation process is miniscule compared to the power to change the code itself, right?

On the other hand, if the maintainers take the codebase in a direction that you don't like, open source has you covered. Forking gives you a full copy of the code, and it doesn't take any code away from the original project. If the maintainers take the community in a direction that you don't like, you can't fork the community. You can only divide it. You don't get a full copy, and any member you get, you take away from the original project. This is exactly why our system makes software licences harder to change than the code itself. Social contracts are not the same as code, and when we blindly treat them like code, things get messy.

### So what do we do?

We come back to this question: why do the various software licence camps get along so much better than the CoC camps? It boils down to these 3 things:

1.  We encourage projects to choose a licence as early as possible.
2.  We don't assume anything about a project with no licence.
3.  Everyone understands and agrees on the process to change a software licence.

So how does this apply to codes of conducts? Step 1 is the easiest part. **We must encourage projects to pick a code of ethics (be it CoC or anti-CoC) as early as possible.** That way new users and contributors know what kind of community they are signing up for. I'd go a bit further to encourage all codes of ethics to be specific about the scope they apply to since that is a such a contentious topic.

Step 2 is a bit more subtle. **We must stop making assumptions about projects that haven't yet documented their code of ethics.** A missing code of ethics doesn't imply an anti-CoC any more than a missing software licence implies a permissive licence. The only thing that you can safely conclude in this case is that you do not know how this community moderates itself. Similarly, a code of ethics that doesn't define its scope doesn't imply a limited scope. In C, an uninitialized integer doesn't necessarily default to zero. In Javascript, undefined !== false. Programmers understand the difference between defined and undefined behavior, and we all know that English is way more ambiguous than either C or Javascript, so why do many of us insist on filling that ambiguity with foolish assumptions? As programmers, we should know better.

Step 3 is the hardest problem. **We must converge on a standard process for changing a code of ethics.** That is not to say that all projects must use the same process. As I mentioned above, some projects require contributors to sign a [CLA](https://en.wikipedia.org/wiki/Contributor_License_Agreement) in order to "opt out" of the standard licence change procedure. In the same way, projects that want to change their code of ethics in a non-standard way should be free to do so as long as they warn contributors up front. I'm also not implying that codes of ethics should be as hard to change as software licences are. On the contrary, although that would be the easiest solution, I personally believe that a code of ethics must be allowed to change with the times. It's just that we ought to know in advance how those changes will happen.

I don't want to sidetrack this post by suggesting any specific process here, but there are plenty of reasonable options. Everything from unanimous contributor agreement (like software licences), to decision by BDFL decree (the status quo), to maintainer vote, contributor vote, or community vote. You can even treat the code of ethics just like a module of the source code. Assign a respected maintainer with final say and let the community submit issues and pull requests to them. Any of these options are fine so long as people know what they're signing up for when they join a community.

Codes of ethics are almost never an issue until someone tries to change them, and that should tell us something. Written or not, these codes are the foundations of our communities. People expect them to be stable, but they do need to adapt as the community grows. When we change a code of ethics without a clear and transparent process, it's like the magic trick where you pull the tablecloth out from under someone's dinner. Everyone freaks out, and hopefully, you don't spill any wine. It's not so bad if you only do it once. But try that trick too many times, and people will stop inviting you to dinner.

### In summary

We must

1.  encourage projects to pick a code of ethics (CoC or anti-CoC) as early as possible.
2.  not make assumptions about projects with no code of ethics.
3.  converge on a standard process for changing a code of ethics.

If we did these 3 things – like we already do with software licences – then we could put this drama to rest and get back to writing awesome software.

<!-- prettier-ignore -->
[^1]: "interest in community consensus" is an extreme understatement. I [founded my startup](https://medium.com/appleseedcorp/a-fresh-start-747b2ce00240) appleseed.vote specifically to tackle the problem.
