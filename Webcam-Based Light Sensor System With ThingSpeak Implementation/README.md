# Project Overview
As the name of this project would imply, this intended purpose of this code is to use a webcam (either integrated or external usb) to 
measure the light in a room based off of the pictures it takes. The program will then analyze every pixel in the photo, calculate the 
light detected by the camera using the luminance formula (0.21 x R) + (0.72 x G) + (0.07 x B), and divide the total luminance score by the
number of pixels in the photo to determine the average light level. Once the light level is calculated, the function will send this 
score to a ThingSpeak server so that it can be graphed and later compared with the other average light scores. The function will run 60
times, in order for a minute's worth of recordings to have taken place. In between each function call, a delay of 16 seconds is implemented
to provide ThingSpeak time to plot the score before the next picture is taken. 

# Disclaimer
This project will require a webcam or integrated laptop camera, several thirdparty libraries, and a linux-based operating system preferably. 
I personally used Ubuntu to build and run this program, but I will point out that Windows Subsystems for Linux will most likely NOT work for 
this project due to some interal permissions issues with camera access. I have also been unable to test this with MacOS, so I cannot 
guarantee it will work either.

# Instructions to Run Program
1.) First, download OpenCV and Pillow for Python. These libraries are required for the program to be able to take the picture and analyze it.
    The instructions to download OpenCV can be found at [link](https://pypi.org/project/opencv-python/), and the instructions to download Pillow
    can be found at [link](https://pillow.readthedocs.io/en/stable/installation.html).
    
2.) With the necessary libraries having been installed, please download the `IoTFinal.py` file into a folder you also would like to have the
    picture saved in. 
    
3.) Now, users will need to set up an account with ThingSpeak in order to create the server space that will be hosting and displaying the 
    light data [link](https://thingspeak.com/). Once an account has been created, create a new channel. The name of the channel, the 
    description, and the name of Field 1 are not necessarily important, but there must be a Field 1, and the channel itself must have a 
    unique name of its own.
    
4.) Now that the ThingSpeak channel has been created, go to that channel and click on the "API Keys" tab that is between the "Sharing" and
    the "Data Import/Export" tab. Once within the tab, copy the auto-generated **"Write API KEY"** key. This key will be necessary to sending
    the light data to ThingSpeak, and will need to be added to the `IoTFinal.py` file.
    
5.) With the API key having been generated and copied, open the `IoTFinal.py` file in a text editor and scroll down to line 68. Here, users
    should see within the **'params'** variable a section labelled **'key': 'API KEY HERE'**. Delete the text *(API KEY HERE)* and paste the key 
    provided by ThingSpeak between the single quotation marks. Save this file, and close it.
    
6.) Finally, the last thing to do is to open a command prompt and go to the directory that the file was saved in. To run this python script,
    Type the command `python3 IoTFinal.py` in the terminal and smile for the camera!
    
# Results
The results of my tests of this program can be found on my google site! [link](https://sites.google.com/stevens.edu/ee629hat/final-project?authuser=0)
While you're there, feel free to check out some of the other work I've done for my EE629-A Internet of Things class!
