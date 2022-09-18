# rust-mmdeploy
Safe MMDeploy Rust wrapper.

## Prerequisites

In order to successfully build this repo, you are supposed to install some pre-packages.

The following guidance is tested on x86 device on Ubuntu OS.

**Step 1.** Install Clang required by `Bindgen`.

```bash
apt install llvm-dev libclang-dev clang
```

**Step 2.** Download and install pre-built mmdeploy package. In this guidance, we choose a MMdepoloy prebuilt package target on ONNXRUNTIME-linux-x86.

```bash
wget https://github.com/open-mmlab/mmdeploy/releases/download/v0.8.0/mmdeploy-0.8.0-linux-x86_64-onnxruntime1.8.1.tar.gz
tar -zxvf mmdeploy-0.8.0-linux-x86_64-onnxruntime1.8.1.tar.gz
cd mmdeploy-0.8.0-linux-x86_64-onnxruntime1.8.1.tar.gz
export $MMDEPLOY_DIR=$(pwd)
```

**Step 3.** Install OpenCV required by examples.

```bash
apt install libopencv-dev
```


## Quickstart

Please read the previous section to make sure the required packages have been installed before using this crate.

Update your *Cargo.toml*

```toml
mmdeploy = "0.2.0"
```

## APIs for MM Codebases

Take a look by running some examples!

### Detector API

Deploy object detection models converted by MMDeploy.

The example deploys a FasterRCNN model converted by ONNXRUNTIME target on CPU device.

Before deploying, please follow the guidance from MMDeploy documentation to install it and convert an appropriate model in `../mmdeploy_model/faster-rcnn-ort`. An optional operation required to fetch MMDetection codebase into `../mmdetection/`. In this example, we use demo-image from it.

```bash
cargo run --example detector cpu ../mmdeploy_model/faster-rcnn-ort ../mmdetecton/demo/demo.jpg
```

A rendered result we can take a look located in the current directory and is named `output_detection.png`.

![](images/output_detection.png)

Good news: Now, you can use Rust language to build your fantastic applications powered by MMDeploy!

### TOSupport List

[ ] Classifier
[x] Detector
[ ] Segmentor
[ ] Pose Detector
[ ] Rotated Detector
[ ] Text Detector
[ ] Text Recognizer
[ ] Restorer