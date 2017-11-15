# bot builder nodejs concepts

https://docs.microsoft.com/en-us/bot-framework/nodejs/bot-builder-nodejs-concepts

* connector
* messages
* dialog
* actions : handles user actions and trigger actions
* recognizers: your bot need to understand what the user is asking for and then
take a appropriate action. LUIS API, or implement a custom recognizer to determine the user's intent.(https://docs.microsoft.com/en-us/bot-framework/nodejs/bot-builder-nodejs-recognize-intent-messages)
* saving state:
  * userData - stores information globally for the user across all conversations

  * conversationData - store information globally for a single conversation.

  * privateConversationData - stores information globally for a single conversation but it is private data specific to the current user.

  * dialogData: persist information for a single dialog instance.
