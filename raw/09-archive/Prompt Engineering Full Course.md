---
title: "Prompt Engineering Full Course"
source: "https://www.youtube.com/watch?v=2BpCk4d2Cc0"
author:
  - "[[Tech With Tim]]"
published: 2026-03-11
created: 2026-04-13
description: "🚀 Try Flow Pro free for 14 days + get an extra month free with my code TECHWITHTIM!👉 Start here: https://ref.wisprflow.ai/techwithtimIn this video, you'll learn everything you need to know about"
tags:
  - "clippings"
---
![](https://www.youtube.com/watch?v=2BpCk4d2Cc0)

🚀 Try Flow Pro free for 14 days + get an extra month free with my code TECHWITHTIM!  
👉 Start here: https://ref.wisprflow.ai/techwithtim  
  
In this video, you'll learn everything you need to know about prompt engineering. I'll explain what it is, why it's important, how to do it faster. The top techniques and methods and advanced strategies to get the most out of loops.  
  
Want to make real money with coding? I share high-signal insights on careers, monetization, and leverage in my free newsletter. Join here and get my guide How to Make Money With Coding instantly: https://techwithtim.net/newsletter  
  
🎞 Video Resources 🎞  
Get the markdown file in this video: https://newsletter.techwithtim.net/prompting  
  
⏳ Timestamps ⏳  
00:00 | Intro  
01:44 | What is Prompt Engineering  
04:07 | How to Prompt Faster  
07:05 | How LLMs "Think"  
10:40 | Steering vs Commanding  
11:53 | Be Specific & Set the Scene  
14:32 | Few-Shot Prompting  
18:10 | Chain of Thought  
20:05 | Structured Output  
22:04 | Constraints & Negatives  
24:19 | Iterative Refinement  
25:22 | Interview Style Prompting  
29:13 | Advanced Techniques & Parameters  
35:04 | Common Mistakes  
  
Hashtags  
#LLMs #AiPrompts #SoftwareEngineer  
  
UAE Media License Number: 3635141

## Transcript

### Intro

**0:00** · In this video, you'll learn everything you need to know about prompt engineering.

**0:04** · I'll explain what it is.

**0:05** · Why it's important. How to do it faster.

**0:08** · The top techniques and methods and advanced strategies to get the most out of loops.

**0:13** · With that said, let's dive in.

**0:14** · So what I've done for this video is have created a markdown file that contains all of the examples and key talking points that I'll go over.

**0:21** · Now, if you want this file for yourself for your reference, you can get it for free just by clicking the link in the description and subscribing to my newsletter.

**0:28** · Anyways, let's start and I want to just show you a quick example of a bad prompt versus a great prompt just to kind of set the tone, and then we'll get into all of the other theory.

**0:36** · And keep in mind, all of the different topics in this video are available down below in the video player or the chapters in the comments in case you want to fast forward.

**0:44** · Okay, so what is a bad prompt?

**0:45** · Well, an example of that would be something like write something about our product.

**0:49** · It's going to give you something like generic marketing fluff, wrong tone, wrong length, probably no CTA.

**0:54** · The model is effectively going to guess what you want here, whereas a better prompt would be something like this.

**1:00** · You are a senior B2B copywriter.

**1:02** · Write a two sentence LinkedIn ad for our project manager at SAS.

**1:05** · As an alternative.

**1:06** · The audience is ops managers at mid-sized companies.

**1:09** · The tone is confident but not salesy and end with a clear CTA.

**1:13** · Now, if you do this, you're hopefully going to get a result that's on brand scoped, actionable, and easy to drop into an ad.

**1:19** · The point of me showing you these examples is that when we're writing these prompts, we're using the same tool or the same LLM.

**1:26** · So what's giving us the difference in result isn't the LLM, it's the way in which we instruct it.

**1:32** · And most people, while this kind of seems obvious, are writing prompts closer to the iPad prompt than they are to the good prompt, and just because a prompt is long does not necessarily make it good.

**1:42** · Which I'm going to go over in this video.

### What is Prompt Engineering

**1:44** · So this leads me to what is prompt engineering and why does it matter?

**1:48** · Well, you should really think of prompt engineering just like programing in natural language.

**1:52** · So rather than using Python or Java or JavaScript, you're just using, you know, text or your voice or whatever language it is that you speak in to try to get some kind of result complete some action, get some text, whatever.

**2:04** · Effectively what you're doing is you're giving instructions in plain language instead of something like code.

**2:10** · Now, it's important to note that the models that we give these instructions to, they don't have a built in task list.

**2:16** · So you have to define the task, the role, the format and the constraints within the prompt.

**2:21** · And you have to be very specific with what it is that you actually want.

**2:24** · And that's why the same model can seem brilliant or useless, depending on the clarity, context and the structure that you provide.

**2:31** · Now, when most people prompt AI models, they're trying to get some kind of text in return.

**2:36** · And while that's still a very valid use case of these models, it's important to note that we've now shifted kind of into an agent era where a lot of these models are capable of interacting with various tools, searching the web, and actually taking actions they can change something in your asana, right?

**2:52** · They can write a Google doc, they can create a PowerPoint slide.

**2:56** · And because of that prompt, engineering becomes even more powerful because we're no longer just directing the model to try to give us some kind of textual output, we're actually instructing it to take some kind of actions which can give us a real meaningful result.

**3:09** · So just keep that in mind.

**3:11** · While a lot of what I'm showing you here is going to be based on text.

**3:13** · This also works for agents, right?

**3:16** · Or more complex models that are capable of calling tools and just go through quick example.

**3:21** · You can see a vague prompt would be something like help me with my essay was a specific prompt is something like you were a tutor, help me improve the thesis and first paragraph of this 500 word history essay on the causes of World War one.

**3:32** · Keep my voice, adjust the edits inline, etc.. Okay.

**3:35** · Now, in terms of why this is important, well, we're moving more and more towards an AI world.

**3:39** · So for people like developers, marketers, researchers, just anyone who's using AI, the better the result you can get from it, obviously the better that is for everyone, and the faster you can get to the result if you have better prompts.

**3:51** · So the takeaway write better prompts is just better results for everyone, and this is overall a skill that you will learn over time.

**3:58** · But by knowing some of the foundations that I'll teach in this video, it will just speed that up for you and allow you to think of these a little bit more intentionally while you're writing the prompts.

**4:06** · Now, what you've probably gathered at this point is that the more details we include in the prompt, the better the result or action is that this model will take.

### How to Prompt Faster

**4:14** · Now, that's generally true.

**4:15** · I mean, longer prompts are not always better, but most of the time they will give you a better result.

**4:19** · However, that's only if you actually take the effort to write them.

**4:22** · Most people are lazy, they type very slow, and they don't want to spend ten, 20, 30 minutes here typing a prompt just to have to maybe change it, iterate on it, whatever.

**4:31** · So what I'm going to suggest to you guys is going forward, rather than typing your prompts, just speak them.

**4:36** · So use your voice, use natural language and this will allow you to have prompts significantly faster where you can include all of the details without lazily having to type them in.

**4:46** · Now this applies on phone and applies on computer, and the tool that I use to do this within any application doesn't just have to be something like ChatGPT.

**4:53** · Here is called a whisper flow.

**4:55** · Now I'm just going to quickly show you how it works and if you want to try it for free, I have a link in the description.

**4:59** · I would highly recommend it because it is currently the best dictation tool that works a lot better than anything built into your computer.

**5:06** · So for example, let me just do something.

**5:08** · Hey, this is just a quick test where I want to dictate with whisper flow and see what kind of results I'm getting.

**5:12** · Notice I'm talking, you know, extremely, extremely fast.

**5:17** · I'm making a few repetitions, pauses, etc.

**5:20** · and let's see the result that we get.

**5:22** · Okay, so you can see the kind of little bubble popped up there.

**5:25** · And pretty much instantly we get the result.

**5:27** · And you'll see that if we go through the result here, it automatically does the punctuation, adds the capitalization, and corrects any of the ums, ons, or repetitions that I had.

**5:36** · I believe I said extremely twice.

**5:38** · It recognized that wasn't useful and it just removed.

**5:41** · So you get a much faster, better result and you can also do something like this.

**5:45** · I want to have three bullet points.

**5:47** · Bullet point one is Apple's bullet point two is banana's, bullet point three is pears.

**5:54** · And you'll see that it will automatically format it for me like that.

**5:57** · Okay.

**5:58** · So when you're doing the prompts, the formatting is very important as well.

**6:00** · And this tool will handle it for you compared to a built in dictation.

**6:04** · I do have a long term partnership with them, full disclosure, but I was using them much before we did the partnership because the tool is very, very good.

**6:11** · You can see here I've spoken 35,000 words.

**6:14** · My WPM is 162, which is much faster than I would be able to type.

**6:19** · It has a lot of other features like dictionaries, snippets.

**6:22** · You can change the style based on the apps that you're working inside of notes, all of this kind of stuff, and a bunch of settings where I was just hitting a keyboard shortcut on my computer, and that allows me to actually trigger flow to start activating on my computer.

**6:35** · So I use this in every kind of application.

**6:37** · Sometimes I use it to write emails, sometimes I use it for prompting.

**6:40** · Right?

**6:40** · Sometimes I used in cursor to prompt a model or reference files, and I'll show you more of it in the video.

**6:45** · But the point is, speak your prompts, you're just going to have better prompts.

**6:49** · And this tool also is available on phone.

**6:51** · They actually recently released it on Android, so you can use it directly from the keyboard like on your iPhone or Android.

**6:57** · So even if you're on mobile, you have no excuse not to give a detailed, comprehensive prompt that actually includes the information that you want.

**7:04** · So this now leads us to the next section, which is how let's think.

### How LLMs "Think"

**7:08** · Now, an LLM is a large language model.

**7:12** · And effectively what these are capable of doing is replying to text okay.

**7:16** · So you give some text in, they give some text app.

**7:19** · Now you can configure them in very fancy ways to call tools or call other LMS or create something or take some action.

**7:27** · But effectively, at the very root of an Lem, there's a text prediction model.

**7:32** · It's important to understand this because when you give a prompt to a model, you need to imagine that what it's attempting to do is predict the next text that you would expect to see in this sequence.

**7:43** · So while you might see reasoning models, you think that you know the AI is thinking or developing something.

**7:49** · Really, it's just been trained on a massive amount of data and given some prompt it's able to predict with a relative degree of accuracy what it is it thinks you want in terms of the output.

**8:00** · So the prediction is usually going to be in text or in tokens that they may call it right.

**8:05** · You give some tokens in it spits some tokens out.

**8:08** · That's effectively what an Lem is.

**8:10** · We don't need to worry about the architecture or anything complicated there just remember you have some input, you get some output, and it's just predicting what it thinks that output is going to be.

**8:19** · Now with that in mind and Lem by default.

**8:22** · So something like GPT 5.2 right.

**8:24** · It doesn't have any memory.

**8:26** · Now what would give it memory is the providers of these models injecting previous parts of your conversation into the prompt or into the model automatically.

**8:36** · So what you need to understand is that a lot of times when you use, you don't.

**8:39** · Lem's right.

**8:40** · You use ChatGPT, you use Claude, or you use curser.

**8:43** · Behind the scenes, the people who developed those tools or these interfaces to work with the LMS, they're injecting a lot of data into the prompt that you provide to give you a better response.

**8:54** · So while you may prompt and say, hey, you know, review my essay and tell me what's wrong behind the scenes, the prompt is significantly larger than that, where it includes a lot more details that the Lem is looking at.

**9:06** · So it's just important for you to understand that, because by default, it doesn't have memory.

**9:10** · It doesn't have, like all of these fancy features that you see in like the ChatGPT user interface.

**9:15** · The reason why that exists is because OpenAI, who made ChatGPT, created this nice interface on top of the Lem, which is like the brain at the heart of all of this, that injects this other information into the prompt that then goes to the model, that then gives you the response.

**9:32** · So 99% of the time, your prompt is not the only thing the yellow Lem is seeing.

**9:37** · It's going to be seeing, you know, previous conversation history.

**9:39** · Maybe it has access to some tools, right?

**9:42** · Whatever.

**9:42** · There's all kinds of things that are usually being thrown in that you don't actually get to see.

**9:46** · And it's really important that you kind of internalize that and understand it.

**9:50** · And you don't think like GPT 5.2 or something has this memory and just knows everything about you.

**9:55** · The only reason that it knows something is because it's just taking information that you've given to it previously, and just injecting that into the prompt that it's using to give you the response.

**10:05** · Now, that additional information that I just talked about is typically referred to as context.

**10:10** · It's the other stuff that the Lem can see and look at.

**10:14** · That's not just the prompt that you gave it.

**10:16** · So just understand that the context, specificity and structure that you provide is what shapes what it's going to say next.

**10:23** · And a lot of these tools, just like, you know cursor. Right.

**10:25** · The tool that I'm using right now, if I create an agent by default, it's jamming a bunch of context into the prompt.

**10:31** · And if I tag something like this markdown file right.

**10:34** · And I say, you know, hello world, the prompt is Hello world plus all of this additional context.

### Steering vs Commanding

**10:40** · Now, with that in mind, let's quickly talk about steering versus commanding the model.

**10:44** · So the common mistake that most people make when prompting is they command the model to do something, rather than steering it in the correct direction.

**10:52** · Now commanding the model is something like summarize this okay.

**10:55** · Do this, you know, write this down.

**10:57** · Take this thing. Look at this thing. Whatever. Right.

**11:00** · So if that's the case, the model chooses the length, the style and the focus that it's going to take when it's summarizing the thing in this instance.

**11:07** · Whereas steering the model, you give it more direction on exactly what you want.

**11:11** · So you are an executive assistant.

**11:12** · Summarize the meeting transcript and for bullet points, focus on decisions and action items.

**11:17** · No filler.

**11:17** · Notice that we're not only telling you what to do, we're telling it what not to do, and we're giving it a much more clear objective where when it's trying to predict what we want next, it can give us a much more accurate, better result because of the detail we've included in the prompt.

**11:31** · So when you steer the model, you're typically indicating the length, the focus and the format that you want.

**11:36** · Whereas when you're commanding the model, you're telling it to do something and it's picking how it's going to do that. The result you're going to get, etc..

**11:42** · So I'm not going to focus on that too much more, but just understand commanding and steering.

**11:46** · Now, what I want to do is get into the core techniques of prompt engineering and really focus on a lot of examples.

**11:52** · So one of the most basic and important techniques that you can employ is to be specific and to set the scene or specify the particular role that you want.

### Be Specific & Set the Scene

**12:00** · The model or agent to take.

**12:02** · Now these are the four things that, if you include, will always give you a much better result than simply commanding the model to do something.

**12:10** · If you include a role in audience, a tone, and some kind of format or output, you're almost always going to get a significantly better reply.

**12:17** · So here it says, you know, reply to this customer complaint.

**12:20** · Okay, fine, you can reply to it.

**12:21** · But if you said something like this, you're giving it all of these details the role, the audience, the tone and the format.

**12:27** · So you're going to get a better response.

**12:28** · So what I want to do now show you a few practical examples of this by actually writing or voicing the prompt here in ChatGPT.

**12:34** · So let's just do a quick example of the bad prompt, right?

**12:37** · Reply to this customer complaint.

**12:39** · And then I'm just going to paste in a random one that I generate here.

**12:42** · And let's see the result that we get here from ChatGPT.

**12:45** · So you can see here it gave us something decent, but it just assumed it was an email.

**12:48** · Even though you know, we didn't specify we want it to be an email gave us something relatively long.

**12:52** · It didn't say it was from the support team. Whatever.

**12:55** · So what I'm going to do now is just make a new chat and let's now do a much more detailed prompt with the same customer complaint so we can say you are a customer support lead.

**13:03** · Reply to this complaint from a paying user whose expert failed twice.

**13:07** · Acknowledge the frustration. Apologize. Briefly.

**13:10** · Confirm we're investigating and offer a concrete next step.

**13:13** · For example, we'll email it in 24 hours, keep it under 150 words and sign off as the support team.

**13:19** · Cool.

**13:19** · So that is our prompt.

**13:21** · Okay.

**13:22** · Notice again the whisper here automatically formatted it for us.

**13:25** · So another important part when you are writing the prompts is that if you structure it well so you have like bullet points for example, different sections, you separate things out into clear sentences.

**13:35** · It's going to be a lot easier for the model to understand what you want and predict the next text.

**13:40** · For example, if we even just do a quick delimiter, like adding these three lines and saying, you know, here is the complaint.

**13:47** · And then putting a colon, it's separate.

**13:49** · So like this is the thing it should be listening to.

**13:52** · And then this is the additional context.

**13:54** · And also notice that I created a new session here in ChatGPT by making a new chat so that it's not automatically going to include the previous text that I had in the conversation in the prompt.

**14:04** · So I'm just going to go ahead and hit enter here.

**14:06** · What I mean is that if I had just run this underneath the other example that I gave, you know, we can still get a decent result, but it's going to be a little bit confused or mixed up with the other conversation history, because that's going to be included in the prompt as well, because ChatGPT will include that as context.

**14:23** · So if we look here, you can see now we get something a little bit more concise.

**14:26** · You know, it says best regards support team.

**14:28** · And it's followed generally what it is that we asked it to do.

**14:31** · Then the next technique you can use is referred to as few short prompting.

### Few-Shot Prompting

**14:35** · Now effectively what this means is that you are going to give a few different examples of input and output pairs that you're looking for, so that when you give the prompt, the model can give you a better reply.

**14:45** · So when you do this, the model can infer and figure out the pattern which it's very good at doing, and then replicate the pattern to give you the exact result that you're looking for.

**14:54** · So this is especially helpful when you want something in a specific format style.

**14:58** · You have various edge cases, and you want to do something like a classification task using an LLF, because limbs are actually very good at classifying things.

**15:05** · For example, like is this email positive or negative?

**15:08** · Is it red or black, whatever, right. All of those things.

**15:11** · But only if they know and have examples to be able to classify that.

**15:15** · And in fact, when you talk about fine tuning LMS, what you're effectively doing is you're passing them a bunch of different examples of inputs and output pairs so they can infer that pattern on top of their base training to give you a more specific, better result.

**15:30** · So let's have a look at a few examples here.

**15:32** · I'm not going to throw them on screen.

**15:33** · Let's just go into ChatGPT and we can do a few prompts and see the result that we get.

**15:38** · So let's do something like turn this user feedback into a short support ticket title.

**15:43** · The feedback is the app crashed when I uploaded a PDF over ten megabits on iPhone.

**15:49** · Okay, and let's see what we get here.

**15:51** · Perfect.

**15:53** · Let's see what it gives us.

**15:54** · Okay, so you can see we didn't really get any clear formatting in this case.

**15:56** · It didn't actually give me one title.

**15:58** · It gave me five because again it's just guessing what to do.

**16:01** · But let's change and do something like this.

**16:03** · Turn user feedback into a short ticket title.

**16:05** · We want this to be under 60 characters, use the format area and then brief description.

**16:11** · Okay. And then I'm just going to paste this.

**16:13** · And then here I'm just going to say here are a few examples of the format that I'm looking for.

**16:17** · Just give me back one line of text that starts with a title and then includes the, area.

**16:23** · And then a brief description of the issue. Okay.

**16:26** · And then we should just say something like this.

**16:28** · And then I can even do, do not return anything other than the title.

**16:33** · Okay.

**16:33** · Cool.

**16:34** · So let's now run this and you can see that I gave a few examples.

**16:37** · So let's actually separate the examples a little bit.

**16:40** · So it's it's a bit easier to see.

**16:41** · And you can see that we have you know feedback long.

**16:44** · It is broken with Google on Safari the title is off okay.

**16:47** · And then Google login fails on Safari.

**16:49** · And then let's go here.

**16:50** · Feedback is export to CSV only. Exports first 200 rows.

**16:54** · The title export right CSV feedback.

**16:56** · The app crashed when I upload a PDF over ten megabytes an iPhone.

**17:00** · This is actually the example that I'm going to pass paste to it in a second.

**17:03** · Sorry.

**17:04** · And I'm going to say like this.

**17:07** · This is the feedback to generate the title for.

**17:13** · Cool.

**17:13** · Okay.

**17:14** · And then it should give us the title and let's see if that works.

**17:16** · Now again I'm being super specific, but I'm just trying to show you that if I give it a few examples, we hopefully will get a better response.

**17:23** · And there you go.

**17:23** · You can see it says upload and then iPhone app crashes on PDFs over ten megabits.

**17:28** · So in this case I was super verbose. But look at the difference.

**17:30** · So we went from this kind of crap here right from the LM to this, which now I could directly plug into like some API or I could use in my app.

**17:38** · And I know that the format I'm going to get from the model is going to be consistent.

**17:41** · And then I could just do something else now because I'm in the same chain.

**17:44** · So let's go.

**17:45** · Like feedback I don't know here.

**17:47** · Let's go feedback and let's change this to say something I don't know what's a good example of feedback.

**17:53** · The keyboard does not disappear when clicking outside of the frame on the login screen.

**17:59** · Okay.

**17:59** · And let's see if we give it if it gives us the title back. Now.

**18:02** · And there you go. You can see it just gives us the title.

**18:04** · And we can now keep doing this in this chain because it has the previous context on how it should behave.

**18:09** · Now the next technique to go over is called chain of thought prompting.

### Chain of Thought

**18:13** · Now this is asking the model to reason step by step before it gives the final answer.

**18:18** · Now this will reduce errors on logic, math, you know, the planning, whatever in different comparisons.

**18:23** · And a lot of models do this by default now, especially if you're using like a planning model or a reasoning model where they're instructions internally.

**18:31** · Right.

**18:31** · Again, like in the prompt that's being created for you in the back end is to actually do this.

**18:36** · So the reasoning models, like they're still using a core line, but they just have some fancy kind of tools and orchestration on top of them to make them do this.

**18:45** · But if you're not using a fancy model like that, then you want to tell it to reason with chain of thought.

**18:50** · So without it, you have something like, you know, store sells pens for $2 and notebooks for $5.

**18:55** · Sarah buys three pens and two notebooks.

**18:56** · She has a 10% off coupon. Coupon? Sorry.

**18:58** · How much does she pay now?

**19:00** · If you don't tell it to reason, it's just going to look at this text and try to predict the result.

**19:05** · Now, in a lot of cases, it will get this wrong.

**19:07** · Just like the famous example of asking them to count.

**19:10** · You know how many teaser and strawberry or something, and it just can't do it unless you change the prompt to tell it how to reason through it so that it actually thinks before it gives you the response.

**19:21** · Okay, so I'm actually not going to show this in ChatGPT because it is probably not going to work or prove the example where I think both prompts will give us a very similar result, just because the default reasoning for like GPT models is already really good, but with some other models where they don't do the reasoning by default, or if you're not using them in the interface like ChatGPT and you're just using it in like an API or something, then you definitely would want to include these kind of keywords, right?

**19:45** · So just anyways, keep that in mind for chain of thought.

**19:48** · A lot of times now the models that are super modern and, you know, state of the art will do this by default.

**19:53** · And actually auto detect what reasoning model they should use based on what you asked them.

**19:58** · But it is kind of worth knowing, especially, you know, six months ago, 12 months ago, this was a lot more important than it probably is right now.

**20:04** · So the next method that is super underrated is structured output.

### Structured Output

**20:08** · Now this is asking the model to provide the output in some kind of format like Json tables, XML, markdown, whatever, and then giving an exact example of what you're looking for such that you're able to parse this and use it in some other format or in some other application.

**20:23** · Now, in my case, you know, I do a lot of development work, right?

**20:26** · And when I have the model generating something, maybe I want to read it into a database.

**20:31** · Maybe I want to display it on the front end of my website, whatever.

**20:33** · In order to do that, I typically need it in some type of structure.

**20:37** · So what I will do is something like what you see right here where I actually provide a Json object schema.

**20:43** · This is what is referred to, which is really just an example of what it should look like to the model.

**20:48** · So it knows how to give me the output.

**20:49** · So obviously compared to the first example where we just said something like this, the main difference is that we're providing the structure and we're telling it that we want it to respond with just that.

**20:58** · No other text in a particular shape.

**21:00** · So we're kind of almost doing this a multi shot prompting right, or few short prompting, but combining it with some kind of output as well.

**21:07** · So anyways, let me go to ChatGPT and just show you a quick example.

**21:10** · So what's something that we can do.

**21:12** · so we can say maybe compare Trello, Monday.com and Clickup.

**21:16** · For a small team of 5 to 10 people, I want to understand the main features, the limitations and the pricing.

**21:23** · And what I'd like you to do is output this with valid Json only.

**21:27** · Don't give me any other text and make sure that it's in this shape.

**21:31** · Okay, so that is what we're going to do here.

**21:33** · Just put that in with whisper.

**21:34** · And then I'm just going to paste in the format.

**21:36** · So we'll just put it like that and we'll say example format like so okay.

**21:41** · So let's run this now and let's see what we get okay.

**21:44** · So just give me the output right now.

**21:46** · But you can see that it's following this format.

**21:48** · It's in a valid Json object.

**21:50** · And now I would be able to load this into my code.

**21:52** · I could store it in a database right.

**21:54** · I can return it from an API.

**21:55** · It doesn't matter. But it is very useful.

**21:57** · And it's going to be a lot better than if you just gave me this random kind of markdown text that ChatGPT usually replies with.

### Constraints & Negatives

**22:04** · So moving on, let's talk about constraints and negative instructions.

**22:07** · So sometimes the best prompts are not talking too much about what to do, but they're talking about what not to do.

**22:14** · Now the more constraints which is saying you know, do this, don't do this, be within this bounds, whatever the better the results you're going to get, because you're steering the model more accurately.

**22:23** · So some examples of constraints is for example the length.

**22:27** · Now you could say summarize in exactly three bullet points.

**22:29** · That's fine. That's a constraint.

**22:31** · You also could say keep the reply under 300 words or under five bullet points.

**22:35** · Right.

**22:35** · You could have a tone like no slang or humor.

**22:37** · Do not apologize. Right.

**22:39** · Do not use bullet points. Use one short paragraph.

**22:42** · Do not suggest paid tools. Do not include code.

**22:44** · Describe the approach only.

**22:46** · So when you do that, it actually ends up listening a lot better sometimes than telling it what you want.

**22:51** · And this has been shown a lot, especially with a lot of the researchers working with these models oftentimes are including a large list of things not to do because it just works extremely well for prompting.

**23:01** · So you don't want to write something like write a short intro for our onboarding doc.

**23:04** · Instead, you would say, write a short intro for onboarding doc.

**23:07** · Start directly with what the user will do in this section.

**23:10** · Do not start with welcome or generic greetings.

**23:13** · And then in that case, you're going to get something that is straight to the point.

**23:16** · So anyways, let's have a quick look at an example here.

**23:18** · If we go inside of something like ChatGPT again, let's make a new chat.

**23:22** · So let's just do something like write a short out of office email reply from me.

**23:26** · Tip okay, so this would be without any constraints.

**23:30** · And let's see the kind of response that we get.

**23:31** · Okay, so ChatGPT actually gave me something interesting here, but it's not really that useful for an out of office email because I need to know, for example, the dates, the time, all of that kind of stuff.

**23:40** · So let's do something better would be, say, write a short out of office reply, start with the exact dates I'm away, and one sentence on who to contact for urgent issues.

**23:49** · Do not use the phrase limited access.

**23:52** · Reply when I can or thank you for your patience.

**23:55** · Be short to the point, but detail enough that people understand when I'm coming back, I'm going to be away from March 1st to March 25th.

**24:02** · Okay, so in this case, again, we've included a few constraints.

**24:05** · So hopefully we're going to get a better response here from ChatGPT.

**24:08** · And let's see perfect.

**24:09** · And you can see that we get a much better email that doesn't include any of the other fluff like, you know, message me if you need to. Limited access. Right.

**24:16** · Which funny enough, we got in this one, but we didn't get here.

### Iterative Refinement

**24:19** · Now the next method to go over is pretty straightforward, and you probably already do this, but it's just to do iterative refinement on your prompts.

**24:26** · So very rarely is the first prompt you send going to give you the desired result.

**24:30** · So rather than restarting simply improve the prompt over and over again until you get what you're looking for.

**24:36** · So as it says here, you know, treat prompting as a conversation, not just a one shot attempt.

**24:41** · The first reply maybe isn't right, so you're going to refine it by saying shorter.

**24:44** · I'd like it more formal. Add another example.

**24:46** · Focus only on X, whatever.

**24:48** · Of course, the better first prompt you give, you know, the better.

**24:51** · But sometimes you just don't know what the result is going to be.

**24:53** · In that case, don't restart.

**24:55** · Just keep going based off the result that you have.

**24:58** · If you're in like a decent enough place now, an example flow here you can see, you know, you dropped a two sentence blurb.

**25:03** · Whatever it returns four sentences a bit salesy.

**25:06** · Hey, cut it to two sentences. You know, make it more factual.

**25:08** · Whatever model tightens it up, add it to work, a Google calendar, whatever.

**25:11** · You get the idea.

**25:12** · I'm not going to show this to you in ChatGPT because I think it's pretty intuitive.

**25:15** · But the point is, be iterative with your prompt.

**25:18** · And then the last method that I'm quickly going to show you, we'll go into some more stuff after is the interview style prompting, which is super powerful and extremely underrated.

### Interview Style Prompting

**25:26** · So I'm just going to read through some of this because it's pretty descriptive.

**25:29** · But instead of guessing what context to provide, give the model the task and ask it to interview you for whatever it is that it needs.

**25:37** · So a lot of times you know, you're not going to be able to provide the best context because you don't actually know what information the model needs to give you the correct result.

**25:45** · You can go off the top of your head, you can guess whatever, but it's actually better if the model prompts you on what it is that it needs, and you go back and forth where it's prompting you and then your prompting it, and you get a much better response.

**25:58** · So you state the goal, and then the model will ask you clarifying questions, and you can answer them one by one, and then it can perform the operation with the full context.

**26:06** · Now it works because we often leave out details, right?

**26:09** · Audience constraints, format examples because we don't know the model needs them.

**26:13** · So if we let them surface that information first, or let the model ask that, it gives us kind of the prompt to then give it all of the details.

**26:21** · And a lot of times we're lazy or we have assumptions.

**26:23** · So again, we just don't include something because we assume the model will know, but it may not actually know that or have the same assumptions as us.

**26:30** · Okay.

**26:30** · So I mean, if you have this talk you can read through here, but what I'm going to do is just go over into ChatGPT and give you an example here of what this kind of interview style would look like in order to get a decent response.

**26:40** · Okay, so let's just read something out here.

**26:42** · I need a short LinkedIn post about 250 words about lessons we learned switching to a four day workweek.

**26:48** · Before you write it, interview me and ask me questions about anything that you need.

**26:52** · So, for example, the audience, company, size, tone, metrics, do's and don'ts, I want you to ask one question at a time.

**26:59** · And then when you have enough information, say, I have enough and give me the post.

**27:03** · Then I want you to write the post and again ask me any questions afterwards for clarifications.

**27:09** · Okay.

**27:09** · So we have the prompt here.

**27:11** · You can see that it's generated.

**27:13** · And now let's see if we can do this.

**27:15** · So great says first question who is the primary audience for this LinkedIn post okay.

**27:19** · And let's say it is founders and CEOs okay.

**27:25** · Let's see what question we get next. Got it.

**27:27** · Second question.

**27:28** · Tell me about your company context.

**27:29** · So the advice doesn't feel too generic.

**27:31** · I run a developer mentorship program where I help developers, you know, land software engineering jobs and a tough market.

**27:40** · And I employ a team of about ten people.

**27:43** · They're mostly remote where they're doing like coaching as well as admin work and some dev work.

**27:48** · For the company.

**27:50** · I'm just making up random stuff right now.

**27:52** · But anyways, you get the idea.

**27:53** · Okay, let's see what else. Get context.

**27:55** · Next question why did you switch to a four day workweek in the first place?

**27:59** · We switch because we wanted to get more flexibility to the employees, and to make them more focused on the four days that they were at work, rather than finding something to do when they, you know, didn't need to be doing that, just spinning random stuff.

**28:12** · Okay, let's see here.

**28:14** · It's actually picked up just spinning random stuff.

**28:16** · So let's remove that, and let's see what we get.

**28:19** · Next question.

**28:20** · What actually happened after you switch overall was a very positive experience.

**28:24** · The productivity went up.

**28:25** · The revenue stayed about the same, but the satisfaction of employees was just higher.

**28:29** · And there was no unexpected problems.

**28:32** · Okay. Let's see what's going to ask me any questions. Okay.

**28:34** · So after this I'm just going to tell it to stop because I don't want to answer more questions.

**28:37** · Use the current information and give me the post.

**28:39** · Don't ask any more questions.

**28:41** · So you can see when I do this, I actually get a very detailed, well-written post that is accurate based on what I told it, rather than a bunch of random AI crap that you guys probably see all the time over social media.

**28:52** · It actually matches, you know, context that we gave it.

**28:56** · So what happened?

**28:56** · Productivity went up, revenue stayed the same, team satisfaction increased.

**28:59** · You get the idea.

**29:00** · So this interview style is really effective and you can get fantastic results by just chatting and giving all of this additional context that you probably never would include by default, especially just in the first prompt.

**29:12** · Okay, so now I'm going to go through a few advanced strategies when it comes to prompting.

### Advanced Techniques & Parameters

**29:16** · So first one to talk about is system versus user prompts.

**29:19** · Now this is more relevant for those of you that are developers.

**29:23** · However in some different applications you will see this notion of like a system prompt and a user prompt.

**29:27** · Now, a system prompt typically sets the identity of the model various rules and style, and it's often not shown to end users.

**29:35** · So this is for always on behavior where any time you talk with the model, it's going to read this system prompt first and understand that this system prompt is designed for the system to look at before answering the user prompt.

**29:49** · So for example, if I want a model that always talks like Mario, you know, I give it a system prompt that says always talk like Mario.

**29:55** · I don't need to say that every time.

**29:57** · It just always reads that.

**29:59** · So in cursor, the app that I'm in right now in chat, GPT and all of these different platforms, they have their own system prompts that they provide to the models to give you the output that you're looking for.

**30:09** · And then when you type the prompt, it gets added to this kind of chain of prompts that's already inside of there, that's building the context of the models or reasoning based off.

**30:18** · So if you have a look here, you know, an example of a system prompt, be like you're a helpful coding assistant, blah blah, blah, whatever.

**30:23** · Whereas the user is, how do I read the first line of a file in Python?

**30:27** · Now if I go to ChatGPT, I'll just quickly show you an example.

**30:30** · So actually if you go to ChatGPT settings, and personalization, you can see that you can add custom instructions, which is somewhat similar to something like a system prompt.

**30:39** · And you can see that I say adopt a skeptical questioning approach.

**30:42** · Take a forward thinking view, be talkative and conversational.

**30:45** · Now I'm going to change this to say, be direct into the points and always talk like Mario when replying to me.

**30:51** · I don't know if that's going to work super well in ChatGPT, but let's see now if we do a new conversation.

**30:55** · Hey, how's your day going?

**30:57** · Let's see if it's actually going to give me something like Mario.

**31:00** · You can see hey Tim, it's good, you see.

**31:02** · So it's actually following like the system prompt here, right.

**31:05** · And giving me a much different response than I would normally get.

**31:08** · Now I need to turn that off. Otherwise that's going to drive me crazy.

**31:10** · So let's just remove the custom instructions for right now.

**31:13** · But you get the idea, okay.

**31:14** · And even these other things like the style, warm, whatever these would be built in to the system prompt that it's going to use when replying to you.

**31:22** · Okay.

**31:22** · Now the next advanced feature to go over is prompt chaining.

**31:25** · Now, generally speaking, it's better to break complex tasks into multiple steps and to use the output of the previous step in the next step.

**31:33** · So rather than just writing a super complex prompt that says like, hey, here are the three different steps that you need to do.

**31:39** · Just do them one by one so that you can verify the result of step one is good before moving on to step two.

**31:45** · So I'm not going to demonstrate this in ChatGPT.

**31:47** · But the example would be like, you know, given topic, whatever output a five heading outline with this Json format.

**31:53** · Okay. It then does that.

**31:54** · Then you say okay based on that result, expand this outline into a 400 word section.

**31:59** · And then, you know, here's the outline that you want okay.

**32:01** · Then you wait for that.

**32:02** · I say turn this draft into, you know, meta title description for SEO.

**32:06** · You get the idea.

**32:07** · So go step by step and break it down.

**32:10** · Rather than having the model do everything at once, that's almost always going to give you a better, more consistent result.

**32:16** · Now, another, more advanced technique you can follow is self evaluation.

**32:20** · So let's say the model outputs something to you.

**32:22** · You can then ask the model to critique or score its own output.

**32:26** · Now sometimes you want to fool the model a bit where you want to maybe start a new session.

**32:30** · You don't want to have it in the same one and say, hey, review this email that I wrote rather than saying, hey, an AI model wrote this, say, hey, I wrote this, and then it's going to give you a more accurate response than if it thinks that it wrote it itself.

**32:42** · So if you have drafts, code, summaries, whatever, you can say something like, here's a short summary I generated. You know, whatever.

**32:48** · Put the text, rate it 1 to 5 for clarity and completeness in one sentence to just the single most important improvement.

**32:54** · And then you can take that improvement and ask it to refine it based on that.

**32:58** · Okay, so super cool.

**32:59** · The evaluation is really good, but make sure you're kind of fooling the model a bit.

**33:02** · And you're not just, you know, in the same conversation chain after it gives you the output saying rank your own reply because it's not going to give you as non-biased of a response as if you ask it in a fresh chain where it doesn't have that in its context already.

**33:16** · Okay.

**33:17** · And then just a few other things to look at here.

**33:18** · So temperature and other parameters.

**33:20** · Now if you're going to work with models in typically an API setting, you're going to have the ability to adjust the temperature of the model.

**33:27** · Now the temperature of the model effectively is the determinism of the model.

**33:31** · Now the determinism means how repeatable effectively is it now something that's deterministic is like okay, if I don't know, open the lid on this pen.

**33:42** · It always opens like it's a deterministic action.

**33:44** · Like if I open this, it's always going to open right?

**33:46** · Whereas if I generate a random number that's non-deterministic because I don't know what number I'm going to get.

**33:52** · And I can get a random number now LMS by default are non-deterministic, which means there's a sense of randomness and you don't know the output that you're actually going to get.

**34:03** · Now you can adjust how deterministic it is by affecting the temperature of the model.

**34:09** · So the lower the temperature is, the more repeatable and deterministic it's going to be, whereas the higher the temperature, the more creative, varied and random it's going to be.

**34:19** · So you would use a low temperature for consistent output, especially if you want something in like a particular format, structured output.

**34:26** · Right.

**34:26** · Code facts, things where there's really just like one clear answer is the sentiment of this, you know, text positive.

**34:34** · That would be a low, you know, temperature, you know, parameter you would want to use there.

**34:38** · Whereas for higher temperature, you use this for brainstorming, varied phrasing, multiple ideas, maybe some advanced planning if it's not really sure, you know how you would get to the result.

**34:48** · And if the outputs are too random, then you can lower the temperature.

**34:51** · But if it's too repetitive, then you can raise it slightly so you know, play with the temperature by default.

**34:56** · It's usually on the lower side on the higher side.

**34:58** · But just know what that parameter means because it does come up a lot when you're working with these models.

**35:03** · So now let's talk about a few common mistakes and how you can fix them.

### Common Mistakes

**35:07** · Now one mistake being too vague right.

**35:09** · What's going to go wrong? Generic or irrelevant output.

**35:12** · How can you fix that at a roll?

**35:14** · Audience tone format potentially length okay, next, too many tasks in one prompt.

**35:20** · So a lot of times you're putting, you know, 100 things that you want it to do.

**35:23** · In that case, the model may, miss something.

**35:25** · You may not actually complete the task.

**35:26** · It might mix them up, whatever.

**35:28** · In that case, split it into steps or separate prompts.

**35:31** · Right.

**35:31** · So chaining like I talked about before.

**35:33** · Now none of context are examples.

**35:35** · So you're going to get like wrong format or style.

**35:37** · So add 123.

**35:38** · Few shot examples include the relevant background.

**35:41** · Or use that interview technique to ensure that you're getting enough context before proceeding.

**35:45** · Another common mistake is that the model ignores the format that you want, which means it can be hard to parse or reuse.

**35:51** · So, like I showed you before, you can explicitly request a specific structure and tell it to only output that.

**35:57** · So Json with keys x, y, z or whatever. Right?

**36:00** · Only give me Json.

**36:01** · Do not give me any text, don't give me anything else. Right?

**36:03** · We're adding the constraints as well as being really specific in what we want and then assuming memory like I said, the model is going to forget the things that aren't relevant or that aren't in the same thread conversation or a context window that you're currently in.

**36:17** · So make sure that you repeat or summarize key facts if the threat is long, or if you're working in a new session, don't assume the model remembers something.

**36:25** · Again, you kind of have to infer like what is the tool that you're using actually doing in the background to load up the model with this context?

**36:32** · Okay, now there's a lot of other mistakes and things that I can go through, but I'm going to leave kind of the rest of the stuff in this document for you guys to refer to if you would like.

**36:40** · Last thing I will say is that it does just make a massive difference to practice this and to prompt a lot.

**36:46** · The more you prompt, the more you're going to see what the outcomes respond to, how you get the best response, and you can prompt more and faster.

**36:53** · If you use a tool like flow, like I've been using in this video, that allows you just to dictate it with your natural voice as opposed to having to type it in.

**37:01** · You guys have seen in this video how quickly I could actually prompt and how much better the response is because I'm using my voice.

**37:07** · So I know yes there partner of mine, but I've been using that for a very long time.

**37:11** · I really cannot recommend it enough, and whether you use them or someone else doesn't matter to me.

**37:15** · But point is, use some kind of dictation tool used on your phone, used on your computer.

**37:19** · Your productivity will skyrocket, especially if you're someone like a developer where you need really long, detailed prompts and you're working with like multiple agents at once, like I am.

**37:28** · So anyways, guys, that's going to wrap up this video.

**37:31** · If you enjoyed, make sure leave a like subscribe and I will see you in the next one.