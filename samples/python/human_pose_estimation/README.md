# Human Pose Detection And Estimation Python Sample

This sample demonstrates how construct and control GStreamer pipeline from Python application, and how to access metadata generated by inference elements and attached to image buffer.

## How It Works
The sample utilizes GStreamer function `gst_parse_launch` to construct the pipeline from string representation. Then callback function is set on source pin of `gvawatermark` element in the pipeline.

The callback is invoked on every frame, it loops through inference metadata attached to the frame, converts raw tensor data into text labels, and visualizes the label around detected objects.

Note that this sample doesn't contain .json files with post-processing rules as post-processing of classification results performed by sample itself (inside callback function), not by `gvaclassify` element.

## Models

The sample uses by default the following pre-trained models from OpenVINO™ [Open Model Zoo](https://github.com/opencv/open_model_zoo)
*   __person-vehicle-bike-detection-crossroad-0078__ is primary detection network for finding human
*   __human-pose-estimation-0001__ human pose estimation on detected humans

> **NOTE**: Before running samples (including this one), run script `download_models.sh` once (the script located in `samples` top folder) to download all models required for this and other samples.

## Running

```sh
./human_pose_estimation.sh [INPUT_VIDEO]
```

If no input parameters specified, the sample by default streams video example from HTTPS link (utilizing `urisourcebin` element) so requires internet connection.
The command-line parameter INPUT_VIDEO allows to change input video and supports
* local video file
* web camera device (ex. `/dev/video0`)
* RTSP camera (URL starting with `rtsp://`) or other streaming source (ex URL starting with `http://`)

## Sample Output

The sample
* prints GStreamer pipeline string as passed to function `gst_parse_launch`
* starts the pipeline and visualizes video with bounding boxes around detected humans, and anticulares and skeleton for each detected human

## See also
* [DL Streamer samples](../../README.md)