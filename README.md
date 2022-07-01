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


### Step 3: Covering all listeners

For the moment, modals aren't supported yet on Onets.

Then, I wasn't able to write a test for the listeners:
- `listeners/action/`: Actions are supported on Onets, but the behavior of this action is to interact with a modal.
- `listeners/shortcuts/`: Shortcuts are supported on Onets, but the behavior of this shortcut is to interact with a modal.
- `listeners/views/`: Because Onets doesn't support modals, it doesn't support `view_submission` as well.

I could have been further and modify those behaviors, but I decided to not cheat and to write tests on the unmodified listeners.


#### Events listener

Commit link [here](https://github.com/AlexisTonneau/boltjs-test-implementation/commit/a4bb7c24ed5618ddc33b9fb8701e46055bcf9e6b)

- I created a new file: `tests/events/app-home-opened.onets`
- I wrote a test case: _When we open the app, it should display the home view_
- I had to write a JSON file that will be compared for our assertion: `tests/events/app-home.json`
- I was able to load it in my test file with Load keyword
- Then I used it in my _Expect_ keyword


#### Commands listener

Commit link [here](https://github.com/AlexisTonneau/boltjs-test-implementation/commit/029d4943dae74bdd2e864a50e133041bddb9d92c)

- I created a new file: `tests/commands/sample-command.onets`
- I wrote a test case: _When a /sample-command is executed, it should respond with an ephemeral message_

