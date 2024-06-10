# totally-real-news-bot
Generates AI text/images/video based on a NYT news headline, can be modified to create other content.

Writing documentation now.

Here's some examples of output: https://www.facebook.com/profile.php?id=61560732713412&sk=videos

Requires:<br>
- Python 3<br>
- A working install of text-generation-webui with the --api flag enabled<br>(https://github.com/oobabooga/text-generation-webui)<br>
- Alltalk_tts extension for text-generation-webui installed with api access enabled.<br>(https://github.com/erew123/alltalk_tts)<br>
- A working install of stable-diffusion-webui with  --api enabled in COMMANDLINE_ARGS<br>(https://github.com/AUTOMATIC1111/stable-diffusion-webui)<br>
- A New York Times API access key<br>(https://developer.nytimes.com/get-started)<br>
- (optional) A Facebook page access token<br>

Basic process overview:<br>
- Bot grabs a NYT headline and short description<br>
- Bot uses text-generation-webui to analyse the headline for tone and stores it.<br>
- Bot generates a news article text based on the headline and short description, asks bot to write in the stored tone.<br>
- Bot uses Alltalk_tts to generate speech based on the generated article text, outputs a .wav file
- Bot starts generating 4 images based on the headline, it will start generating using what ever model is loaded into stable-diffusion-webui, outputs .png files<br>
- Bot combines the images and speech into a .mp4 file<br>
- If enabled, bot will post the .mp4 to a Facebook page.<br>
- Bot will continue to generate until the python script is stopped.<br>
