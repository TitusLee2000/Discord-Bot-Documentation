# Troubleshooting
  
| **Symptoms** | **Probable Cause** | **Action** |
| ------------ | ------------------ | ---------- |
| Error Type: discord.errors.LoginFailure | Invalid Token input | Double check if token is correctly matched to save else reset and save the new token | 
| Python code doesn't compile | discord.py is an unknown module  | Make sure discord.py is installed by trying to install again `pip install discord.py` |   
| Discord bot doesn't respond to message input  | Discord token intent is not set to the right configuration |  Generate a new token with the right token configuration  |   
|              | Did not set the right command prefix | Make sure you have `bot = commands.Bot(command_prefix='!', intents=discord.Intents.all())` in your python `.py` file |   
|   |   |   |   
|   |   |   |   