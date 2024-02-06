# CHIPS Alliance project GSoC contribution guidelines

# Step 0 - Prior Reading

Firstly, **please read the Google Summer of Code
[Contributor Manual](https://google.github.io/gsocguides/student/)**. It contains a
lot of helpful information about the program and about participating as a
contributor in Google Summer of Code.

Secondly, **please read the Google Summer of Code
[FAQ](https://developers.google.com/open-source/gsoc/faq)**.
It contains lots of helpful information about the program, specific deadlines
and how things will run.

# Step 1 - Finding an **Idea**

Due to CHIPS Alliance operating in various Workgroups and many smaller projects, it can be tricky to work out which projects match your skills. We have a number
of useful tools to help match you with projects.

As selecting a project or understanding an idea can be hard, we recommend you
come join us [on Slack](https://chipsalliance.slack.com) and talk to us further about them. Good contributors engage with the community
even before GSoC starts!


## **Idea** Issue Tracker

The CHIPS Alliance organization has 
[dedicated markdown list for specific years](https://github.com/chipsalliance/ideas)
that lists tasks that are suitable to be completed as part of GSoC.

## Can I work on XXX?

If an idea is listed in the list mentioned above, it's probably
a good one!

## What should I work on?

What do you like doing? What interests you? You know better what projects are
going to keep you interested for 3 months than we do.

## Is project XXX important?

**For GSoC the most important factor is the application's quality!** If the
strongest application submitted is for a lower priority project, it is much more likely to
be accepted - even if poorer applications exist for higher priority projects.

# Step 2 - Writing A **Proposal**

**Feel free to submit multiple proposals.**

The following links detail general ways to write a successful Summer of Code Proposal:

* [HOWTO Write Project Proposals](http://wiki.inkscape.org/wiki/index.php/SOC_Writing_Project_Proposals)
* [Inkscape's Accepted Proposals](http://wiki.inkscape.org/wiki/index.php/SOC_Accepted_Proposals)
* [RedHat's experience](https://opensource.com/article/21/10/google-summer-code)

## Tips

Having reviewed many proposals in the past years, there are a couple of things that many of them seem to
be lacking. This list of tips should help you avoid common mistakes and make
your proposals better.

### **Tip 1** - Include Slack and GitHub Nickname

Include your Slack and GitHub nicks as the first thing in the detailed description.

During Summer of Code hundreds of new people turn up, keeping records straight
can become a bit of a challenge. Especially when your Slack and/or GitHub nick, email address and real name have
no resemblance.

### **Tip 2** - **Project First**, Resume Second

We are most interested in your proposal for the project. If your proposal looks
good, we may then want to look at your resume / personal description.

Hence, include the project information first and your personal stuff second.

### **Tip 3** - Include assertive Functional Milestones

One of the best ways to show that you are a serious contributor is to include
proper assertive milestones. These should be single sentences which say
something like:

 * The AI will issue move orders.
 * The client will be able to display planets in a 3d fashion.
 * The ruleset will allow tpclient-pywx to see planets.
 * The metaserver will display a starmap generated from starmapper.

**The keyword here is will, it is assertive.**

These milestones should have dates associated with them. We understand that you
are new to the project and that these dates will change as the project
progresses. You *will not* fail just because a milestone had to be moved a week
or dropped altogether.

The milestones should be testable and specific. Here are some examples which
are not acceptable.

 * The AI framework will be finished.
 * The star map will work.
 * The ruleset will be balanced.

Negative milestones are hard to test, avoid them if possible. For example "The
AI will not issue wrong orders" is almost impossible to prove and not all that
useful. More often negative statements are goals not milestones.

These milestones will be hard to figure out, being able to talk about specifics
shows that you have done your research and know your stuff. Have confidence in your
own abilities!

Keep your milestones small, they should be doable in less than a week's full
time work. The smaller (and more specific) they are, the harder it will be to
get behind on.

Talk to the mentors about your milestones, they have a huge amount of knowledge
about what is realistic and will be happy to help you refine the details.

### **Tip 4** - We are not mind readers

**Anything which is not linked to from your proposal effectively does not
exist.** I'm afraid we cannot (yet) read your mind.

It is unlikely that we will remember that Slack conversation we had about XYZ.
Other mentors may not have seen that conversation either.

If you have thought about a certain way to do something, tell us - even if you
decided that it was not feasible. If you had an important Slack conversation
which resulted in changing the way you think, link to the logs. If a web page 
you've been reading proved influential, share with us!

### **Tip 5** - Submit now!

Do not submit last minute as you won't have time to update your
proposal based on feedback. There is still plenty of time for mentors to give
feedback and for you to update your proposal. Plan ahead!

### **Tip 6** - Make your application public

Having a public application means not only can mentors give you feedback but
other contributors and the general community can, too!

Using a wiki is a good idea because it lets us look at the history of how your
proposal has evolved. It also means you can have formatting, making it easier to
read.

### **Tip 7** - Splitting applications which are too long

Google limits the text length you can submit for your detailed description.
This can be quite limiting if you have some detailed information or pseudo code.
Hence, it is recommended that you produce two versions of your application.

A "cut back" version which fits into the character limit. This should be all
the very important bits of your application. You must include your functional
milestones in this section. There should be enough 'meat' in this section to
convince us to look at your further URL.

The URL in the document should link to your full proposal. Feel free to add
things like pseudo code, design information or anything else which you feel is
relevant.

The extended proposal to which you will be linking should also be included in your complete 
Google application. Duplicated text should be clearly marked in a different
color, ensure it remains readable. We will not be able to jump between documents back and forth, 
so make sure the extended proposal is self-contained.
**Remember, quality is better than quantity!**

<hr>

## Selection Criteria

The following might give you an indication of some of the things we are looking for.

There is always a subjective element to judging applications, but we believe that
by trying to quantify the decision process, we're making it easier for people to understand why
their application was or was not accepted.

 * **Proposal is longer than a few sentences.** - We need some 'meat' in the proposal in order to even consider it.
 * **Proposer has contacted us prior to the submission.** - This demonstrates a definite interest in CHIPS Alliance's projects and proves your ability to communicate with us.
 * **Proposer knows the appropriate programming language(s).**
 * **Proposer shows evidence of being able to create software.** - Our goal is to help programmers become good at Open Source, not to teach non-programmers how to program. However, we are willing to help people develop their programming skills.
 * **Proposal is well written.** - While we don't expect perfect English, we do expect that the proposer took time to spell check, proofread it, organize it logically, and use comprehensible grammar.
 * **Proposal demonstrates understanding of the subject matter.** - We expect the proposer to do some research, ask questions, and gain some understanding of the project they're proposing. This gives us confidence that they'll be able to complete the project successfully.
 * **Proposal shows creativity.** We like to see someone thinking outside the box, including proposing ideas for projects we hadn't listed.
 * **Proposal is the only submission for the given task.** - Many proposals focus on the same few tasks, so if you're the only person proposing to do a given project, that weighs in your favor.
 * **Proposal shows implementation planning.** - If the author has broken the work out into a task list, it shows that they know what they'll be doing.
 * **Proposal scope is realistic.** - 12 weeks will go by fast. Proposals that promise too much are unlikely to be completed in a timely fashion.
 * **Proposal shows motivation.** - While it's important to describe the project in detail and show us that you have the necessary skills, do not forget to communicate your motivation, i.e. why you want to work with us on this particular project.

The following are conditions that automatically result in rejection:

 * Group project proposed. Google has specified that groups MAY NOT participate. Individuals only.
 * Proposer must be at least 18 years old at time of registration.
 * Proposer must be eligible to work in their country of residence during the duration of the program.
 * Proposer must be a resident of a country not currently embargoed by the United States.

# Step 4 - Fixing your first bug

While not required, it is **highly recommended** that GSoC contributors try and fix
at least one small bug before the mentors finish reviewing applications.

Most CHIPS Alliance projects have a number of small tasks marked with the 'good first issue label'. These problems/improvements are generally smaller and designed to be easy to get started with.

Submitting an enhancement or bug fix shows that you have understood the project enough to get things set up.

# How to ask for help

Google Summer of Code will require you to work independently and hence showing
independent investigation and troubleshooting skills **is a must**. We
definitely encourage asking questions of the mentors, but you must demonstrate
having researched the question.

Some good pages to look for tips about writing good questions can be found below:

 * [How To Ask Questions The Smart Way - Eric Steven Raymond](http://www.catb.org/esr/faqs/smart-questions.html)
 * [How To: Ask Questions The Smart Way - C++ Articles](http://www.cplusplus.com/articles/jLzyhbRD/)

Often the best way to ask questions is to start writing your Google Summer of Code proposal as documented in the [Writing Proposals](#step-2---writing-a-proposal) section and finding out what areas you are getting stuck at.


---

# Where to Ask Questions

 * Join the [mailing lists](https://lists.chipsalliance.org/) for the projects you are interested in.
 * Join [CHIPS Alliance Slack](https://chipsalliance.slack.com/). To do so, use the following [Slack invite](https://slack-invite.chipsalliance.org/)

---

# Frequently Asked Questions (FAQ)

## Can I work on project XXX?

Yes!

## Can you please help me?

Please ask more specific questions. What is it you don't understand? What have you
read so far? Tell us about yourself.

See the [How to ask for help](#how-to-ask-for-help) section above.

## What should I work on?

What do you like doing? What interests you? You know better what projects are
going to keep you interested for 3 months than we do.

### Is project XXX important?

For GSoC the most important factor is the application's quality! If the strongest
application submitted is for a lower priority project, it is much more likely to be
accepted - even if poorer applications exist for higher priority projects.

## What should I do next?

Start writing your proposal as laid out in the [Writing
Proposals](#step-2---writing-a-proposal) section. This will help you ask better
questions, too!

## Whom should I contact for project XXXX?

As developer time is limited, we ask everyone post their messages to the public
mailing list or Slack channel (read
<http://www.catb.org/esr/faqs/smart-questions.html#noprivate> for a more detailed
explanation).

# Thanks

We would like to thank the following:

 * <http://wiki.creativecommons.org/Summer_of_Code> _Creative Commons_ - a lot of the information in this document was adapted from their Summer of Code page.
 * <http://www.google.com/> - without Google, this wouldn't even be possible.
