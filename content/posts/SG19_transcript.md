P1997 is a small proposal submitted December 2019 with a quick first revision.
There may be a second revision later this year.
The main author was a student  reading the standard.
14:10:35 I'm not sure who the second author is he's perhaps an academic. But, anyway, the, the paper itself is somewhat academic it.
14:10:46 You know, it includes the wording.
14:10:48 It's been criticized by some people high up in the c++ Committee is lacking motivation.
14:10:54 I can talk to that if we need so the reason why I think this is of interest, the machine learning group is it's related, and the remit here is pretty much rate related when you read it.
14:11:07 Now, this is going back 50 years really fixing an issue from see that then was inherited into c++, that arrays are not regular types, you can't copy them to be fully regular you need to compare as well, a semi regular type is called people.
14:11:24 And that can mostly be fixed and I don't understand why it wasn't done back when Richie made struct comfortable. So for a while in early. See, you would have to copy every single member of a struct when you copy destruct but somewhere between one and
14:11:42 two, structural help people with your rep with a raised hand side.
14:11:44 So that's one place where you get to wake up in the C, and c++.
14:11:48 The other singular cases string literal Wars character array can be initialized from right hand side string literal.
14:12:02 Now, in recent years have been a couple of other cases of array copies have been added, where that is convenient. So, lenders will copy the by value capture of an array structure bindings will copy an array, right hand side, oh sorry I'm not talking over
14:12:22 the paper here at all. That's not included. So there is a nice examples in the paper. So one of the questions that comes up incessantly is, why isn't good enough.
14:12:34 And I don't see that as a relevant question I want good built in a race. I want them in order to build better class arrays. So, I've been kind of working in array related stuff for many years, I did blessing, implementation, many years ago.
14:12:50 I'm kind of in the Python data, ecosystem at the moment, used to do MATLAB
14:12:56 arrays, can be comfortable. I, you know, this paper hasn't seen any, any issues raised against it people haven't come up with any reasons why it won't work.
14:13:07 I've been trying to look at it from, you know, an attackers point of view what what could be wrong with this what doesn't work. I, I know of two small breakages that were discussed with this see.
14:13:22 Okay, so what's the history of this, so 20 months ago, it hasn't seen any interest. I'm the main proponent keep pushing on it, the author has gone on to other things, but it's still kind of keeping his hand in a little probably would be involved with
14:13:35 this, if there's a revision.
14:13:37 So about a year ago, I joined this group, mostly to push rate related things and the SG 22, the newly formed C and c++ liaison group, partly because I realized that they were more likely to be interested in this proposal then c++.
14:13:56 As you know, array is a somewhat to boo within the c++ Committee and community where it's still very central to see.
14:14:03 I mean that's foundational in c++, as well, but it creates something of a two worlds view of and that you know, coming back to standard array, it's kind of typify by standard array.
14:14:16 So what's the problem with standard rate. One of the problems listed in this paper is the initialization issue. So I call this the member array initialization conundrum.
14:14:28 And there is the few kind of work around solutions I've blogged on a few of them.
14:14:35 But the problem is, you have an existing l value array. How do you initialize the standard away with it.
14:14:41 Now we have stood ranges copy. So ranges copy can do can do that for a one dimensional array, but fails, as soon as it is nested, so it won't do it for nested see array.
14:14:53 I believe it won't do it for nested standard right but I haven't tried that
14:14:58 out, I'll try that.
14:15:02 Now, with bit cast you can build custom array and created that way. But, you know, standard rate was standardized with c++ 11 but really came from boost 10 years before that.
14:15:13 And it's you know an early example of a way of wrapping horrible see and giving it to c++ facade or API to work with the other algorithms. That's not necessary now in c++ 17 we got data and science free member functions, along with the existing data and
14:15:50 data science. Yeah.
14:15:42 Yeah. So, oh beginning End Of course. So, you know, all of those three functions, interoperate fine with a radius and built in arrays also have a specialization for stud swap.
14:15:55 So, effectively, you know that's a, an old range algorithm that will copy even nested array is properly recursive Lee.
14:16:02 I'm drifting off again. So, standard rate in c++ 20 we got standard to array, which will take an array of value and create a standard array from it. But what wasn't noticed is that in the is Luke here, yeah.
14:16:20 Oh yeah, look see So Luke noticed a couple of months ago that the earlier experimental maker Ray was able to make zero sized standard array.
14:16:27 But to array cannot do that because it's converting built in and ready to a standard rate you can't have a zero size built in array. So, so you know one of the advantages of standard rate is that it's got the zero sys specialization.
14:16:45 And then one of the downsides, is it needs to zero size specialization so every array class you right you have to do as he works on a specialization. And it's a little tricky to write, it's easy to get wrong.
14:16:56 And there's several of the standard library implementations got it wrong and had issues raised against it.
14:17:01 But anyway, I'm rambling again I guess so.
14:17:04 The history then so it got viewed, but it got raised on the liaison mailing list and was discussed, a month ago was August the sixth.
14:17:14 It holiday season. So, that partly member to dissenting voices are not dissenting there was some concern raised at the highest levels.
14:17:25 Worried of WG 21 didn't make it to the meeting, but sent messages to the reflector with, you know, unspecified concerns that when arrays have been dealt with.
14:17:37 When it's been attempted to improve it raised in the past, it's led to difficulties.
14:17:44 So that's what I want to drill down on you know I'm so, so what came out of that meeting is we need implementations we need compiler implementations. So, the paper has been forwarded to EWG, but it's not worth doing, until we have implementation experience.
14:18:00 And similarly on the sea side wg 14. I've got much stronger gating they require implementations.
14:18:09 So, I happen to have a few weeks, open before contract, that's coming up in mid October, so I volunteered to do the planning and GCC implementations.
14:18:22 And that's what I've started on this, this week.
14:18:26 I don't think we have any other clan guys here it was William Moses and the, the array, the young, the calculus guy is like do to have some sessions with them on the VM side.
14:18:39 Oh yeah, so there's a bunch of Tony tables that are worth looking at. So what does it propose the initialization is fairly simple that you can initialize an array from an array, right hand side.
14:18:52 Then copy. If you have to raise a and b. Now you can just do A equals B, and you get the copy.
14:19:00 Then a little trickier perhaps that's placeholder semantics. So, an auto.
14:19:09 We are playing array will declaration will deduce the element type.
14:19:16 Now that interacts a little oddly with existing language features, and there's a c++ 20 edition. That allows pointers or references to incomplete arrays to be initialized from array is with no deduction going on there.
14:19:30 So that's an template deduction with all with auto attack. So anyway, the placeholder is one possible area of dragons. The other possible area is praised initialization.
14:19:42 You know the code for that and GCC is pretty horrible I've dived into that before. And I'm sure the same is true in clang.
14:19:49 And it's different also between C and c++. So at the moment I'm focusing on the c++ implementation of this
14:20:00 array return from function in fact yes that's the main thing that I kind of got into this foreign, and wanting.
14:20:07 So, that change. I believe will be easy enough to implement, but it then leads to Abi, that this is a new API for both C and c++, and for the wider foreign function interface world.
14:20:21 And that's obviously going to take time, you know, there's so many platforms, especially on the, on the sea side of things, and, you know, who are the API people, they think that meeting some smoky room.
14:20:33 So even find out who they are and how this how this happens, is likely to take some time.
14:20:43 So I guess I'm up to 10 minutes so if if there are any questions we can spend five minutes or so before the next papers.
14:20:51 At the end of this will this make or break a regular type.
14:20:56 Sorry Sagan with this make array regular lets me know it will make it mostly semi regular. So, this. So the problem is with array parameter types or formal parameter types.
14:21:10 So, for the liaison meeting. The authors were keen to discuss it, but the extremely strong feedback was just let's not even discuss it because this proposal will be sunk.
14:21:21 If we talk about passing arrays by value two functions. The syntax is broken and see an array parameter in either a function or a template argument list gets adjusted to the point to type.
14:21:37 And there's nothing you can do about that. Actually, there is on the template argument side and this is something I'm thinking of amending revising the proposal with.
14:21:48 So, in a function you cannot declare an argument with dental type auto, you know, auto works but that gives you a decay copy of the argument that will type of auto with an array argument will deduce array.
14:22:01 But then as a function argument that will be interpreted as an array as the element pointer and, but in a template document list, you can actually use deco type auto that's allowed you pass it in a way it will produce an array.
14:22:17 But then the array can't be initialized.
14:22:20 It will be really nice if you could do that with string literal because it gives you for free.
14:22:25 You know strings as template arguments, which is what people will be finally getting with static string, this is you know you can already do that in c++ 20 but this allows you to use a built in a way to do that, and potentially, you know, arrays of integers
14:22:40 or floating point numbers, or whatever. So in fact, that only requires a tiny change in the wording for what constitutes a structural type, because that is the requirement on non tight template arguments now.
14:22:56 And TTP is I should say.
14:22:59 And so, Has this been reviewed by any c++ groups.
14:23:05 No.
14:23:06 Okay, except the liaison group officially counts as.
14:23:10 Yeah. Okay, so it was passed over. Because, so December 2019 was a was a tricky period because right after that we got shut down. So, if it's not on anybody's radar is this or no I mean I talked to friends about it because he you know he frequents this
14:23:30 group as well as SG 22.
14:23:33 And he's written a rave related papers in the past, you know after the Vla the array study group debacle. He, he wrote the last paper on killing and helping this and what has he said, is he.
14:23:47 I'm not sure so he before the liaison meeting he sent out a strange message saying why are we talking about this, I don't think he realized it had been on the agenda, but also when I, when I said well it's been you know it hasn't been looked up to 20
14:24:02 months he said, That's usual for c++ proposals small proposals like this go in and unless somebody is pushing it, it's not going to get seen.
14:24:13 So, it hasn't had sufficient inspection from language experts, and I would really like to get that done before the labor that really needs an examination from the design people like so this needs to go through evolution.
14:24:29 working group.
14:24:31 So that's so it's it's do for evolution working group, and the implementation is what is required to make it worth going there.
14:24:39 So hopefully, by early October I'll have something by mid October, enough to move it to EWG while that might be true.
14:24:49 Your, yo, yo, you might also be your, you're also risking the idea that evolution can change this significantly on you, or just rejected outright. And then you might not have anything to you might have wasted some time right so that's true.
14:25:04 And, you know, that was flagged up in liaison as well.
14:25:08 But somebody needs to do this, I'm not, I'm not the best I'm a hacker I can dive in. I've done a couple of PC patches in the past. I'll give it my best go yeah and and the fact that the fact of doing it will allow you to find, you know some some some
14:25:24 of the answers that this paper is posing and, you know, maybe it should smoke, it should smoke out any issues, and hopefully quell the third because you know there is fear, uncertainty and doubt being spread.
14:25:36 And this will get more certainty.
14:25:40 So, at the end of the day, if this works then you're going to be able to copy a raise to raise directly, without going through some sort of loop. Is that is that right that's right and then it happens to kind of mend a whole bunch of standard algorithms
14:25:58 that are the moment it doesn't make sense to pass a raised because they will fail. So you know ranges is pretty good but as soon as you get to multi dimensional raise it fails, or once you go past the level where you need now value it will fail, I think.
14:26:12 So this just makes it more robust. There's also a c++ 23 proposal to allow braced initialization in more standard algorithms, and that will just work with a radius once, once this is done.
14:26:27 And I think.
14:26:27 Recently, that was a cosmetic change that allows you to do square brackets with, with commerce, to be to be parsed properly as an array.
14:26:39 Sorry, I missed that, this, this.
14:26:43 So this is a paper by.
14:26:46 I'll have to dig it out later it was put in.
14:26:49 My name is Mark Coleman.
14:26:55 No, I'm thinking of another paper this is
14:26:55 I braced initialization in standard algorithm.
14:26:59 Yeah, I know. Yeah.
14:27:02 But yes, I'll check check this afterwards and send out links. Okay, thank you.
14:27:08 Okay, I mean this is this is only the start.
14:27:12 You know, we make it a semi regular, and then there's a bunch of other things that improve things more, like this one, you know that what you're getting into, because if you don't put push this through EWG first, and then do an implementation, while that's
14:27:27 that. That is really helpful it snot smoking out the, the Gremlins you, you know, ew, you might totally reject this or change it. So just be careful.
14:27:40 I mean, I mean, I'm interested in any opinions from the group here as well if anybody thinks either this is crazy or this is great, please drop me a line.
14:27:48 If anybody sees any issues especially. Great.
14:27:54 And yes thanks for that heads up Michael Yeah that's it some hopefully people will have a bit of a chance to look at I mean arrays is of interest to a lot of people, I would say, especially the high performance computing people and of course by influence
14:28:07 the machine learning people, it would be it would be good if you can pass this to people like Mark Coleman.
14:28:14 Yes, I've talked with him in the past. Yeah, see what he thinks, because they you stay as he is still firmly involved in high performance computing.
14:28:24 Anybody who's doing work in the US National Labs, especially some of the high performance computing labs. So sure, Andrew might be interested who was on the call.
14:28:40 Maybe, Devon Devon Lieber at all gone Nevin Yes, yes, so yes I dropped Andrew line earlier in the year actually along with the other. Some of these guys, they have time they might end and they care, then they might actually take a look.
14:28:50 I think you have to tread a little bit more carefully on that on paper on display but as you said this. This area has lots of Gremlins, and there's a lot of people who have historic antagonism towards any kind of work towards standard on standard array
14:29:03 and still the rest right yes it's almost to do it feels, and I didn't make any friends. So, the last time I was here, I had a rant about p 2128, the multi dimensional array subscript operator.
14:29:15 And we should have a one minute silence because yesterday that was voted to call in do. Yes.
14:29:23 So, you know, I probably didn't make any friends by opposing that but in the end I didn't publish the paper, and it's gone in the world hasn't ended. Okay.
14:29:32 It's good to know. Good to have you bring this to our attention, just to make sure. But, but yeah, this is, this is full of potholes I suspect, in some ways, but if it works, it is it will challenge one of our biggest
14:29:46 areas that we've been having troubles with and that's why we've tried creating replacements for story.
14:29:53 There was an attempt that there was an array subcommittee The reason Yes, his name is so prominent involved in it was because yes he cares about this.
14:30:00 And he was actually chairing this array.
14:30:04 Working Group subgroup.
14:30:06 Okay, which got terminated because they ran into this huge problem with this new design of a library type array which can switch between the heat, and the stack, which was amazingly incredibly difficult to implement.
14:30:23 Yes, I tried to follow the history of that I don't have the reflector access, but I followed the history of that working group and you know went right back to the earlier see groups as well to follow the history of this as far back as I could.
14:30:37 And Yano was deeply involved in this as well, too, he in fact proposed one of the proposed solutions. And I don't know if you can get on his attention on this.
14:30:50 Yes, I've tried, I've opened channels with him and his main feedback is, it's poorly motivated. And this just general concern that when it's kind of in the past it's caused issues.
14:30:59 So you've got a lot of. You don't say you got almost everything covered which is good. I written up more motivation, but to me that's not the most important thing I know why I wanted.
14:31:10 And I'm just ahead of the curve, no problem, that's that's why a lot of us are here, ahead of the curve and that's that's okay.
14:31:16 All right, anything else in the group. Anybody have any questions and things like that on this issue
14:31:25 here hearing none.
14:31:26 Well, thank you.
14:31:29 Well, thank you for for letting me get the news. Yeah.