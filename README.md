# discordbot
import discord
from discord.ext import commands
import random

TOKEN = "MTA1MTM3Njk0MTQyNjU0ODg0OA.G3r8aJ.gTdwAlvsN21SdVv1To-BjpY81yP8QtZqwXwivc"

intents = discord.Intents.all()
client = commands.Bot(command_prefix='/', intents = intents)


@client.event
async def on_ready():
    print(f'{client.user} online!')

@client.command(name='주사위')
async def roll(ctx, number):
    await ctx.send(f'주사위를 굴려 {random.randint(1,int(number))}이(가) 나왔습니다. (1-{number})')

@roll.error
async def roll_error(ctx, error):
    await ctx.send("명령어 잘못썼어!")

client.run(TOKEN)
