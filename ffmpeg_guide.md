## Collection of notes to be used for scripting processing

To save one frame of input.mov every four seconds to output_0000.png, output_0001.png etc.:

ffmpeg -i input.mov -r 0.25 output_%04d.png

Change the %xd to however many digits you need, e.g. if the command would create more than 10,000 frames change the %04d to %05d. This also works for input files that are image sequence. Read more here.

+++

To encode all videos in a directory:

$ mkdir encoded
$ for f in *.avi; do ffmpeg -i "$f" -c:v libx264 -crf 23 -preset medium \
  -c:a aac -b:a 128k -movflags +faststart -vf scale=-2:720,format=yuv420p \
  "encoded/${f%.avi}.mp4"; done


+++
