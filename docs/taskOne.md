# Setting Up a Discord Bot
In this section we will show how to create a discord bot and install need packages for your prefer IDE

## Creating a Discord Bot
!!! warning "Prerequisite" 

    You will need to have discord account  if do not have one you make an account [`here`](https://discord.com/register)
  
1. Go to [`Discord Developer Page`](https://discord.com/developers/applications)

<br>

2. Make a Application Top-Right of The Page:
    
    [insert Image]

3. Customise Your Discord Bot

    - After creation you will be in the bot interface you can focus on the left side of the screen select the `Bot` tab 

    [Insert image]

    !!! info "Customization"

        You can choose images that are appropriate if use is for public use.
    

4. Select The Intent of Your Bot

    For this Demo you will select from the following image:

    [insert image]

    1. Presence Intent
    2. Server Members Intent 
    3. Message Content Intent

5. Create Discord bot's token
    
    - You have click on the blue button `Reset Token`

    [insert image]


    !!! warning Protect Your Token

        Make sure to keep note of your token as it give access to your Bot's key to to connect to Discord's server


!!! success 
    
    At this point, you have successfully create A discord bot


## Setting Up Python for VSCode

Next we will start up the new porject in VSCode

!!! info "VSCode"
    refers to Visual Studio Code

1. Make a new folder within a desired location

2. Open folder within VSCode

    [insert image]

3. Install python extension 

    1. Select the extension tab on the right

    [insert image]

    2. search for python

    3. install python from Microsoft store

4. Time to start python Virtual Environment

    1. use `ctrl + shift + p` at the same time
        
        ```
        ctrl + shift + p
        ```

    2. Type the following:

        ```
        Python:Select Interpreter
        ```
    3. Select the option `Create Virtual Environment`

        [insert image]

    4. Select `Venv` option
    
    5. select your latest version python in the options

    !!! success install complete
        now you will a new folder show up in your directory
        [insert image]

5. Install important packages

    1. make a new terminal by the following:
        ```
        ctrl + shift + `
        ```
    2. use the following command to install Discord package

        ```
        pip install discord.py
        ```

!!! success Completed Setup
    Now you are ready for the next step