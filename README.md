# FYP - SignChat
SignChat application is an iOS application which translate sign language. It applies Multi-hand Tracking ML solutions in [MediaPipe](https://github.com/google/mediapipe) framework to capture sign data.

# Competition
Third Prize (Information Technology) The 6-th Hong Kong University Student Innovation and Entrepreneurship Competition
https://www.hkchallengeplus.com/en/

## Introduction & Demo
[![Watch the video](https://img.youtube.com/vi/xQbxFl4ju1Y/0.jpg)](https://www.youtube.com/watch?v=xQbxFl4ju1Y "Watch the video")

[![Watch the video](https://img.youtube.com/vi/82r3OOJMhio/0.jpg)](https://www.youtube.com/watch?v=82r3OOJMhio "Watch the video")

## Interviewed by Hong Kong Television Broadcasts Limited
[![Watch the video](https://img.youtube.com/vi/kPpcmBiDhhA/0.jpg)](https://www.youtube.com/watch?v=kPpcmBiDhhA&list=PLci2z87RuSLwgzTVfzN5kCzeaT8njKZ6i&index=3 "Watch the video")

## Installation
1. Follw the [instructions](https://github.com/google/mediapipe/blob/master/mediapipe/docs/mediapipe_ios_setup.md) to set up Mediapipe for iOS.
2. Remove all the files in `mediapipe/examples/ios/multihandtrackinggpu`.
   
   ```
   rm -r mediapipe/examples/ios/multihandtrackinggpu/*
   ```
   
3. Clone the SignChat repository to folder `mediapipe/examples/ios/multihandtrackinggpu`.

   ```
   cd mediapipe/examples/ios/multihandtrackinggpu
   git clone https://github.com/eching0519/FYP-SignChat.git
   ```
   
4. Run the project in XCode.

### Team Members
- [Yannis Ng](https://github.com/eching0519) : System design, UI design, Plugin application, Implementation
- [Oscar Chan](https://github.com/oscarNCC): Database design, Documentation, Implementation
- Hin
