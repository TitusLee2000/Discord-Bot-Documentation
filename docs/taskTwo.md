# Setting Up Discord Bot With a Server
    [insert overview]

## Inviting Discord Bot To a Server

1. asd

    ![Image](./assets/tasktwo/tasktwo_p1.png "Authio")

2. asd

3. asd

    ![Image](./assets/tasktwo/tasktwo_p2.png "Discord Bot Authio URL generator")

4. asd

    ![Image](./assets/tasktwo/tasktwo_p3.png "Discord Bot Permission")

5. asd

    ![Image](./assets/tasktwo/tasktwo_p4.png "Bots Join Link")

6. asd

7. asd

    ![Image](./assets/tasktwo/tasktwo_p5.png "Join server")

8. asd

    ![Image](./assets/tasktwo/tasktwo_p6.png "Server Member List")

!!! success "Joined the server"
    Your Discord bot should now be visable in your selected server


## Testing if Bot Works in Server

1. asd

2. asd

    ```
    import discord
    from discord.ext import commands
    ```

3. asd

    ``` 
    bot = commands.Bot(command_prefix='!', intents=discord.Intents.all())
    ```

4. asd

    ```
    @bot.event
    async def on_ready():
        print(f'Logged in as {bot.user.name} ({bot.user.id})')
        print('------')
    ```

5. asdad

    ```
    @bot.command()
    async def ping(ctx):
    await ctx.send('Pong!')
    ```

6. asda

    ```
    @bot.command()
    async def hello(ctx):
    await ctx.send(f'Hello, {ctx.author.mention}!')
    ```

7. asd

    ```
    bot.run('YOUR_TOKEN_HERE')
    ```

    !!! warning "If token is invalid"
        The program crash on compile

8. asd

    ![gif](./assets/tasktwo/Discord_bot_test.gif "Test Results")

!!! success "Discord Bot's responds"
    Now your Discord bot will respond to certain commands

## Conclusion

By the end of this section, you will successfully learned the following:

- [x] How to invite a Discord Bot to your server

- [x] How to test basic programs with you Discord Bot

