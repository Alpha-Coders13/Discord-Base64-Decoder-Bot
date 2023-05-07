# Discord Base64 Decoder Bot
Simple repo for any newbies who want to decode base64 link/words in thier discord bot. 



# Instructions
To start, open up something like Python, CMD or VScode and install the pybase64 module.
Use ```pip install pybase64``` to install it.

After that, open up your discord bot's python file. 
Under the
```
@client.event
async def on_message(message):
    if message.author == client.user:
        return
 ```
        
 section, create a new line and paste the following text in it.
  ```
  if message.content.startswith("!base64link"):
        base64link = message.content
        split = base64link.split(' ', 1)[1]
        base64_string = split
        base64_bytes = base64_string.encode('ascii')
        data_bytes = base64.b64decode(base64_bytes)
        data = data_bytes.decode('ascii')
        await message.author.send("I decoded this link to: `" + data + "` :)" )
        channel = discord.Embed(title= "Sent a DM! :white_check_mark:")
        await message.channel.send(embed=channel)
```

A very simple break-down is that when a user says `!base64link <linkhere>` the bot will decode link and then send the text over to the user who sent the command. 
Afterwards it will post an embed in the server channel saying `Sent a DM!`.


Pretty simple overall!
