# Copyright 2019 The MediaPipe Authors.
#
# Licensed under the Apache License, Version 2.0 (the "License");
# you may not use this file except in compliance with the License.
# You may obtain a copy of the License at
#
#      http://www.apache.org/licenses/LICENSE-2.0
#
# Unless required by applicable law or agreed to in writing, software
# distributed under the License is distributed on an "AS IS" BASIS,
# WITHOUT WARRANTIES OR CONDITIONS OF ANY KIND, either express or implied.
# See the License for the specific language governing permissions and
# limitations under the License.

load(
    "@build_bazel_rules_apple//apple:ios.bzl",
    "ios_application",
)

licenses(["notice"])  # Apache 2.0

MIN_IOS_VERSION = "11.0"

# To use the 3D model instead of the default 2D model, add "--define 3D=true" to the
# bazel build command.
config_setting(
    name = "use_3d_model",
    define_values = {
        "3D": "true",
    },
)

genrule(
    name = "model",
    srcs = select({
        "//conditions:default": ["//mediapipe/models:hand_landmark.tflite"],
        ":use_3d_model": ["//mediapipe/models:hand_landmark_3d.tflite"],
    }),
    outs = ["hand_landmark.tflite"],
    cmd = "cp $< $@",
)

ios_application(
    name = "MultiHandTrackingGpuApp",
    app_icons = glob(["Assets.xcassets/AppIcon.appiconset"]),
    bundle_id = "com.eching.Sign-Chat",
    families = [
        "iphone",
        "ipad",
    ],
    infoplists = ["Info.plist"],
    minimum_os_version = MIN_IOS_VERSION,
    provisioning_profile = "provisioning_profile.mobileprovision",
    deps = [
        ":MultiHandTrackingGpuAppLibrary",
        "@ios_opencv//:OpencvFramework",
    ],
)

objc_library(
    name = "MultiHandTrackingGpuAppLibrary",
    srcs = glob(["*.m"]) + glob(["*.mm"]) + glob(["IQKeyboardManager/*.m"]),
    hdrs = glob(["*.h"]) + glob(["IQKeyboardManager/*.h"]),
    data = [
        "Base.lproj/LaunchScreen.storyboard",
        "Base.lproj/Main.storyboard",
        ":model",
        "//mediapipe/graphs/hand_tracking:multi_hand_tracking_mobile_gpu_binary_graph",
        "//mediapipe/models:palm_detection.tflite",
        "//mediapipe/models:palm_detection_labelmap.txt",
    ] + glob(["Assets.xcassets/**"]),
    sdk_frameworks = [
        "AVFoundation",
        "CoreGraphics",
        "CoreMedia",
        "UIKit",
        "SceneKit",
        "NaturalLanguage",
        "Speech",
    ],
    deps = [
        "//mediapipe/objc:mediapipe_framework_ios",
        "//mediapipe/objc:mediapipe_input_sources_ios",
        "//mediapipe/objc:mediapipe_layer_renderer",
    ] + select({
        "//mediapipe:ios_i386": [],
        "//mediapipe:ios_x86_64": [],
        "//conditions:default": [
            "//mediapipe/graphs/hand_tracking:multi_hand_mobile_calculators",
            "//mediapipe/framework/formats:landmark_cc_proto",
        ],
    }),
)
