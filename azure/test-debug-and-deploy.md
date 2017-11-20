# test and debug a bot

## debug with the emulator

https://docs.microsoft.com/en-us/bot-framework/debug-bots-emulator

1. download and install emulator

2. install and configure ngrok

https://dashboard.ngrok.com/get-started

```
0. install
https://ngrok.com/

1. connect your account:
ngrok authtoken 7Uxxxxxxxxxxxxxxxxxxxxxxxxxxxghn9
2. start your first tunnel:
ngrok http 80
3. ngrok inspector
http://localhost:4040/inspect/http
4. ngrok -v // to check version
```

## connect to a bot that is running on localhost

```
Open app setting then input path to ngrok.exe
check bypass local
```

## connect to a bot that is running on remotely
```
launch the bot framework emulator and enter your bot's endpoint into the emulator's address bar
```

## enable speech recognition

```
https://docs.microsoft.com/en-us/azure/cognitive-services/Speech/home
```

## emulate payment processing

you can use bot framework emulator to emulate payment processing. The process payment logic
simply returns a successful payment record.

# deploy a bot

## deploy a bot from local git
https://docs.microsoft.com/en-us/bot-framework/deploy-bot-local-git

```
1. download and install Azure
https://docs.microsoft.com/en-us/cli/azure/install-azure-cli?view=azure-cli-latest

2. install windows sub system for linux
https://msdn.microsoft.com/commandline/wsl/install-win10

```
