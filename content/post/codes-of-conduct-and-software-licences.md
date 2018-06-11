---
title: Codes of Conduct need to learn from OSS Licences
date: 2018-06-05
draft: true # hide this post for now
---

Full disclosure: I'm a fan of Codes of Conduct (CoCs), but I'm not here today to proselytize. If anything, this post favors the other side of the debate. But I've noticed something that has been overlooked in the discussion, and we need to talk about it. Namely, that this shouldn't be a debate about if CoCs are universally good or bad.

If you just want to participate in a never ending flamewar, we already have spaces vs tabs, vim vs emacs, and [Newcomb's paradox](https://en.wikipedia.org/wiki/Newcomb%27s_paradox). Surely, in all 3 of these debates, we're making good progress towards finding the **right** answer.

![/sarcasm](/img/spongebob-meme-sarcasm.jpg)

I do hope that someday, we can all come to an agreement on CoCs, but I'm not holding my breath. In the meantime, **we need to have a discussion about if and when it's acceptable to change the CoC of a project**. That's something that we can make real progress on, and would help heal the rift in our community. I came to this realization by noticing the similarities and differences between CoCs and open-source software (OSS) licences, but before we get to that, we need a little background.

### Software Licences

In the OSS world, there are two categories of software licences: copyleft and permissive. Copyleft licences, such as the [GPL](https://en.wikipedia.org/wiki/GNU_General_Public_License), place some restrictions on the software developer in the pursuit of what is best for users and the community at large. The ideology behind these kinds of licences, known as [free (or libre) software](https://en.wikipedia.org/wiki/Free_software), asserts that users should be free to inspect, modify, redistribute, and run the software on their machines for any purpose. Copyleft licencess are designed to ensure these "four essential freedoms". Permissive licences, such as [MIT](https://en.wikipedia.org/wiki/MIT_License) or [Apache](https://en.wikipedia.org/wiki/Apache_License), place significantly fewer restrictions on developers. These licences usually only require that credit be given to the original authors.

![open source xkcd](https://imgs.xkcd.com/comics/open_source.png")
and speaking of giving credit, https://xkcd.com/225

Sometimes licence choice is a technical decision based on the needs of a specific project, but more often it is an ideological choice of the original authors. If they believe in the tenets of free software, they will prefer copyleft licences for all their projects. Conversely, if they believe that developer freedom is more important than user freedom, they will universally prefer permissive licences. While there is the occasional debate about which class of licence is "better", the two camps of developers co-exist peacefully and even contribute to eachother's projects without complaint.

### Codes of Conduct

The term Code of Conduct is not very well-defined, so I'm going to invent/redefine some terms I'll be using to avoid confusion.

1.  A Code of Ethics is a document that outlines how individuals in a community should behave.
2.  A Code of Conduct is a code of ethics that additionally provides clarity on at least some of the following:

    - examples of encouraged and discouraged behavior
    - the scope, that is the places in which a violation is relevant
    - the enforcement process
      - the processes for reporting a potential violation
      - the processes for investigating the validity of a violation
      - any resolution or mediation processes
      - potential punishments for a confirmed violation

    Examples: The [Contributor Covenant](https://www.contributor-covenant.org/) is the de-facto CoC template, but it is common for projects to customize code of conducts for their specific needs.

3.  An Anti-Code of Conduct is a code of ethics that is intentionally vague about the items listed above that a CoC attempts to clarify.  
    Examples: The [NCoC](https://github.com/domgetter/NCoC) and Linux's [Code of Conflict](https://www.kernel.org/doc/html/v4.13/process/code-of-conflict.html) are the most famous anti-CoCs.

I've tried to be as impartial as possible with these definitions. To that end, they focus on the _what_ and totally avoid the _why_. If you want do go down that rabbit hole, I suggest you start with [this article](https://techcrunch.com/2016/03/05/how-we-may-mesh/). In short, the pro-CoC group believes that CoCs help projects by making them more welcoming to groups that are underrepresented in tech. The anti-CoC crowd is a bit more varried in their specific beliefs, but they agree that the CoC cure is worse than the disease.

Lastly, I should mention that the most contention part of CoCs relate to their scope.

### Comparison

So in both of these cases, we have 2 camps of programmers with different beliefs about what is best for their projects' communities. The copyleft and pro-CoC camps both choose to impose a few more rules on their members because they believe it will be better for the community as a whole. The permissive licence and anti-CoC camps believe that placing fewer restrictions on their members is best. So why can the licence camps agree to disagree, but the CoC debates always devolve into a shitshow? I see two possible reasons. Firstly, the debate over CoCs is dangerously close to political party lines. Terms like "microagression" and "gender identity" sometimes used in CoCs are trigger words that carry political baggage. If this is the main reason for the vitriol, then there's not much we can do besides wait for the winds of politics to change. But that isn't the only difference between software licences and codes of ethics.

### The secret 3rd licence

So far, I've presented OSS licences as if it was a choice between copyleft and permissive. However, we can't ignore the default state of a project: no-licence. Fortunately, software licencing has been around long enough that the lack of a licence in an open source project is a legally well-defined state. You might think that code release published online with no licence would be in the public domain, but you'd be wrong. The no-licence state is implicitly _all rights reserved_. In other words, if you publish some code on the interwebs without a licence, and someone uses that code in almost any way, you can sue their ass.

![oprah lawsuit](/img/oprah-lawsuit.jpg)

That's not too unreasonable for code written by a single person, but it's batshit crazy for a project with multiple contributors. In that case, none of the authors actually has the rights to do anything with the full codebase. Each of them can only legally run the parts of the code that they wrote themselves. Obviously this is a terrible state for an open source project to be in, so you all agree to add a licence. That's great, so long as you all can agree on the same licence.

You see, the process for changing the licence of a piece of software is also legally well-defined. It requires agreement from **all** of the authors. If any non-trivial contributor doesn't agree to re-licence their code, the project must remove all the code contributed by that author before they can change the licence of the whole project. As a result, most tools these days encourage you to add a licence before you even make your first commit.

This all may seem like lunacy, but in practice, it works out pretty well now that we all know the rules. A junior developer occasionally creates an open source project without a licence, but this is almost always noticed and fixed before it becomes a problem.

Now, consider the alternative. Imagine a world where software licences could be changed on the whim of a project's [BDFL](https://en.wikipedia.org/wiki/Benevolent_dictator_for_life), or maybe by a majority vote. If that were the case, then you could pour your blood, sweat, and tears into an open source project for years, and then wake up one day to find that the licence had been changed to prevent you from using the very software that you helped create.

<div style="display:flex;justify-content:center"><video width="400" height="400" autoplay loop><source src="/img/racoon-cotton-candy.mp4" type="video/mp4"></video></div>

Most people agree that would be be wrong. Look how sad that racoon got when his project slipped from his tiny little fingers! And so, software re-licencing requires unanimous support. However as a result, it is prohibitavely difficult to re-licence any sufficiently large open source project unless every contributor signed away their rights in advance.

### The secret 3rd code of ethics

Like software licences, projects don't start out with a code of ethics. The problem is that unlike licences, this state isn't even close to well-defined. At the end of the day, it boils down to this. Whoever has the power to moderate the community can do it however they want. Whoever happens to administer the server is judge, jury, and executioner. Ironically, this kind of broad authority is often a complaint that people have about the processes outlined in CoCs. In reality, it's just not feasable for any community to have a full fledge judicial system. It's always going to be about one or more people in power making a judgement call. The only real choice here is how transparent your project is in who those people are.

But that isn't why you should always have code of ethics. The **real** problem here is that when your project doesn't have a code of ethics, it's not clear to people who are contributing to your project which camp the maintainers fall into. The general assumption is that a project without a code of ethics is equivalent to an anti-CoC stance, but that's as wrong as thinking unlicenced code is public domain. In practice, programmers just notoriously good at putting of documentation, and they haven't gotten around to it yet. The values of these communities can fall anywhere on the anti-CoC to pro-CoC spectrum. By not including a CoC **or** an anti-CoC, the maintainers are implicitly _reserving the right_ to choose whatever code of ethics they want at a later date. This sounds similar to the no-licence state, but this right isn't reserved individually for each contributor. Instead, it's reserved for whoever has the power. Furthermore, this right to unilaterally change the code of ethics doesn't go away once a code of ethics has been officially adopted. Any project can change their code of ethics at any time for any reason.

At this point, you might be grabbing your pitchforks, but back up a minute. The maintainers already have the power to change the codebase at any time for any reason. They've earned that privilege, and it's generally used wisely. So why is this any different? Surely the power to change the moderation process is miniscule compared to the power to change the code, right? Actually, no. If the maintainers take the codebase in a direction that you don't like, you can always fork it. Forking gives you a full copy of the code, and it doesn't take any code away from the originial project. If the maintainers take the community in a direction that you don't like, you can't fork the community. You can only divide it. You don't get a full copy, and any member you get, you take away from the originial project. This is exactly why our system makes software licences harder to change than the code itself. Social contracts are not the same as code, and when we blindly treat them like code, things get messy.

### So what do we do?

The easy part is that we should start to treat projects without codes of ethics in the same way that we treat projects without software licences. That is, we should encourage projects to pick a code of ethics (CoC **or** anti-CoC) as early as possible so that contributors know what kind of community they are signing up for. I'd go a bit further to say that all codes of ethics should be specific about the scope they apply to since that is a particularly contintious topic. In fact, it was my defense of [a scope change](https://blog.golang.org/conduct-2018) in the Go community CoC that inspired me to write this post.

Speaking of code changes, that's the harder problem. I'm not saying that codes of ethics should be as hard to change as software licences. Instead, I'm proposing that **having a transparent process for if, when, and how the code of ethics will be changed is as important as the contents of the code**. There are plenty good options here. Everything from, "we promise to never change this", to by BDFL decree, to maintainer vote, contributor vote, or even community vote. Heck, you can even treat the code of ethics just like a module of the source code. Assign a respected maintainer with final say and let the community submit issues and pull requests to them. Any of these things is fine as long as people know what they're signing up for when they join your community.

Codes of ethics are almost never an issue until someone tries to change them, and that should tell us something. Written or not, these codes are the foundations of our communities. People expect them to be stable, but they do need to adapt as the community grows. When we change a code of ethics without a transparent process, it's like the magic trick where you pull the tablecloth out from under someone's dinner. Everyone freaks out, and hopefully, you don't spill any wine. It's not so bad if you only do it once. But try that trick too many times, and people will stop inviting you to diner.

### In conclusion

If you're running an open source project today, manage the expectations of your members around future changes to your code of ethics. Do this **well before** you make changes whenever you can so that people know what they're getting into. Don't just anounce changes and justify them after the fact.

If you are a member of a community, and you would be upset if the code of ethics were to change, make a public issue asking the project owners to clarify if they might make those changes. Don't blindly project your expectations on a project. It's not the project's falt if your expectations don't match reality.

Lastly, all of us should try to converge on reasonable expectations with regards to a missing code of ethics and how these codes should, or shouldn't, be changed. If we all agreed on these two things – like already do with software licences – then we could finally quit the drama get back to writing awesome software.
