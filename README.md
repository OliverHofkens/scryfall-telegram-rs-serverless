# scryfall_telegram_rs #

*Note: Spritual successor to [Scryfall_Telegram](https://github.com/OliverHofkens/Scryfall_Telegram)*

Scryfall-telegram-rs is both an inline and always-on [Telegram](https://telegram.org/) bot that uses
[Scryfall](https://scryfall.com/)'s API to search Magic: The Gathering cards.

All Scryfall syntax that can be understood by the API can be used in inline mode. A full reference
can be found here: [Scryfall Syntax Reference](https://scryfall.com/docs/reference).

For always-on mode, add [ScryfallBot](https://t.me/ScryfallBot) to your chat and mark cards to be looked up with `[[ card you want to find ]]`.
You can find a specific printing or limit the search to a specific set by adding the 3 letter set code like this: `[[ my card | SET ]]`

NOTE: Currently, the bot needs to be an admin in your chat in order to see messages without being explicitly mentioned...

Some inline examples:
- Search a card by name: `@ScryfallBot Bolas`
- Search an instant that can be played in an Esper EDH deck: `@ScryfallBot id<=esper t:instant`
- Search cards that enter the battlefield tapped: `@ScryfallBot o:"~ enters the battlefield tapped"`

Some always-on examples:
- Does anyone have an extra [[ nyx fleece ram ]] or [[ bolas dragon god ]] ?  
- Which is best: [[Bottle Gnomes|TMP]] or [[Bottle Gnomes]] ?

## Running it yourself

This bot lives on Telegram: [t.me/ScryfallBot](https://t.me/ScryfallBot) (Beta version: [t.me/ScryfallBetaBot](https://t.me/ScryfallBetaBot) ),
but you can easily run a copy of it yourself:

### Requirements
- Rust
- Serverless framework
- A Serverless provider (the included `serverless.yml` contains config for AWS Lambda)

### Building
- Ensure these 2 variables are in your environment:
    - TELEGRAM_BOT_TOKEN_PROD: The token given to you by the [The Botfather](https://core.telegram.org/bots#6-botfather)
    - WEBHOOK_SECRET: A secret you can choose yourself. It will be used in your webhook URL.
- Run `serverless deploy --stage production` to build and deploy.
- Run `python3 scripts/register_webhook.py production {webhook_url}` to register your webhook on Telegram
- You're live!
