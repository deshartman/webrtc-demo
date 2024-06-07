# Web RTC Web UI Demo
A simple react based Web UI that uses Twilio Voice SDK to place calls over the net

## Requirements
- A Twilio account
- Someone to call :)

## Blog
Check out this [blog](https://www.twilio.com/blog/enable-voip-calls-on-twilio-flex) for a step by step guide on settings this up from scratch 


![demo](/docs/demo.png)



# Twilio Console Config

## API Keys
1. In Console, open Account > API Keys
2. Create a new API key
3. Put the values in the `serverless/.env` file


## Routing Calls without Studio
1. In Twilio Console > Phone Numbers > Manage > Twiml Apps. Create a new application
2. Paste the URL for the Function you want to execute when this client is called. To ensure it works, test using "Call using Twilio Client". 
3. Press create
4. Open the newly created App and copy the TwiML App SID, e.g. `APe2e49959e28d111f9b7e2b064111abd8`, this will be used when minting tokens
5. Save the TwiML App SID. This will be used in the URL to select the App. The url parameter is "twimlAppSID", so use the URL `https://your-twilio-domain.twil.io/voice?twimlAppSID=APe2e49959e28d111f9b7e2b064111abd8` for example.
6. Test again using the URL in a browser



## Studio and Routing Calls
1. Create a Studio flow, add logic as required, if the call is sent to Flex, pass through a "from" value in the task payload for a Twilio number to be used in the case of an outbound call
2. Add logic to send calls to Flex or Forward or to a bot etc
3. From the "Trigger" block copy the WebHook URL
4. In Twilio Console > Phone Numbers > Manage > Twiml Apps. Create a new application
5. Paste the URL from Studio into the Voice Configuration Request URL. Press create
6. Open the newly created App and copy the TwiML App SID, e.g. `APe2e49959e28d111f9b7e2b064111abd8`, this will be used when minting tokens
7. Save the TwiML App SID. This will be used in the URL to select the App. The url parameter is "twimlAppSID", so use the URL `https://your-twilio-domain.twil.io/voice?twimlAppSID=APe2e49959e28d111f9b7e2b064111abd8` for example.
8. Test again using the URL in a browser


# App Build

## Configuration
In the `serverless` folder create an `.env` file using the `.env.example`, populate the required values (from above)

## Install Dependencies
In the `client-ui` folder, run `yarn`, `npm install` or `pnpm install`
In the `serverless` folder, run `yarn`, `npm install` or `pnpm install`

## Build the Serverless App
In the `serverless` folder, run `yarn build`, `npm run build` or `pnpm run build`

## Build the Next App
In the `client-ui` folder, run `yarn build`, `npm run build` or `pnpm run build`.  This will create the next app and move the output to the `../serverless/dist/assets` folder

## Deploy serverless
Deploy the application to Twilio serverless 
```sh
serverless $ twilio serverless deploy
```
