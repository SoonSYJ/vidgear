<h1 align="center"><img alt="vidgear Logo" src="https://raw.githubusercontent.com/abhiTronix/Imbakup/master/Images/vidgear.png" width="50%" height="50%"></h1>

**VidGear** is a lightweight python wrapper around OpenCV [Video I/O module](https://docs.opencv.org/master/d0/da7/videoio_overview.html) that contains powerful multi-thread modules(gears) to enable high-speed video frames read functionality across various devices and platforms. It is a reworked implementation of [imutils](https://github.com/jrosebr1/imutils) library's video modules with all major bugs fixed and comes with addition features like direct network streaming(*GStreamer Pipeline supported*) and flexible direct source parameters/attributes manipulation of OpenCV's [VideoCapture Class properties](https://docs.opencv.org/master/d4/d15/group__videoio__flags__base.html#gaeb8dd9c89c10a5c63c139bf7c4f5704d) on the go. This library is also very well compatible with Raspberry Pi Camera module's [Picamera library](http://picamera.readthedocs.io/) and provides us the ability exploit its various features like `brightness, saturation, sensor_mode` etc. easily. This library supports *Python 2.7 and all above versions.*

## Features:
Key features which differentiates from the other existing multi-threaded open source solutions:
- [x]  Multi-Threaded high-speed OpenCV video-frame capturing(resulting in High FPS)
- [x]  Flexible Direct control over the video stream
- [x]  Lightweight
- [x]  Built-in Robust Error and frame synchronization Handling
- [x]  Multi-Platform compatibility
- [x]  Full Support for Network Video Streams(*Including Gstreamer Raw Video Capture Pipeline*) 

## Installation

**VidGear requires [OpenCV](https://www.pyimagesearch.com/2018/05/28/ubuntu-18-04-how-to-install-opencv/) and [Picamera](https://picamera.readthedocs.io/en/release-1.13/install.html) (*Only if you want to use Raspberry Pi Camera Module*) libraries installation prior to its installation (*Latest versions recommended*).**

- **From PyPI(Stable Only):** `vidgear` can be easily installed as follows(*available on [Python Package Index (PyPI)](https://pypi.org/project/vidgear/)*):
  ```bash
  sudo pip install vidgear
  ```
- **Clone this repository(For Development):** You can also directly clone this repo. for latest patches(*maybe experimental*) and development purposes and thereby can install `VidGear`as follows:
  ```bash
  git clone https://github.com/abhiTronix/vidgear.git
  cd vidgear
  sudo pip install .
  ```
- **Conda Install:**  Anaconda prefers to use its own `conda package manager`, but it’s also possible to install packages using `pip` as follows:
   ```bash
   pip install vidgear
   ```

## Documentation and Usage

<h3 align="center">You can checkout vidgear <a href = https://github.com/abhiTronix/vidgear/wiki>Wiki-Section</a> for detailed documentation with examples for each Class(Gear).</h3>

### Basic example: 

The basic example of VideoGear Class for webcam stream is as follows :

```python
# import required libraries
from vidgear.gears import VideoGear
import cv2

stream = VideoGear(enablePiCamera = False, source=0).start() 
# define various attributes and start the stream

# infinite loop
while True:
	
	frame = stream.read()
	# read frames

	# check if frame is None
	if frame is None:
		#if True break the infinite loop
		break
	
	# do something with frame here
	
	cv2.imshow("Output Frame", frame)
	# Show output window

	key = cv2.waitKey(1) & 0xFF
	# check for 'q' key-press
	if key == ord("q"):
		#if 'q' key-pressed exit loop
		break

cv2.destroyAllWindows()
# close output window

stream.stop()
# safely close video stream.
```


## Contribution and Development
You are welcome to contribute with suggestions, feature requests and [pull requests](https://github.com/abhiTronix/vidgear/pulls).

## Author

- Abhishek Thakur [@abhiTronix](https://github.com/abhiTronix)

## License

Copyright © 2019 Abhitronix

This project is under the MIT License. See the LICENSE file for the full license text.
