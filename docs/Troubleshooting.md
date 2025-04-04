# Troubleshooting
  
| **Symptoms** | **Probable Cause** | **Action** |
| ------------ | ------------------ | ---------- |
| Python code doesn't compile | discord.py is an unknown module  | Make sure discord.py is installed by trying to install again `pip install discord.py` |   
| Discord bot doesn't respond to message input  | Discord token intent is not set to the right configuration |  Generate a new token with the right token configuration  |   
|              | Did not set the right command prefix | Make sure you have `bot = commands.Bot(command_prefix='!', intents=discord.Intents.all())` in your python `.py` file |   
| Error Type: `discord.errors.Forbidden`  |  Bot lacks permissions for an action | Check the bot’s role in the server and grant necessary permissions (e.g., "Send Messages," "Manage Roles") in Discord  |   
| Error Type: `discord.errors.LoginFailure` | Invalid Token input | Double check if token is correctly matched to save else reset and save the new token | 
| Error Type: `SyntaxError` in Python  | Code typo or incorrect syntax  |  Review the line number in the error message and fix typos (e.g., missing colons, parentheses) |   
|Commands trigger multiple times|Event listener or command handler duplication|Ensure commands are only registered once and check for overlapping `on_message` listeners overriding commands|