# Bolt.js Test Implementation

This repository is a test implementation of the Bolt.js framework, made with [Onets project](https://github.com/CovidBackToWork/onets). The Slack app is taken from [Slack starter repository](https://github.com/slack-samples/bolt-js-starter-template).


## Walkthrough

This walkthrough explains step-by-step how to implement onets to test the Bolt.js framework.
Each step of the walkthrough corresponds to a commit in the repository.

### Step 1: Enable testing connectivity

Commit link [here](https://github.com/AlexisTonneau/boltjs-test-implementation/commit/ab6dbc11a0fa2e48c0a78d48bd1472eba72bbcb5)

In code:

- Add `.env.development` and `.env.test` file copied from the `.env.sample` file
- Add SLACK_API_URL to `.env.test` file : `http://localhost:3000/kals/`
- Load environment variables according to the current env in `app.js`
- Add slackApiUrl option to `app.js` : `slackApiUrl: process.env.SLACK_API_URL`

Running the app:

- Start mock server: `onets start`
- Start app in test mode: `NODE_ENV=test npm run start`


### Step 2: Writing a first test 

We will write the first test corresponding to the listener at `listeners/messages/`

Commit link [here](https://github.com/AlexisTonneau/boltjs-test-implementation/commit/7b55f0f4600924e640d6543251fb26e5c4c8858e)

In code:

- Add a new file: `tests/messages/sample-message.onets`
- I wrote three test cases:
  - _When we say "hello" on a channel, it should answer with "hello how are you"_
  - _When we say "hi" on a channel, it should answer with "hi how are you"_
  - _When we say "bye" on a channel, it should not answer_

Running the tests:
- Reproduce actions from step 1
- Run tests: `onets test -f tests/messages/sample-message.onets`

