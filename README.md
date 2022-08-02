# TokenDetectApi
メッセージからDiscordのTokenを検知します。
# Example
```py
import nextcord
from tokenapi import TokenDetectApi

client = nextcord.Client(intents=nextcord.Intents(messages=True, message_content=True))
detect = TokenDetectApi(client, link=True)

@client.event
async def on_message(message):
  result = detect.check_token(message.content)
  if result == True:
    await message.delete()

client.run("")
```
## nextcordやdiscord.pyを使わない?
検知力が著しく下がるため、非推奨です。
```py
import nextcord
from tokenapi import TokenDetectApi

client = nextcord.Client(intents=nextcord.Intents(messages=True, message_content=True))
detect = TokenDetectApi(None, link=False)

@client.event
async def on_message(message):
  result = detect.check_token(message.content)
  if result == True:
    await message.delete()

client.run("")
```
