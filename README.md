
# Gmail Push notifications to Discord

![gmail_discord_integrations](https://user-images.githubusercontent.com/10729787/203806753-e9c9392e-e72a-4c96-b461-dc67f4bb9b93.png)


Get real-time Gmail push notifications to your Discord channel!


## Acknowledgements

 - [Gmailpush library for handling Gmail API push notification](https://github.com/byeokim/gmailpush)
 - [discord.js for Node.js to interact with the Discord API](https://discord.js.org/)

 
## Features

- No need to periodically poll the Gmail API's history feed for updates
- Just subscribe and whenever a change occurs, the app will instantly notify you
- Once a new email is pushed, it will route as a text message to your Discord webhook URL
- Choose which part of the email (subject, body, from, to) you want to include them in the message to Discord


## Prerequisites
- [Create a new project on the Google Cloud console](https://cloud.google.com/resource-manager/docs/creating-managing-projects#creating_a_project)
- Generate the `credentials.json` file by creating an OAuth2 client ID and client secret for your new project
- [Enable the Gmail API](https://console.cloud.google.com/apis/library/gmail.googleapis.com) for your new project
- [Enable the Pub/Sub API](https://console.cloud.google.com/cloudpubsub/) and the Gmail API for your new project
- [Create a Pub/Sub Topic](https://cloud.google.com/pubsub/docs/quickstart-console#create_a_topic) and a Subscription for that Topic
- Get a VPS on the cloud with a public domain (HTTPS) for setting up the endpoint URL for google to send us updates. Deploy the Node.js server however you like. For testing purposes, I recommend using [ngrok](https://ngrok.com/download)
- Create a [Discord Webhook](https://discordjs.guide/popular-topics/webhooks.html#creating-webhooks-through-server-settings)
## Installation

1. Clone this repo and then install it with npm:

```
  git clone https://github.com/jzvi12/gmail-push-to-discord.git
  cd gmail-push-to-discord/
  npm i
```
2. Rename the `.env_exmaple` file to `.env` and then add your credentials:

```
EMAIL=test@gmail.com
CLIENT_ID=xxxxxxxxxxxxxx.apps.googleusercontent.com
CLIENT_SECRET=xxxxxxxxxxxxxx
TOPIC_URL=projects/<your-project-id>/topics/MyPush
SUBSCRIPTION_URL=projects/<your-project-id>/subscriptions/MyPush-sub
EMAIL_LABEL=UNREAD
WEBHOOK_URL=https://discord.com/api/webhooks/get/yours
```

3. From the [prerequisites](#prerequisites),  download and place your `credentials.json` file in the app root directory.

4. Generate a Gmail access token by running the following command:

```bash
node getNewToken.js
```
Copy the verification URL from the terminal and paste it a browser where the same Gmail account is already logged in.
Just allow access to your new app and copy and code and paste it in the terminal.
If everything went fine, you'll see your `token.json` file.




## License

[MIT](https://choosealicense.com/licenses/mit/)

