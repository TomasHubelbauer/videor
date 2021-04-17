# Videor

Videor is an online web application for making short videos. Its UI allows the
user to place various elements to make up the video. The finished video can be
exported directly from the browser.

## Status

Work in progress: nothing is done.

## Method

At the core of this application is the [`MediaRecorder`] API.

[`MediaRecorder`]: https://developer.mozilla.org/en-US/docs/Web/API/MediaRecorder

The video gets built up using a `canvas` element. The `MediaRecorder` instance
uses the `canvas` element to generate frames of the video.

## To-Do

### Figure out the best way to generate the video frames fast & without stutter

[`captureStream`] has a `frameRate` argument. The documentation says when `0` is
supplied, the `requestFrame` method can be used to tell `MediaRecorder` to use
the current state of the canvas for a frame. This seems preferable to setting
the frame-rate upfront, because then the video must be generated in real time.
The video will lag in case the code for generating the frames can't keep up with
the desired frame rate. But even if it can, the video cannot be generated faster
than real-time. Ideally, I'd find a way to generate the frames as fast as they
can be generated and generate the video faster than its intended runtime, but
also prevent the video from being laggy in case the frames can't be generated in
real-time.

[`captureStream`]: https://developer.mozilla.org/en-US/docs/Web/API/HTMLCanvasElement/captureStream

