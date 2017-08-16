---
title: 'How not to do open source'
created: '7-26-2017'
tags: ['open source', 'code', 'github', 'community']
license: 'cc-40-by-sa'
---

It’s the little things that count.   
  
I open a lot of issues on open source repositories. They’re the best way to get in touch with maintainers, and they’re your first point of entry to a new community. Most code bases do not have a Slack group, or an IRC channel, or a Gitter room. They have open issues, and maybe someone who is looking at them from now and again. You could email the maintainer - if their email isn’t in their GitHub profile, it is likely in the commit logs. But that can be seen as invasive, and doesn’t let other people see the issue you logged or the question you had. Opening an issue is the best way.   
  
I want to share two different issues I’ve made this week.   
  
I was going through all of the repositories in the [Divvun](https://github.com/divvun) organization, looking for interesting tools to add to my list of tools that could be used by people working with [endangered languages](https://github.com/RichardLitt/endangered-languages). Divvun is a language lab that does cool work, primarily on Sámi languages from northern Norway. When I ran across [giellakbd-ios](https://github.com/divvun/giellakbd-ios), I noticed that the GitHub description wasn’t as useful as the description in the README. So, I opened an issue. 
  
> Hey there! 👋 Awesome tool.  
> I think the description for this repository could be a better better. I suggest: OSS reimplementation of iOS keyboard with support for localised keyboards. That might be more useful to newcomers than Giella keyboard for iOS.  
> Is this part of Giellatekno? I'm not sure what Giella means, and it is hard to tell from the README.  
> Thanks.  

[Link](https://github.com/divvun/giellakbd-ios/issues/1)  

The maintainer, [@bbqsrc](https://github.com/bbqsrc), an Australian (who else would be online at 5:30am EST?), commented back almost immediately. He resolved the issue, and we had a little conversation about the tool and what could be done for newcomers. He was thankful for the feedback, and encouraged future participation.  
  
Compare this to an interaction I had with [hunspell](https://github.com/hunspell), a [widely used spellchecker](https://en.wikipedia.org/wiki/Hunspell). I noticed there was a new repository of [miscellaneous tools](https://github.com/hunspell/misc-hunspell) in the organization on GitHub. But the README was a bit lacking. I didn’t understand what the repository was, or how to use the tools. So, I opened an issue, with roughly the same tone as the other one I opened.   
    
> Glad to see this repo!  
> It's a bit difficult to know what these are, at the moment. Logging this here asa reminder to fill it out. Feel free to ping me if you need external eyes and aren't sure if it makes sense.  
> Also, adding a GitHub description and GitHub tags to the repository would be nice.  

[Link](https://github.com/hunspell/misc-hunspell/issues/1#event-1178352760)  
  
Two hours later, the maintainer closed the issue, without a comment. No “thanks”, no explanation. He’s pushed some commits since, but hasn’t edited the README or made the repository more accessible to newcomers.   
  
This felt bad. I could ask: “Why did you close this?” But I get the feeling he wouldn’t care. The maintainer clearly isn’t interested in working with newcomers. Am I less likely to be interested in helping out with hunspell in the future? Definitely yes.

The lesson? Don’t close issues without saying why. Be welcoming. Participate. Or you’ll lose people who might be interested in helping you out, in turn.   
  
It’s the little things that count.
