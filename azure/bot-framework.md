# bot framework

https://docs.microsoft.com/en-us/bot-framework/overview-how-bot-framework-works

https://chatbotsmagazine.com/how-to-develop-a-chatbot-from-scratch-62bed1adab8c

## how it work

### azure bot service
  * provide an integrated environment purpose-built for bot: write, connect, test, deploy, and manage from web browser with no separate editor or source control required.
  * simple bot: not need to write code at all.
  * hosting plans: app service or pay-per-run azure functions pricing
  * 5 bot templates:
  https://docs.microsoft.com/en-us/bot-framework/azure-bot-service-templates
    * basic: uses dialog to respond to user input
    * form: collects input from a user via guided conversation > formflow(c#) or waterfalls (node.js)
    * language understanding: uses  natural language models (LUIS) to understand user intent
    * proactive: uses Azure Functions to alert users of events
    * question and answer: uses knowledge base to answer the user's question

### bot builder
  * C#:

  https://docs.microsoft.com/en-us/bot-framework/dotnet/bot-builder-dotnet-overview

  * Node.js :

  https://docs.microsoft.com/en-us/bot-framework/nodejs/bot-builder-nodejs-overview

### core concepts

* channel: skype, and web chat channels are automatically pre-configured

* bot connector: connects a bot to one or more channels and handles the message exchange between them.

* activity: to exchange information between bot and channel. any communication going back and fort is an activity of some type.

* message: is the most common type of activity. it can be text, contain attachments, interactive elements, and rich cards.

* dialog: helps organize the login in your bot and manages conversation flow.
are arranged in a stack. ex: BrowseProducts, PlaceOrder

* rich cards: comprises a title, description, link, and images.
