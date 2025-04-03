# Setting Up Discord Bot Reminder Program

### _In this section we will learn:_

- [ ] How to make reminder program with your Discord bot

!!! info "Coding Portion"

    This is the very last stage which gives Grokamoly a heart and a purpose! It is also the stage where the most coding is required, but don't be too overwhelmed. We recommend you to run through the steps once to get everything working and come back to examine what each function does. Best if you played around with it too. With that spirit at heart, the following documention lists out the purpose of each snipet as well as what you can and 'cannot' change.

1. Using the same directory as `python.py`, make a new file called `reminder.py`

2. Initialize imports for the `Python` file. <**Do Not Change**>

   ```py
   import discord
   from discord.ext import commands
   import asyncio
   from datetime import datetime
   import re
   ```

3\. Insert the code your Discord Bot to recogonize the command

```py
intents = discord.Intents.all()
bot = commands.Bot(command_prefix='!', intents=intents)
```

<br>
___

## Create helper function to parse Time from commands

1.  Define your function `parse_time` and it takes in the paramter `time_str`

    ```py
    def parse_time(time_str):
        """Parse time input like '5m', '2h', '1d' or 'YYYY-MM-DD HH:MM'"""
    ```

2.  Insert a format checker to ensure time can be read correctly then find the differece fromo current time and desire time to be set

    ```py
    def parse_time(time_str):
        """Parse time input like '5m', '2h', '1d' or 'YYYY-MM-DD HH:MM'"""
        for date_format in ('%Y-%m-%d %H:%M', '%Y-%m-%d %H:%M:%S'):
            try:
                current_time = datetime.strptime(time_str.strip(), date_formate)
                seconds = (current_time - datetime.now()).total_seconds()
                return seconds
            except ValueError:
                pass
    ```

3.  Insert a regex checker if user wants timer from secs, mins, hours, or days

    ```py
    def parse_time(time_str):
        """Parse time input like '5m', '2h', '1d' or 'YYYY-MM-DD HH:MM'"""
        for date_format in ('%Y-%m-%d %H:%M', '%Y-%m-%d %H:%M:%S'):
            try:
                current_time = datetime.strptime(time_str.strip(), date_formate)
                seconds = (current_time - datetime.now()).total_seconds()
                return seconds
            except ValueError:
                pass
        time_units = {'s': 1, 'm': 60, 'h': 3600, 'd': 86400}
        match = re.match(r'(\d+)([smhd])', time_str.lower())
    ```

4.  Add a if statement to determine if it is match return the time in seconds else print a error message

    ```py
    def parse_time(time_str):
        """Parse time input like '5m', '2h', '1d' or 'YYYY-MM-DD HH:MM'"""
        for date_format in ('%Y-%m-%d %H:%M', '%Y-%m-%d %H:%M:%S'):
            try:
                current_time = datetime.strptime(time_str.strip(), date_formate)
                seconds = (current_time - datetime.now()).total_seconds()
                return seconds
            except ValueError:
                pass
        time_units = {'s': 1, 'm': 60, 'h': 3600, 'd': 86400}
        match = re.match(r'(\d+)([smhd])', time_str.lower())
        if match:
            amount, unit = match.groups()
            return int(amount) * time_units[unit]
    ```

5.  Add program interface for Discord Bot called `remind`

    1.  Define your function for `remind` with the parameter `ctx, time_str: str, *, message:str`

        ```py
        @bot.command()
        async def remind(ctx, time_str: str, *, message: str):
        """Set a reminder. Usage: !remind <time> <message> (e.g., !remind 5m Break or !remind "2025-04-03 14:30" Meeting)"""
        ```

    2.  Add a code the replace `','` with `' '` so the `parse_time` function and operate on it

        ```py
        @bot.command()
        async def remind(ctx, time_str: str, *, message: str):
        """Set a reminder. Usage: !remind <time> <message> (e.g., !remind 5m Break or !remind "2025-04-03 14:30" Meeting)"""
        time_str = time_str.replace(',', ' ').strip()
        ```

    3.  Add checkers to see if is greater than 0 seconds and if reminder is a timer or a set time

        ```py
        @bot.command()
        async def remind(ctx, time_str: str, *, message: str):
        """Set a reminder. Usage: !remind <time> <message> (e.g., !remind 5m Break or !remind "2025-04-03 14:30" Meeting)"""
        time_str = time_str.replace(',', ' ').strip()
        try:
            seconds = parse_time(time_str)
            if seconds <= 0:
                await ctx.send("Please set a reminder for a future time!")
                return

            # Adjust confirmation message based on input type
            if ' ' in time_str:  # Absolute time
                await ctx.send(f"Reminder set for '{message}' at {time_str}.")
            else:  # Relative time
                await ctx.send(f"Reminder set for '{message}' in {time_str}.")

            await asyncio.sleep(seconds)
            await ctx.send(f"{ctx.author.mention}, here's your reminder: {message}")
        ```

    4.  Add a error return message section to allow error display for user

        ```py
        @bot.command()
        async def remind(ctx, time_str: str, *, message: str):
        """Set a reminder. Usage: !remind <time> <message> (e.g., !remind 5m Break or !remind "2025-04-03 14:30" Meeting)"""
        time_str = time_str.replace(',', ' ').strip()
        try:
            seconds = parse_time(time_str)
            if seconds <= 0:
                await ctx.send("Please set a reminder for a future time!")
                return

            # Adjust confirmation message based on input type
            if ' ' in time_str:  # Absolute time
                await ctx.send(f"Reminder set for '{message}' at {time_str}.")
            else:  # Relative time
                await ctx.send(f"Reminder set for '{message}' in {time_str}.")

            await asyncio.sleep(seconds)
            await ctx.send(f"{ctx.author.mention}, here's your reminder: {message}")
        except ValueError as e:
            await ctx.send(f"Error: {str(e)}")
        ```

6.  Insert Your Discord Bot's Token

    ```py
    bot.run('Insert Token Here')
    ```

<br>
___

## Test within Discord server

![gif](./assets/taskthree/Discord_reminder_program.gif 'Reminder Program')

<br>

---

## Conclusion

By the end of this section, you will successfully learned the following:

- [x] How to create a Discord Bot Remainder Program
