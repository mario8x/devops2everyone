# principal for bot design
https://docs.microsoft.com/en-us/bot-framework/bot-design-principles

## factors that do not guarantee a bot's success
  * how smart the bot is: unlikely that your bot smarter will guarantee happy
  users and adoption of your platform.

  * how much natural language the bot supports:
  your bot can be grate at conversations. but unless it addresses the problems
  that your users need to solve, these capabilities may contribute very little to making your bot successful.

  * voice: forcing users to use voice can result in a frustrating user experience.

## factors that do influence a bot's success

  * does the bot easily solve the user's problem with minimum number of steps ?
  * does bot solve the user's problem better than any of  the alternative experiences?
  * does the bot run on the devices and platforms the user cares about?
  * is the bot discoverable? do the users naturally know what to do when using it?

# first interaction

## first impression matters
https://docs.microsoft.com/en-us/bot-framework/bot-design-first-interaction
just say `hi` is not enough

* design 1:
```
Hello user, how can i help you?
```

* design 2:

```
Hello! how can i help you?
Orders
Products
Help
```

* others:
a well-designed bot provides the user with access to information about its privacy policy and terms of use.


# conversations flow:

https://docs.microsoft.com/en-us/bot-framework/bot-design-conversation-flow


* traditional :
main screen  > new order screen > product search screen

* bot:
root dialog > new order dialog > product search dialog

## dialogs, stacks and humans

humans do not communicate in "stacks". They tend to frequently change their minds.
while your bot may have logically constructed a stack of dialogs, the user may decide to do
something entirely different or ask a question that may be unrelated to the current topic.

* Insist that the user answer the question first.
* disregard everything that the user had done previously, reset the whole dialog stack, and
start from the beginning by attempting to answer the user's question
* attempt to answer the user's question and then return to that yes/no question and try to resume
from there.

# Navigation

users often interact with bots in a non-linear fashion, making it challenging to design bot navigation that consitently
delivers a great user experience. Consider the following dilemmas:

* how do you ensure that a user doesn't get lost in a conversation with a bot?
* can a user navigate "back" in a conversation with a bot?
* how does a user navigate to the "main menu" during a conversation with a bot?
* how does a user "cancel" an operation during a conversation with a bot?

## the stubborn bot

insist upon maintaining the current course of conversation, even when the user attempts to steer things in a different direction.
```
* do: design your bot to consider that a user might attemp to change the course at any time.
* don't: design your bot to ignore user input and keep repeating the same question in an endless loop.
```

## clueless bot

responds in a nonsensical manner when it doesn't understand a user's attempt to access certain functionality.
```
* do: implement `global message handlers` that will examine user input for the keyword that you specify(ex: 'help', 'cancel', 'start over')
* don't: design every dialog to examine user input for a list of keywords
```

## mysterious bot

fails to immediately acknowledge the user's input in any way.
```
* do: design your bot to immediately acknowledge user input, evn in cases where the bot may take some time to compile its response
* don't: design your bot to postpone acknowledgement of user input until the bot finishes compiling its response.
```

## captain obvious bot

provides unsolicited information that is completely obvious and therefore useless to the user
```
* do: design your bot to provide information that will be useful to the user
* don't: design your bot to provide unsolicited information that is unlikely to be useful to the user.
```

## bot that can't forget

can't forget inappropriately integrates information from past conversations into the current conversation.

```
do: design your bot to maintain the current topic of conversation, unless/until the user expresses a desire to revisit a prior topic
don't: design your bot to interject information from past conversations when it is not relevant to the current conversation
```

# UX elements

https://docs.microsoft.com/en-us/bot-framework/bot-design-user-experience

## rich user controls

## text and natural language

## speech

# Patterns

## task automation

https://docs.microsoft.com/en-us/bot-framework/bot-design-pattern-task-automation

enables the user to complete a specific task or set of tasks without any assistance from a human.
it may have natural language understanding capabilities to enrich conversations with users.

## knowledge base

https://docs.microsoft.com/en-us/bot-framework/bot-design-pattern-knowledge-base
can be designed to provide information about virtually any topic.
Regardless of the use case for which a knowledge bot is designed, its basic objective is always the same: find and
return the information that the user has requested by leveraging a body of data.

* Search
* QnA maker (FAQs)
* LUIS
* Combining Search, QnA Maker, and/or LUIS

## bot to web
https://docs.microsoft.com/en-us/bot-framework/bot-design-pattern-integrate-browser

Integrate your bot with a web browser, may need to send the user to a web browser to complete a task then resume
the conversation with the user after the task has been completed.

* bot to web browser, and back again

## handoff to human

https://docs.microsoft.com/en-us/bot-framework/bot-design-pattern-handoff-human

Regardless of how much artificial intelligence a bot possesses, there may still be times when it
needs to hand off the conversation to a human being.
It should recognize when it needs to hand off and provide the user with a clear, smooth transition.

## bots in app
https://docs.microsoft.com/en-us/bot-framework/bot-design-pattern-embed-app

although bots most commonly exist outside of apps, they can also be integrated with apps.

### Integrating bot with app
https://docs.microsoft.com/en-us/bot-framework/bot-design-pattern-embed-app

* native mobile app
* IoT app: can communicate with bot framework by using the Direct Line API.
* other types of apps and games

## embed a bot in a website

https://docs.microsoft.com/en-us/bot-framework/bot-design-pattern-embed-web-site

although bots commonly exist outside of websites, they can also be embedded within a website.
