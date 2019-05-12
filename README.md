# Plaza_Parking_Solutions
A smart parking system that can enable booking parking slots and also detect cars and update the slots.
Android App: The android app can only be run on Android studio. The file can be open through android studio. The required libraries is to be downloaded before running the file. Once there is no error after building the gradle, we can run the Android SDK to run it in an desktop emulator. Else we can enable the 'USB debugging' on an android mobile from 'Developer's Option'. Then we can upload run the app directly on the mobile by selecting the Android device from the 'Android SDK'.
Car Detection:
The main issue is how to detect the empty slots in parking area. So in the code 'drawing_utils' we store manually 4 points to define the parking area using mouse as a 'paintbrush'. Then with some calculation in code 'coordinate_generator' we mark the serial of each slot.After drawing the rectangles, all there was left to do was examine the area of each rectangle to see if there was a car in there or not.

By taking each (filtered and blurred) rectangle, determining the area, and doing an average on the pixels, I was able to tell when there wasn't a car in the spot if the average was high (more dark pixels). I changed the color of the bounding box accordingly and viola, a parking detection program!

The code for drawing the rectangles and motion detection is pretty generic. It's seperated out into classes and should be reusable outside of the context of a parking lot.

Running procedure-
One has to run in command line by going to the corresponding folder and running

'' python main.py --image images/parking_lot_1.png --data data/coordinates_1.yml --video
videos/parking_lot_1.mp4 --start-frame 400''.

Program flow is as follows:

User inputs file name for a video, a still image from the video, and a path for the output file of parking space coordinates.
User clicks 4 corners for each spot they want tracked. Presses 'q' when all desired spots are marked.
Video begins with the user provided boxes overlayed the video. Occupied spots initialized with red boxes, available spots with green.
Car leaves a space, the red box turns green.
Car drives into a free space, the green box turns red.

The data on the entering and exiting of these cars can be used for a number of purposes: closest spot detection, analytics on parking lot usage, and for those counters outside of parking garages that tell how many cars are on each level (to name a few).
