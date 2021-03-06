# Discord bot
[![Discord.py](https://img.shields.io/badge/Uses-Discord.py-violet?style=for-the-badge&logo=Discord&colorB=7289da)](https://discordpy.readthedocs.io/en/latest/index.html)
[![License](https://img.shields.io/badge/License-MIT-green?style=for-the-badge)](https://lbesson.mit-license.org/)

### Installation

Create a virtual environment using [venv](https://virtualenv.pypa.io/en/latest/#:~:text=virtualenv%20is%20a%20tool%20to,library%20under%20the%20venv%20module.)

```bash
python -m venv <your-env>
source <your-env>/bin/activate
```

Use the package manager [pip](https://pip.pypa.io/en/stable/) to install discord.py and other packages using the requirements file.

```bash
pip install -r requirements.txt
```

## 1. Screenshot bot (with Azure Vision)
Takes screenshot when pressed a custom keyboard shortcut, performs OCR via Azure's Vision API and sends it to a discord channel via bot.

### Usage

- Add your Discord API token, Channel ID and Azure Vision API Key and Endpoint to `.env` file. Refer this [example .env file](./.env.example)

- (optional) Modify `take_screenshot()` function to control what kind of screenshot you want.

- (optional) Set a custom keybind in `keyboard.is_pressed(<keybind_here>)`

- (optional) Change duration in `@tasks.loop(seconds=<duration_in_Seconds>)` for recording keypresses.

- Run the python file with root access (required by keyboard module) <br>`sudo <path-to-your-env>/bin/python3 microsoft_screenshot.py`

### Note

If you dont want to use Azure Vision, there is another file [screenshot.py](./screenshot.py) which uses Tesseract OCR. Installation instructions for Tesseract [here](https://www.bl.uk/britishlibrary/~/media/bl/global/early%20indian%20printed%20books/training%20resources/installing%20and%20using%20tesseract%20ocr.pdf)

## 2. Song player bot (Youtube URL)
Plays the given URL in the voice channel of the connected user who commanded it.

### Usage

- Add your Discord API token to the `.env` file. (ignore if done already)

- (optional) Set a commmand and command prefix.

- Run the python file with venv activated `python youtube.py`

## 3. Annoy bot (?)

Basically this bot plays a random audio file from a list of audio files whenever a specific user (or users) join a voice channel. Also can be triggered manually using a command. Use this to annoy someone.

### Usage

- Add your Discord API token to the `.env` file. (ignore if done already)

- Move the audio files you want to play locally, and add them to `PATH_LIST`

- Add ID of user or users in `member.id == <ID_HERE>` ([How to get User ID](https://support.discord.com/hc/en-us/articles/206346498-Where-can-I-find-my-User-Server-Message-ID-))

- (optional) Set a commmand and command prefix.

- Run the python file with venv activated `python audio.py`

### Note

FFMPEG is required for this bot to run. Download and install [FFMPEG](https://ffmpeg.org/download.html),  and point the installation bin folder in `discord.FFmpegPCMAudio(executable = <PATH_HERE>,` to where you installed it.

## 4. Gif bot (with status)

Sends gif using links stored in MongoDB and has custom status refreshing for given duration. Can also add any GIF link to db from discord chat. 

### Usage

- Add your Discord API token and MongoDB Token to the `.env` file.

- Add the MongoDB endpoint and update the db name and collection name respectively.

- Add some status tags in `status_list`

- (optional) Change duration in `@tasks.loop(seconds=<duration_in_Seconds>)` for refreshing status.

- (optional) Set a commmand and command prefix.

- (optional) Change how gifs are searched and indexed according to your DB.

- Run the python file with venv activated `python gifbot.py`

### Note

[Mongodb](https://www.mongodb.com/) is required for this program. See the link for more info and how to start your own DB cluster.

## License

This software is licensed under the terms of the [MIT License](./LICENSE).