import discord

import asyncio


client = discord.Client()

@client.event
async def on_ready():
    print('Pybot ist nun Online {}'.format(client.user.name))
    client.loop.create_task(status_task())



async def status_task():
    while True:
        await client.change_presence(activity=discord.Game('https://discord.gg/DyPJVWcyaQ'), status=discord.Status.online)   
        await asyncio.sleep(4)
        await client.change_presence(activity=discord.Game('https://discord.gg/dfjFgWtDe7'), status=discord.Status.online)
        await asyncio.sleep(4)

@client.event
async def on_message(message):
    if message.author.bot:
        return
    if '!help' in message.content:
        await message.channel.send('**Alle commands**\r\n'
                                   '!invite -> Pyx Community Discord\r\n')


@client.event
async def on_message(message):
    if message.author.bot:
        return
    if '!invite' in message.content:
        await message.channel.send('**Pyx Community Discord**\r\n'
                                   'https://discord.gg/dfjFgWtDe7')

@client.event
async def on_message(message):
    if message.author.bot:
        return
    if '!code' in message.content:
        await message.channel.send('**Bot Code Download**\r\n'
                                    )








client.run('Dein Token')
