# Bolt.js Test Implementation

This repository is a test implementation of the Bolt.js framework, made with [Onets project](https://github.com/CovidBackToWork/onets). The Slack app is taken from [Slack starter repository](https://github.com/slack-samples/bolt-js-starter-template).


## Walkthrough

Each step of the walkthrough corresponds to a commit in the repository.

### Step 1: Enable testing connectivity

Commit link [here](https://github.com/AlexisTonneau/boltjs-test-implementation/commit/ab6dbc11a0fa2e48c0a78d48bd1472eba72bbcb5)

Configuration:

- Add `.env.development` and `.env.test` file copied from the `.env.sample` file
- Add SLACK_API_URL to `.env.test` file : `http://localhost:3000/kals/`
- Load environment variables according to the current env in `app.js`
- Add slackApiUrl option to `app.js` : `slackApiUrl: process.env.SLACK_API_URL`

Running the app:

- Start mock server: `onets start`
- Start app in test mode: `NODE_ENV=test npm run start`

