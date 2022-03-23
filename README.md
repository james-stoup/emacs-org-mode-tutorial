
# Table of Contents

1.  [The Beautiful Nightmare that is Org Mode](#org71b303a)
    1.  [Why learning Org Mode is so hard](#org72d4730)
2.  [Workflows](#org7a2ed94)
    1.  [How this guide is trying to solve these problems](#orgc8bc92c)
    2.  [Understanding workflows](#org3201645)
        1.  [Understanding your workflow options](#orge9b5494)
        2.  [Figuring out your first workflow](#orgd93b974)
3.  [Configuring Org](#org5e18e8f)
    1.  [Before you start](#orgec4eef0)
    2.  [Default settings](#org17f46ff)
    3.  [Configuration #1 - Work Log](#org8db505c)
        1.  [Capture Template](#orgc61dd8e)
    4.  [Configuration #2 - Simple Note](#org29e6d60)
        1.  [Capture Template](#org12042d5)
    5.  [Configuration #3 - General TODO](#org5920824)
        1.  [Components of the TODO Item](#orgf95e5eb)
        2.  [Explanation of the TODO Workflow](#orgb083abf)
        3.  [Capture Template](#orgf28d918)
        4.  [Org States](#orgc556a65)
    6.  [Configuration #4 - Programmer TODO](#org7b8b471)
        1.  [Tracking Bugs](#org4877dbd)
    7.  [Configuration #5 - Meetings](#org9989588)
    8.  [](#org4458dda)


<a id="org71b303a"></a>

# The Beautiful Nightmare that is Org Mode

So you want to learn ogr mode? Well god help you. Welcome to the circus.


<a id="org72d4730"></a>

## Why learning Org Mode is so hard

Learning Org Mode is so challenging because it is so complex that it easily becomes overwhelming. In learning about Org Mode I've found that it is often presented to new users as an impenetrable whole with no obvious starting point. The intro guides frequently describe basic functionality and then reference custom configurations by advanced users that are breathtaking in their scope and complexity. No path is given to go from novice to expert other than vague advice and useless platitudes. Most often you will hear variations on "just play with it until it makes sense".

That sentiment is, to put it bluntly, some serious bullshit.

Imagine if you read a tutorial for building a house and by the end of it you had constructed a small square house containing a single room with a window on each wall and a standard angled roof. It had a front door, carpet, paint on the walls, etc. It was technically a house, but it wasn't useful in any way. After all, a house has to have things like electrical outlets, plumbing, multiple rooms, etc. So then you decide to take the next step and build a usable house. Unfortunately the tutorial doesn't tell you how to build a three bedroom rancher, but after some searching you find links to other people's houses. Naively thinking you can draw inspiration from them you glance through their plans. And you discover the following homes:

-   a 50,000 square foot mansion with 5 swimming pools and a helo pad
-   an inflatable 1,000 square foot camping enclosure
-   an underwater sealab capable of withstanding the crushing pressure of the deep sea
-   a large bus that has been converted into a drivable home

And so from these pieces you try to assemble your own home. And what you end up with is more that a little weird. You just copied some pieces from each design and so you have a house with wheels attached to it even though it doesn't move. You don't want the wheels but every time you try to remove them, the electrical system doesn't work. You don't want a pool in your yard but you liked the grass around the pool and you can't figure out how to separate the two so you now have nice grass and an empty pool. And so on and so on. Periodically you go back to the house building manual but they don't tell you how to build a 1 story rancher, they do however have 900 pages dedicated to different light switches and the various ways you can install and configure them.

That is what learning Org Mode is like. 

Other tools might have a setup wizard, sample configurations, or other tutorials to ease you into the software. However Org Mode is designed to be an open ended framework within which you the user can construct your ideal workflow. In this regards it is simpler to think of Org Mode as a programming language within Emacs. It is no wonder than adoption of this tool is so difficult. If you aren't already a programmer (one with lisp experience no less) you will find Org Mode has a brutal learning curve.

As a senior software engineer it took me almost 6 months of working with Org Mode before I was happy with the results. In my initial 2 months I was barely productive with it because I didn't understand what it could do and, more importantly, I didn't know what I wanted it to do. I feel like most people who try to use Org Mode find it to be so frustrating due to its complexity that they  ultimately give up on it entirely. And this is a shame because this is a fascinatingly useful piece of software.


<a id="org7a2ed94"></a>

# Workflows

The part that everyone skips over. Org Mode was so difficult for me to learn because I started this process backwards. I started trying to use it before having any idea of what I actually wanted it to do. 


<a id="orgc8bc92c"></a>

## How this guide is trying to solve these problems

Understanding org mode is a two fold process. The first step is developing a tentative workflow that works for you. The second step is figuring out what parts of org mode will support that workflow.

This guide tries to help you discover a workflow that best suits you. Then a few common org configurations will be given to show how they can support different parts of a work flow. Finally everything will be modular so that a new user can pick and choose what they want to incorporate into their system. This is not meant to be a comprehensive list of every possible workflow or feature, but rather some common examples for new users to build on.

So, let's dig into the problem.


<a id="org3201645"></a>

## Understanding workflows

Most websites with Org primers offer a very detailed org configuration that supports their very specific workflow. And this is great for them, but not for your average user who might only care about 10% of that particular setup. But since it is presented as one unified whole, it can be difficult to separate out which pieces you want vs which pieces will break things for you. So before we can start writing any configuration code we need to step back and ask ourselves, what should our workflow look like?

I'm going to use this term "workflow" a lot in this document and to prevent any confusion, let's clearly define it now. A workflow is the sum of all the steps you take when processing information with Org Mode. Everything you do that ultimately is meant to interact with Org Mode is part of your workflow.

For example, here are two workflows, one for my personal life and one for my job:

**Personal Workflow**
"I want to keep a journal of my thoughts, track home projects, and plan out my personal programming endeavors."

**Professional Workflow**
"I want to track my accomplishments at work, organize the tickets I have been assigned, record data produced in meetings, summarize everything, and display metrics of my productivity."

When thinking of your own workflow, start off by filling in the sentence "I want to use org mode to <span class="underline"><span class="underline"><span class="underline"><span class="underline">\_</span></span></span></span>"

Before you can write any configuration code or really get any use out of Org Mode you need to clearly define your goals.


<a id="orge9b5494"></a>

### Understanding your workflow options

So here we are. You want to use Org Mode to do&#x2026;something. You aren't totally sure what but a lot of really smart people seem to think it is useful so you want to give it a try. And so you did what most new users do. You read the startup guide, you skim the docs, you realize you don't understand anything, and shortly thereafter you gave up in despair.

But not today. Today is going to be different.

So let's start off the right way by first brainstorming some ideas on how you want this whole thing to work. Initially you should focus only on establishing the simplest version of your own workflow. Go into this assuming that this is going to change and that nothing here is set in stone. Instead, treat this as a first draft that will get thrown away, redesigned, or heavily modified as you further understand what it is you really hope to get out of Org Mode. Look through the following list and see if any of these things are something you would want to integrate into your new Org Mode workflow.

Common Workflow Components

-   handling emails
-   recording meeting notes
-   tracking time sensitive events
-   tracking reoccurring events
-   general to-do items
-   journals
-   work logs
-   prioritizing tasks
-   tracking your time
-   generating reports
-   outlining presentations
-   outlining a book
-   tracking JIRA tickets
-   tracking bugs in code
-   exporting documents to common formats

And so on and so on.

As a side note, something that took me a while to wrap my head around was that not everything has to be interconnected. So if you want to keep a journal, there is no reason that it has to be integrated into anything else. Where as you might want to keep your meetings in one file, your TODOs in another, and reference both of them in your agenda view.


<a id="orgd93b974"></a>

### Figuring out your first workflow

So at this point you should take a look at the list above (which is by no means meant to be taken as comprehensive) and decide what pieces you want to implement. I'm not going to implement every one of these examples (that would be a small book and I'm not *that* committed to this enterprise) but I am going to implement several of the more important ones and hopefully that will serve as a foundation on which to build your own workflow.

Once you figure out what you want to do, starting thinking of the simplest way that you would like to reorganize your workflow to incorporate org mode. For example, don't do this:

"what are all the steps required to interface with my email client, import my emails, tag them, create TODO's from them, and then sort them in my Agenda View&#x2026;"

and instead do this:

"I want to make TODOs based on my email"

Note that the second one doesn't require any fancy configuration. Of course, this means that there are going to be a lot of manual steps, BUT THAT IS OK! So in this example, imagine that you come up with the following work flow:

**New possible workflow**

-   open gmail in my web browser
-   look at my unread messages
-   open up emacs
-   create a new Email TODO
-   fill in all the details by copy and pasting into emacs
-   do this for a week
-   live my best life

Now I get what you are thinking. This is a lot of work. This is boring. This isn't leveraging anything! Where is the magic I was promised?

I feel you, I really do. But we aren't there yet. This step is all about seeing if this prototype workflow is actually going to be useful. If it is then great! You can go down the road of turning emacs into your own email sorting hub. But you might do this for a few days and realize that you really don't get that many TODOs from your email, but instead you get them from meetings and then people just email you later to confirm details. So maybe making your emails the center point of this workflow isn't what you really need.

Unfortunately there is no shortcut here. You just have to try a bunch of things out and see what clicks for you. Everyone has different needs and this is most definitely not a one-size-fits-all type of solution. But the key here is to try different approaches, do it all manually so you have minimal investment (think of how frustrating it would have been to spend 10 hours configuring your mail settings only to never use it), and then refine the parts that work for you.


<a id="org5e18e8f"></a>

# Configuring Org

Now we get to the heart of things.


<a id="orgec4eef0"></a>

## Before you start

So you have looked at my list, maybe picked a few pieces out you want to try, thought about how your own workflow should work and now you are ready to configure org. Ok, let's do this. First, if you have not done so, you should check out [Org Mode Quickstart Guide](https://orgmode.org/quickstart.html). It's ok if you haven't memorized all of this yet, just keep that page open in your browser and reference it until things start to make more sense. Also, it is really going to help if you have some working knowledge of emacs configuration. You can muscle your way through this if this is your first time, but this is definitely not the package you want to be your introduction to Emacs.


<a id="org17f46ff"></a>

## Default settings

Listed below are some default settings that I use for Org Mode to make my life easier. You can find all of my settings in the .emacs file that is in this repo if you are curious. There are lots more that I will cover later, but for now here are some basic ones to get you started. Copy these lines into your .emacs file or where ever you keep your configurations.

**Default Org Mode Settings**

    ;; Must do this so the agenda knows where to look for my files
    (setq org-agenda-files '("~/org"))
    
    ;; When a TODO is set to a done state, record a timestamp
    (setq org-log-done 'time)
    
    ;; Follow the links
    (setq org-return-follows-link  t)
    
    ;; Associate all org files with org mode
    (add-to-list 'auto-mode-alist '("\\.org\\'" . org-mode))
    
    ;; Make the indentation look nicer
    (add-hook 'org-mode-hook 'org-indent-mode)
    
    ;; Remap the change priority keys to use the UP or DOWN key
    (define-key org-mode-map (kbd "C-c <up>") 'org-priority-up)
    (define-key org-mode-map (kbd "C-c <down>") 'org-priority-down)
    
    ;; When you want to change the level of an org item, use SMR
    (define-key org-mode-map (kbd "C-c C-g C-r") 'org-shiftmetaright)
    
    ;; Hide the markers so you just see bold text as BOLD-TEXT and not *BOLD-TEXT*
    (setq org-hide-emphasis-markers t)
    
    ;; Wrap the lines in org mode so that things are easier to read
    (add-hook 'org-mode-hook 'visual-line-mode)

**Optional Org Mode Settings**
I really like how this makes my layout look, but your mileage may vary so that's why I'm tagging this as optional.

    (let* ((variable-tuple
            (cond ((x-list-fonts "ETBembo")         '(:font "ETBembo"))
                  ((x-list-fonts "Source Sans Pro") '(:font "Source Sans Pro"))
                  ((x-list-fonts "Lucida Grande")   '(:font "Lucida Grande"))
                  ((x-list-fonts "Verdana")         '(:font "Verdana"))
                  ((x-family-fonts "Sans Serif")    '(:family "Sans Serif"))
                  (nil (warn "Cannot find a Sans Serif Font.  Install Source Sans Pro."))))
           (base-font-color     (face-foreground 'default nil 'default))
           (headline           `(:inherit default :weight bold :foreground ,base-font-color)))
    
      (custom-theme-set-faces
       'user
       `(org-level-8 ((t (,@headline ,@variable-tuple))))
       `(org-level-7 ((t (,@headline ,@variable-tuple))))
       `(org-level-6 ((t (,@headline ,@variable-tuple))))
       `(org-level-5 ((t (,@headline ,@variable-tuple))))
       `(org-level-4 ((t (,@headline ,@variable-tuple :height 1.1))))
       `(org-level-3 ((t (,@headline ,@variable-tuple :height 1.2))))
       `(org-level-2 ((t (,@headline ,@variable-tuple :height 1.3))))
       `(org-level-1 ((t (,@headline ,@variable-tuple :height 1.5))))
       `(org-document-title ((t (,@headline ,@variable-tuple :height 1.6 :underline nil))))))

Change the height multipliers to suite your own tastes. This is what works for me, but you may want them larger or smaller. Either way, put all of that into your .emacs file, relaunch emacs and let's roll.


<a id="org8db505c"></a>

## Configuration #1 - Work Log

I find it very helpful to keep a daily log of what I accomplish at work. Before we get too deep into this, it is important to point out that this is not a journal. There are already tutorials and packages on how to use Org Mode as a journal. So if that is what you are actually looking for, go ahead and skip this one.

In this case a journal contains daily entries that are typically several paragraphs of text while a work log is several bullet points of accomplishments with additional detail as needed.

So here is what I want:

[work log screenshot](images/work-log-screenshot.png)

And here is the code that needed to make this work:


<a id="orgc61dd8e"></a>

### Capture Template

When the capture template is initiated the capture key should be "j". I set it to "j" because I use a journal at home and I wanted to just associate the "j" key with "write a log of my thoughts" regardless of whether I'm at home or at work. But if you wanted to change this to a "w" I won't hold it against you.

    (setq org-capture-templates
          '(    
            ("j" "Work Log Entry"
             entry (file+datetree "~/org/work-log.org")
             "* %?"
             :empty-lines 0)
            ))

This is going to save all of my work logs into the `work-log.org` file using the date structure shown in the picture above. For details on how to modify that structure look up `org-capture-templates` in the manual. 


<a id="org29e6d60"></a>

## Configuration #2 - Simple Note

This is my dumping ground for trivial pieces of information. Things like the password for the supply closet door, where I left that obscure part that I will need one day, or some important piece of trivia that I keep having to look up. There are no tags, filtering, or automatic-anything here. This is the most basic Org Mode example I can think of and I'm including it here mainly for reference.

[random notes screenshot](images/random-notes-screenshot.png)

Here is the capture template:


<a id="org12042d5"></a>

### Capture Template

If you wanted to use this along with the work log capture template from above, then you would only need to copy in the small subsection, not the entire chunk starting with `(setq org-capture...` in case that was not clear. Otherwise, here is the template for a basic note.

    (setq org-capture-templates
          '(    
            ("n" "Note"
             entry (file+headline "~/org/notes.org" "Random Notes")
             "** %?"
             :empty-lines 0)
            ))

No date structure needed here, just a long list of random notes. If you wanted to use the same file but add another heading called "Door Codes" you could then configure another capture template like so: 

    (setq org-capture-templates
          '(    
            ("d" "Door Codes"
             entry (file+headline "~/org/notes.org" "Door Codes")
             "** %?"
             :empty-lines 0)
            ))

And then all of the notes captured from that would go into that heading. 


<a id="org5920824"></a>

## Configuration #3 - General TODO

Now we are getting to the heart of what makes Org Mode so amazing, the ability to track TODO items! To fully explore this feature is going to require several configurations, however I am going to start off with a simple "General To-Do" item and then layer more functionality onto it in later steps. In the Agenda section we will review how to organize all of our TODOs, but right now we are focusing on simply creating them.

[general tasks screenshot](file:///home/jstoup/org/images/general-tasks-screenshot.png)

We are going to look at one TODO in particular.

    * OBE [#B] Talk to Mike and ask about broken restores
      CLOSED: [2021-11-15 Mon 13:09]
      - State "OBE"       from "IN-PROGRESS" [2021-11-15 Mon 13:09]
      - State "IN-PROGRESS" from "TODO"       [2021-11-09 Tue 15:13] \\
        Wrapping this into CCRS-4453.
    
      Namely, what do do when a restore fails. Do we just leave it in whatever state it is in?

There is a lot going on here so I'm going to break it down in the various components. Here is what this TODO is comprised of:

    * STATE [#PRIORITY] TITLE
      - STATE CHANGE 2              TIMESTAMP
      - STATE CHANGE 1              TIMESTAMP
        NOTE ABOUT STAGE CHANGE 1
    
      NOTE ABOUT TODO


<a id="orgf95e5eb"></a>

### Components of the TODO Item

Let's look at each piece one at a time.

1.  STATE

    In this TODO it is set to "OBE" (overcome by events). Other TODOs are set to "DONE", "TODO", or "IN-PROGRESS". We will setup these states in just a minute, but for the moment all you need to know is that each TODO can cycle through several states.

2.  PRIORITY

    Each TODO can have a priority. You can create your own set of priorities such as [DEFCON 1, TROUBLE, MILDLY-BAD,SAFELY-IGNORE] but the defaults of [A,B,C] work just fine and it is what we will be using here. In this case "A" is the highest priority and "C" is the lowest. Don't worry too much about this yet, this will make more sense once we get to the agenda view.

3.  TITLE

    This is the name of your TODO that is entered from the capture menu.

4.  STATE CHANGE 2

    The latest state change. As we see it went from "IN-PROGRESS" to "OBE" and a timestamp was recorded when this occurred.

5.  STATE CHANGE 1

    The initial state change. The TODO went from in the "TODO" state to "IN-PROGRESS" and a timestamp was recorded when this occurred too.

6.  STAGE CHANGE 1 NOTE

    When work was started on this TODO and the state changed, a note was added as a form of documentation.

7.  NOTE

    And here is where all the details go. This could be much more involved, but for this example it was reduced to a single line. so


<a id="orgb083abf"></a>

### Explanation of the TODO Workflow

The general idea behind all of this is to capture a TODDO item, assign it a priority, and save a detailed description of what needs to be done. Once that is recorded we can revisit this TODO at a later date and begin working on it. Once work has begun the state changes to "IN-PROGRESS". When that happens the user is prompted to write a small note (this is not required, you could leave it blank) and a timestamp is recorded of when the state change happened. Finally, once the work has been completed, the note can be set to a done state. In these examples the done states are `DONE`, `OBE`, and `WONT-DO`. But we are getting ahead of ourselves. First let's look at how this was accomplished.


<a id="orgf28d918"></a>

### Capture Template

A general TODO item is captured with a "g" from the capture template buffer. All of the TODOs are saved to the `todos.org` file under the `General Tasks` heading. You can see that the initial state is set to `TODO` and the initial priority is set to `B`. Along with all of this I've added an additional field called `Created:` which adds a timestamp for when this TODO was created. We can filter on that later, but it is simply an optional piece of meta data that you might want to include.

    (setq org-capture-templates
          '(    
            ("g" "General To-Do"
             entry (file+headline "~/org/todos.org" "General Tasks")
             "* TODO [#B] %?\n:Created: %T\n "
             :empty-lines 0)
          ))


<a id="orgc556a65"></a>

### Org States

By default Org only sets up two states, `TODO` and `DONE`, which by and large isn't very useful. There are so many more nuances we could capture! In fact, we shall do so now. Here are the states I've setup for my workflow (and remember I'm a programmer, not all of these will apply to you) that I find very handy.

    ;; TODO states
    (setq org-todo-keywords
          '((sequence "TODO(t)" "PLANNING(p)" "IN-PROGRESS(i@/!)" "VERIFYING(v!)" "BLOCKED(b@)"  "|" "DONE(d!)" "OBE(o@!)" "WONT-DO(w@/!)" )
            ))

So as you can see here I've got eight different states setup. Five of these states are active states with the final three being inactive. The idea behind this is that a task is created, work is begun, and finally it concludes. Along the way the work could require verification (possibly from someone else) or be blocked completely. Eventually it will reach an end state and become inactive. Ideally the task will have been successfully completed and we can mark it as `DONE` but it may be that in the course of working this it no longer becomes a priority. At which point it can be marked `OBE`. Finally, it is possible that after further review, you decide you don't want to work on this. Maybe it no longer matters, it is someone else's job, or you just changed your mind. Either way, you never want to just delete something because you always want a log of what you've been working on. Thus it gets set to `WONT-DO`.

If you are curious about the extra characters in the parens then you can look in the documentation for the exact details as well as other configuration options. But the short version is that they signify to Org which key to use for shortcuts, some prompt the user for a note, and some record a timestamp. In this example, when you set it to `IN-PROGRESS` it prompts you to record a note and then records a timestamp. As it is possible that when you start a new task you want to record some initial thought however setting it to the `VERIFYING` state does not because it is assumed no note is required. Likewise when you set it to `DONE` it just records a timestamp, but setting it to `OBE` or `WONT-DO` requires a note because you should explain why you aren't going to complete this task. 

Finally, if you have been following along, editing your own config file to match my changes, you might start to notice some differences. Your files look flat and my examples all look nice and sexy. What is going on? Well I've decided to add some color to my life to improve my Org experience. Don't worry, you can easily spice things up by telling Org that you want to set custom colors for your TODO states. Simply add this in to your config and tweak the colors as needed:

    ;; TODO colors
    (setq org-todo-keyword-faces
          '(
            ("TODO" . (:foreground "GoldenRod" :weight bold))
            ("PLANNING" . (:foreground "DeepPink" :weight bold))
            ("IN-PROGRESS" . (:foreground "Cyan" :weight bold))
            ("VERIFYING" . (:foreground "DarkOrange" :weight bold))
            ("BLOCKED" . (:foreground "Red" :weight bold))
            ("DONE" . (:foreground "LimeGreen" :weight bold))
            ("OBE" . (:foreground "LimeGreen" :weight bold))
            ("WONT-DO" . (:foreground "LimeGreen" :weight bold))
            ))

That is it for TODOs. Save your config, reload, and test everything out. Tweak things until you like the colors and such. Now that we've gotten all the easy stuff out of the way, let's move on to more complex things.


<a id="org7b8b471"></a>

## Configuration #4 - Programmer TODO

I'm including this as a separate section because I don't want to confuse people who came here looking for help but aren't themselves programmers. I was going to include this in the previous section but I felt that had already grown too long as it is. With that in mind, here are some features that really only other programmers will care about.


<a id="org4877dbd"></a>

### Tracking Bugs

As a programmer I do all my development in Emacs. Regardless of the language, I have it open at all times. And so there are plenty of times that I will be scanning through some source code and see something that I want to fix. If it is relatively trivial I will just leave a comment in the code with a note saying someone should come back and fix this in the future. However, frequently I'll see something that is considerably more involved. Maybe I just found an edge case that wasn't previously being handled or some tricky chunk of code that I just spent 20 min figuring out and I don't want to have to go through all of that again in 3 months when I finally get a chance to refactor it. It is in cases like this where it is extremely handy to capture the location of the bug and store it inside my TODO item. Here is what I mean.

1.  Capture Template

    A code specific TODO
    
        (setq org-capture-templates
              '(    
                ("c" "Code To-Do"
                 entry (file+headline "~/org/todos.org" "Code Related Tasks")
                 "* TODO [#B] %?\n:Created: %T\n%i\n%a\nProposed Solution: "
                 :empty-lines 0)
                ))
    
    By adding this in you can navigate to the exact line of code you want to reference and then create this 


<a id="org9989588"></a>

## Configuration #5 - Meetings

There are two distinct parts to capturing meeting data. There is the "scheduling/tracking/people" side of it and there is the "note taking/action item/what next" side of it.

For the first part, the planning and all that, I just use Microsoft's Outlook. Now I hate Outlook, but everyone uses it. They schedule meetings through it, I get email reminders through it, I get system notifications of upcoming meetings through it, and then when we do the meeting, it gives me the Teams link to join. That functionality already exists, everyone in my company uses it, and so for our purposes here, there is no need to try and replicate that. Just let Microsoft win this round and move on.

However the second part, that is something that Org excels at. Now this one is going to be a lot more complex than the previous two configurations, so pay close attention to the various moving parts.


<a id="org4458dda"></a>

## 

