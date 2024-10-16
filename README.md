# Video Reversal using OpenCV

This project is a Python script that reads a video from a URL, creates a reversed version of the video, and then stacks the original and reversed videos side by side. The script also overlays two timers on the video: one running forward on the original video and another running backwards on the reversed video. The final output can be saved as both a reversed video and a stacked video.

![reversed_optimized](https://github.com/user-attachments/assets/1b81ebe0-5d46-4589-b4e1-c34fb5a3613f)


## Contents
1. [Features](#features)
2. [Requirements](#requirements)
3. [Installation](#installation)
4. [Usage](#usage)
5. [Explanation of Code](#explanation-of-code)
6. [Example Outputs](#example-outputs)

## Features

- Reverse the original video and save the reversed version.
- Stack the original and reversed videos horizontally.
- Display a forward timer on the original video and a backward timer on the reversed video.
- Save the stacked video with timers as a separate file.
- Resize the displayed output to fit the screen during playback.

## Requirements

This project uses Python and the OpenCV library to handle video manipulation. You'll need the following dependencies:

- **Python 3.x**: Ensure Python is installed on your system.
- **OpenCV**: You can install OpenCV using the command:

    ```bash
    pip install opencv-python
    ```

## Installation

1. Clone the repository:

    ```bash
    git clone https://github.com/Pushtogithub23/video-reversal-opencv.git
    ```

2. Navigate to the project directory:

    ```bash
    cd video-reversal-opencv
    ```

## Usage

To use the script, you can simply run the `save_reversed_and_stacked_video` function, specifying the video's URL and filenames for the output.

```python
save_reversed_and_stacked_video(video_url, save_video=True, reversed_filename='reversed_video.mp4', stacked_filename='stacked_video.mp4')
```

### Parameters

- **`video_url`**: The video URL to be processed (input video URL).
- **`save_video`**: A boolean flag (`True` or `False`) that determines whether to save the output videos.
- **`reversed_filename`**: The filename for saving the reversed video (if `save_video=True`).
- **`stacked_filename`**: The filename for saving the horizontally stacked video (if `save_video=True`).

### Example

```python
save_reversed_and_stacked_video(
    video_url="https://videos.pexels.com/video-files/7187055/7187055-hd_1920_1080_24fps.mp4",
    save_video=True, 
    reversed_filename="reversed_video_1.mp4", 
    stacked_filename="stacked_video_1.mp4"
)
```

## Explanation of Code

1. **Video Capture**:
   - The script reads the video from the provided URL using `cv.VideoCapture`. It checks if the video capture was successful. Otherwise, it raises an error.

2. **Extract Video Properties**:
   - The video's width, height, and frame rate (FPS) are retrieved, along with the total frame count, to calculate the video's duration.

3. **Frame Processing**:
   - The video frames are read into memory and stored in a list. The script then reverses this list of frames for later use.

4. **Timer Calculation**:
   - The script calculates a forward timer for the original video and a backward timer for the reversed video based on the frame index and frame rate. Each time is formatted as MM: SS.

5. **Overlaying Timers**:
   - Using OpenCV's `cv.putText()`, the timers are added to the top-left corner of both the original and reversed frames, positioned appropriately in the stacked frame.

6. **Stacking and Saving**:
   - The original and reversed frames are horizontally stacked using `cv.hconcat()`. If saving is enabled, both the reversed and stacked videos are written to files using `cv.VideoWriter`.

7. **Display and Cleanup**:
   - The stacked video is displayed in a resizable window. After processing, resources are released, and any opened windows are closed.

## Example Outputs
### Reversed Video Example
![reversed_video_1](https://github.com/user-attachments/assets/02459034-1711-469a-ab60-e995a2fdabfd)

### Stacked Video Example
![stacked_video_4](https://github.com/user-attachments/assets/69a953b4-d5eb-43a5-a9f9-654766eb0aae)

![stacked_video_1](https://github.com/user-attachments/assets/8eba03ab-e616-48d1-accc-8d996069bf98)

![stacked_video_with_timers](https://github.com/user-attachments/assets/15555b4f-ed2d-4e4d-afae-871417725d66)

The above GIFs show the reversed video and the stacked version, with the forward and backward timers overlaying on the original and reversed frames.

