# totally-real-news-bot
Generates AI text/images/video based on a NYT news headline, can be modified to create other content.

Update - 16/6/24 - Project uses a standalone version of alltalk_ttsv2 BETA, it works pretty much the same as the TWGUI extension but has its own install location, read more here:<br>
https://github.com/erew123/alltalk_tts/tree/alltalkbeta<br>

Here's some examples of output: https://www.facebook.com/profile.php?id=61560732713412&sk=videos

Requires:<br>
- Python 3<br>
- A working install of text-generation-webui with the --api flag enabled<br>(https://github.com/oobabooga/text-generation-webui)<br>
- A working Alltalk_tts v2 BETA installation with api access enabled.<br>(Either the standalone or TWGUI extension will work)<br>(https://github.com/erew123/alltalk_tts/tree/alltalkbeta)<br>
- A working install of stable-diffusion-webui with  --api enabled in COMMANDLINE_ARGS<br>(https://github.com/AUTOMATIC1111/stable-diffusion-webui)<br>
- A New York Times API access key<br>(https://developer.nytimes.com/get-started)<br>
- (optional) A Facebook page access token<br><br>

Usage:<br>
1. Clone this repository<br>
2. Run `pip install -r requirements.txt`<br>
3. In run_bot.py, under "API Details", double check that your text-generation-webui, stable-diffusion-webui and alltalk_tts API paths are correct as well as your NYT API key is set<br>
4. In run_bot.py, confirm bot settings under "Config", use True and False to set options.
5. Make sure both text-generation-webui (with alltalk_tts) and stable-diffusion-webui are running with api enabled<br>
6. Run `python run_bot.py` in console<br><br>

Basic process overview:<br>
1. Bot grabs a NYT headline and short description<br>
2. Bot uses text-generation-webui to analyse the headline for tone and stores it.<br>
3. Bot trys to make up hashtags related to the headline and article summary<br>
4. Bot generates a news article text based on the headline and short description, asks bot to write in a randomly selected tone from emotions.txt and from a random perpective from descriptive.txt<br>
5. Bot uses Alltalk_tts to generate speech based on the generated article text, outputs a .wav file
6. Bot starts generating 4 images based on the headline and the tone stored from step 2, it will start generating using what ever model is loaded into stable-diffusion-webui, outputs .png files<br>
- If enabled, bot will overlay a watermark to the images, logo_overlay.png in the root is the watermark file, it can be changed to whatever you want.<br>
7. Bot combines the images and speech into a .mp4 file<br>
- If enabled, bot will combine videos together to form a longer video with multiple articles in it, transClip.mp4 in the root is the video that goes in between your generated videos, you can change this to whatever you want<br>
- If enabled, bot will post the .mp4 to a Facebook page.<br>
- If enabled, bot will add the generated hashtags to the end of the video description on Facebook.<br>
8. Bot will continue to generate until the python script is stopped.<br>
