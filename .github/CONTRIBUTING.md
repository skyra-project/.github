# Contributing

**The issue tracker is only for issue reporting or proposals/suggestions. If you have a question, you can find us in our
[Discord Server]**.

To contribute to this repository, feel free to create a new fork of the repository and submit a pull request. We highly
suggest [ESLint] to be installed in your text editor or IDE of your choice to ensure builds from GitHub Actions do not
fail.

1. Fork, clone, and select the **main** branch.
1. Create a new branch in your fork.
1. Make your changes.
1. Ensure your linting and tests pass by running `yarn test && yarn lint`
1. Commit your changes, and push them.
1. Submit a Pull Request!

## Running TypeScript + Gateway based Skyra Project bots locally

To run any of the TypeScript + Gateway based Skyra bots locally a few steps should be taken.

1. Install [Node.JS], [Yarn] and [Docker].
1. In the Discord Developer portal go to your application and then to the "Bot" menu.
1. At "Privileged Gateway Intents" enable `SERVER MEMBERS INTENT` and `MESSAGE CONTENT INTENT`
1. Copy and paste the [`.env.development`] file in the `src` directory and rename it to `.env.development.local`.
1. Scroll down to the tokens section.
1. At this section enter your own bot's API token at `DISCORD_TOKEN`.
1. Fill in any other API keys you have / want to fill in.
1. Install project dependencies with `yarn install`.
1. Start the bot in development mode with `yarn dev`.

A few other important commands:

```bash
# Lints and format all the code:
$ yarn lint

# Run the bot in development mode:
$ yarn start
```

## Running TypeScript + HTTP-Only based Skyra Project bots locally

To run any of the TypeScript + HTTP-Only based Skyra bots locally a few steps should be taken.

1. Install [Node.JS], [Yarn] and [Docker].
1. You will need an **HTTPS** public endpoint which Discord can send payload data to. We recommend using [Cloudflare
   Tunnels][cf-tunnels] for this. You can find instructions on how to set up a [Cloudflare Tunnel here][cf-tunnel].
   - The basic idea is that locally you start a cloudflare tunnel that forwards your `localhost:port` to the Cloudflare
     domain, for example `https://my-bot-project.mywebsite.xyz`.
1. In the Discord Developer portal go to your application and stick to the "General Information" menu.
1. At `INTERACTIONS ENDPOINT URL` enter the HTTPS endpoint you have set up.
   - Following the previous example this would be `https://my-bot-project.mywebsite.xyz`.
1. Copy and paste the [`.env.development`] file in the `src` directory and rename it to `.env.development.local`.
1. Scroll down to the authentication section.
1. At this section enter your own bot's:
   1. Application ID (at `DISCORD_APPLICATION_ID`)
   2. Application Public Key (at `DISCORD_APPLICATION_PUBLIC_KEY`)
   3. The port at which you want to start the application (at `PORT`)
      - This is the port that you will forward with [Cloudflare Tunnels][cf-tunnels]
1. Fill in any other API keys you have / want to fill in.
1. Install project dependencies with `yarn install`.
1. Start the bot in development mode with `yarn dev`.
1. Start your [Cloudflare Tunnel][cf-tunnels] to start forwarding data
1. (**_First Time Only_**) on the Discord Developer portal press the "Save Changes" button to save the
   `INTERACTIONS ENDPOINT URL`.
   - **_IMPORTANT: Your bot has to be running and your Cloudflare Tunnel has to be active for the save to proceed
     successfully as Discord will send an acknowledgement message to the bot to ensure the URL being saved is correctly
     set up_**

A few other important commands:

```bash
# Lints and format all the code:
$ yarn lint

# Run the bot in development mode:
$ yarn start
```

## Running .NET + HTTP-Only based Skyra Project bots locally

**_TODO_**

## Skyra Project Concept Guidelines

There are a number of guidelines considered when reviewing Pull Requests to be merged. _This is by no means an
exhaustive list, but here are some things to consider before/while submitting your ideas._

- Skyra Project should never change Sapphire's or Discord.js' default behavior. Skyra should only add to Sapphire and
  Discord.js, and be as consistent as possible with them.
- Everything in Skyra Project should be generally useful for the majority of users. Don't let that stop you if you've
  got a good concept though, as your idea still might be a great addition.
- Everything should be shard compliant. If code you put in a pull request would break when sharding, break other things
  from supporting sharding, or is incompatible with sharding; then you will need to think of a way to make it work with
  sharding in mind before the pull request will be accepted and merged.
- Everything should follow [OOP paradigms] and generally rely on behaviour over state where possible. This generally
  helps methods be predictable, keeps the codebase simple and understandable, reduces code duplication through
  abstraction, and leads to efficiency and therefore scalability.
- Everything should follow our ESLint rules as closely as possible, and should pass lint tests even if you must disable
  a rule for a single line.
- Everything should follow [Discord Bot Best Practices]
- Scripts that are to be ran outside of the scope of the bot should be added to a `scripts` directory at the root and
  should be in the `.mjs` file format.

<!-- Link Dump -->

[discord server]: https://join.skyra.pw
[eslint]: https://eslint.org/
[node.js]: https://nodejs.org/en/download/
[yarn]: https://classic.yarnpkg.com/en/docs/install
[docker]: https://www.docker.com
[oop paradigms]: https://en.wikipedia.org/wiki/Object-oriented_programming
[discord bot best practices]: https://github.com/meew0/discord-bot-best-practices
[`.env.development`]: /src/.env.development
[cf-tunnels]: https://www.cloudflare.com/products/tunnel/
