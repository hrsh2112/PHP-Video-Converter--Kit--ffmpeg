** FFmpeg Extension for Video Processing without any php extension Requirement For Windows (for Ubantu install it using "sudo apt-get install ffmpeg" command )

Introduction
============
FFmpeg Extension for Video Processing without any php extension Requirement For Windows.Using by this plugin you can do versatile operation such as you can convert video into other format,grab screen shot of specific second from video , convert video into single gif file, convert video in to audio  , convert video into serialize images.

# Developed By : 
HARSH PATEL

# Version : 
1.0

Documentation
-------------
This Package Contains Following Files
1.Code
2.input
3.output
4.Commands 


1.Code 

In this Folder you can find demo.php which contain some ffmpeg commands to convert video into different formate,Capture Image of specific seconds from video,Convert audio from video , etc.
You can here one "ffmpeg.exe" please do not delete it is require for execution.
   
2.input 

This Folder contains sample avi video. 

3.output

In this Folder you will get converted video as per path set in demo.php. 

4.Commands

Here you can find some useful ffmpeg commands.

(as per your requirement you can change input output folder path)  

Operating system Support
---------------
- Windows
- Linux
- Ubantu (sudo apt-get install ffmpeg)


License
-------
This Package is an open source project by HARSH PATEL 

USEFUL COMMANDS
----------

1. Cut video file into a smaller clip
=====================================

You can use the time offset parameter (-ss) to specify the start time stamp in HH:MM:SS.ms format while the -t parameter is for specifying the actual duration of the clip in seconds.

==> ffmpeg -i input.mp4 -ss 00:00:50.0 -codec copy -t 20 output.mp4


2. Split a video into multiple parts
====================================

If you want to split a large video into multiple smaller clips without re-encoding, ffmpeg can help. This command will split the source video into 2 parts – one ending at 50s from the start and the other beginning at 50s and ending at the end of the input video.

=> ffmpeg -i video.mp4 -t 00:00:50 -c copy small-1.mp4 -ss 00:00:50 -codec copy small-2.mp4

3. Convert video from one format to another
===========================================

You can use the -vcodec parameter to specify the encoding format to be used for the output video. Encoding a video takes time but you can speed up the process by forcing a preset though it would degrade the quality of the output video.

=> ffmpeg -i youtube.flv -c:v libx264 filename.mp4
=> ffmpeg -i video.wmv -c:v libx264 -preset ultrafast video.mp4

4. Join (concatenate) video files
=================================

If you have multiple audio or video files encoded with the same codecs, you can join them into a single file using FFmpeg. Create a input file with a list of all source files that you wish to concatenate and then run this command.

=> ffmpeg -f concat -i file-list.txt -c copy output.mp4

5. Mute a video (Remove the audio component)
============================================

Use the -an parameter to disable the audio portion of a video stream.

=> ffmpeg -i video.mp4 -an mute-video.mp4

6. Extract the audio from video
===============================

The -vn switch extracts the audio portion from a video and we are using the -ab switch to save the audio as a 256kbps MP3 audio file.

=> ffmpeg -i video.mp4 -vn -ab 256 audio.mp3

7. Convert a video into animated GIF
====================================

FFmpeg is an excellent tool for converting videos into animated GIFs and the quality isn’t bad either. Use the scale filter to specify the width of the GIF, the -t parameter specific the duration while -r specifies the frame rate (fps).

=> ffmpeg -i video.mp4 -vf scale=500:-1 -t 10 -r 10 image.gif

8. Extract image frames from a video
====================================

This command will extract the video frame at the 15s mark and saves it as a 800px wide JPEG image. You can also use the -s switch (like -s 400×300) to specify the exact dimensions of the image file though it will probably create a stretched image if the image size doesn’t follow the aspect ratio of the original video file.

=> ffmpeg -ss 00:00:15 -i video.mp4 -vf scale=800:-1 -vframes 1 image.jpg

9. Convert Video into Images
============================

You can use FFmpeg to automatically extract image frames from a video every ‘n’ seconds and the images are saved in a sequence. This command saves image frame after every 4 seconds.

=> ffmpeg -i movie.mp4 -r 0.25 frames_%04d.png

10. Merge an audio and video file
=================================

You can also specify the -shortest switch to finish the encoding when the shortest clip ends.

=> ffmpeg -i video.mp4 -i audio.mp3 -c:v copy -c:a aac -strict experimental output.mp4
=> ffmpeg -i video.mp4 -i audio.mp3 -c:v copy -c:a aac -strict experimental -shortest output.mp4

11. Resize a video
==================

Use the size (-s) switch with ffmpeg to resize a video while maintaining the aspect ratio.

=> ffmpeg -i input.mp4 -s 480x320 -c:a copy output.mp4

12. Create video slideshow from images
======================================

This command creates a video slideshow using a series of images that are named as img001.png, img002.png, etc. Each image will have a duration of 5 seconds (-r 1/5).

=> ffmpeg -r 1/5 -i img%03d.png -c:v libx264 -r 30 -pix_fmt yuv420p slideshow.mp4

13. Add a poster image to audio
===============================

You can add a cover image to an audio file and the length of the output video will be the same as that of the input audio stream. This may come handy for uploading MP3s to YouTube.

=> ffmpeg -loop 1 -i image.jpg -i audio.mp3 -c:v libx264 -c:a aac -strict experimental -b:a 192k -shortest output.mp4

14. Convert a single image into a video
=======================================

Use the -t parameter to specify the duration of the video.

=> ffmpeg -loop 1 -i image.png -c:v libx264 -t 30 -pix_fmt yuv420p video.mp4

15. Add subtitles to a movie
============================

This will take the subtitles from the .srt file. FFmpeg can decode most common subtitle formats.

=> ffmpeg -i movie.mp4 -i subtitles.srt -map 0 -map 1 -c copy -c:v libx264 -crf 23 -preset veryfast output.mkv

16. Crop an audio file
======================

This will create a 30 second audio file starting at 90 seconds from the original audio file without transcoding.

=> ffmpeg -ss 00:01:30 -t 30 -acodec copy -i inputfile.mp3 outputfile.mp3

17. Change the audio volume
===========================

You can use the volume filter to alter the volume of a media file using FFmpeg. This command will half the volume of the audio file.

=> ffmpeg -i input.wav -af 'volume=0.5' output.wav

18. Rotate a video
==================

This command will rotate a video clip 90° clockwise. You can set transpose to 2 to rotate the video 90° anti-clockwise.

=> ffmpeg -i input.mp4 -filter:v 'transpose=1' rotated-video.mp4

This will rotate the video 180° counter-clockwise.

=> ffmpeg -i input.mp4 -filter:v 'transpose=2,transpose=2' rotated-video.mp4

19. Speed up or Slow down the video
===================================

You can change the speed of your video using the setpts (set presentation time stamp) filter of FFmpeg. This command will make the video 8x (1/8) faster or use setpts=4*PTS to make the video 4x slower.

=> ffmpeg -i input.mp4 -filter:v "setpts=0.125*PTS" output.mp4

20. Speed up or Slow down the audio
====================================

For changing the speed of audio, use the atempo audio filter. This command will double the speed of audio. You can use any value between 0.5 and 2.0 for audio.

=> ffmpeg -i input.mkv -filter:a "atempo=2.0" -vn output.mkv