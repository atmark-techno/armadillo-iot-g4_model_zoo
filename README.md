# Armadillo-IoT G4 Model Zoo

[Armadillo-IoT ゲートウェイ G4](https://armadillo.atmark-techno.com/armadillo-iot-g4) + NPUで動作が確認済みの機械学習モデルをまとめたリポジトリです。

各種機械学習モデルの量子化手順と動作確認手順を、Pythonでの実装とともに Google Colaboratory ノートブック形式で紹介します。
動作確認手順は Armadillo-IoT ゲートウェイ G4 実機上でも同様に動作します。

## 機械学習の推論を Armadillo-IoT ゲートウェイ G4 上で動かしている際の動画

本リポジトリで紹介している機械学習モデルを用いた Armadillo-IoT ゲートウェイ G4 上で動作するデモアプリケーションの動画もYouTubeにアップロードしています。  
こちらは基本的には本リポジトリで紹介している動作確認手順の実装と大枠は同じですが、画面構成の変更や映像入力をUSBカメラにするなどの変更が加わっています。  

<table>
<tr>
<td>▼物体検出・姿勢推定・セグメンテーションデモ動画</td>
<td>▼超解像・手指検知デモ動画</td>
</tr>
<tr>
<td>
<a href="https://www.youtube.com/watch?v=gNu7BUy-BoI" >
<img src="https://user-images.githubusercontent.com/82640976/186608897-3be7f761-8e46-4673-a36f-f35dc60800d9.jpg">
</a>
</td>
<td>
<a href="https://www.youtube.com/watch?v=E9dYSni7pBc" >
<img src="https://user-images.githubusercontent.com/82640976/186611414-a236f32a-382c-4ac3-8659-f54e5ad899ef.jpg">
</a>
</td>
</tr>
</table>

<div align="center">
<b>画像クリックでYouTubeの動画ページに移動します。</b>
</div>
<br>

これらのデモアプリケーションは、Armadillo-IoT ゲートウェイ G4 上で実際に動かすことができます。
詳しくは、「[Armadillo-IoT ゲートウェイ G4 製品マニュアル](https://armadillo.atmark-techno.com/resources/documents/armadillo-iot-g4/manuals)」内の「デモアプリケーションを実行する」を参照してください。

## 物体検出

### ssd_mobilenet_v1

* [モデルDL](http://storage.googleapis.com/download.tensorflow.org/models/tflite/coco_ssd_mobilenet_v1_1.0_quant_2018_06_29.zip)
* [動作確認 Colab Note](https://colab.research.google.com/github/atmark-techno/armadillo-iot-g4_model_zoo/blob/main/GoogleColabNotebooks/ObjectDetection_OperationCheck.ipynb)

[Tensorflow Liteの物体検出サンプル](https://www.tensorflow.org/lite/models/object_detection/overview)(当該ページは削除済み)にて使用されているモデルです。COCOデータセットでトレーニングし、uint8で量子化されています。  
※使用されているモデルは異なりますが、[こちら](https://www.tensorflow.org/lite/examples/object_detection/overview?hl=ja)にTensorflow Liteの物体検出についてのページが新しく作成されています。

入力画像上の「どこに」、「何が」あるかを認識し、バウンディングボックスで表示できます。  
認識可能な物体は90種類あります。

<div align="center">
<img src="https://user-images.githubusercontent.com/82640976/186605942-a5514039-eb86-4753-a3e0-7bb673b38f77.png" width="75%">
</div>

## 骨格推定

### posenet

* [モデルDL](https://download.atmark-techno.com/armadillo-iot-g4/example/sample-models/posenet.tflite)
* [量子化 Colab Note](https://colab.research.google.com/github/atmark-techno/armadillo-iot-g4_model_zoo/blob/main/GoogleColabNotebooks/PoseEstimation_Quantize.ipynb)
* [動作確認 Colab Note](https://colab.research.google.com/github/atmark-techno/armadillo-iot-g4_model_zoo/blob/main/GoogleColabNotebooks/PoseEstimation_OperationCheck.ipynb)

[posenet-python](https://github.com/atomicbits/posenet-python)をベースにtfliteに変換、量子化したモデルです。

入力画像に写った人間の骨格(両目、鼻、両耳、両肩、両肘、両手首、両腰、両膝、両足首の計17点)を検知して表示します。  
最大10人の骨格を一度に推定できます。

<div align="center">
<img src="https://user-images.githubusercontent.com/82640976/186803220-de78f998-4f26-4bb9-987e-790a6f90e132.png" width="75%">
</div>

## セマンティックセグメンテーション

### MediaPipe_Meet_Segmentation

* [モデルDLスクリプト (c.f. PINTO_model_zoo)](https://raw.githubusercontent.com/PINTO0309/PINTO_model_zoo/main/082_MediaPipe_Meet_Segmentation/download_full_144x256.sh)
* [動作確認 Colab Note](https://colab.research.google.com/github/atmark-techno/armadillo-iot-g4_model_zoo/blob/main/GoogleColabNotebooks/ImageSegmentation_OperationCheck.ipynb)

[PINTO0309](https://github.com/PINTO0309)様がtfliteに変換、量子化したモデルです。具体的な量子化手順などの詳細は[PINTO_model_zoo](https://github.com/PINTO0309/PINTO_model_zoo/tree/main/082_MediaPipe_Meet_Segmentation)を参照してください。

入力画像の各画素ごとに、そこに写っているものは何かを推定し、人間が写っている領域を赤く色付けします。  
Google Meetのバーチャル背景のために使用されているモデルをベースとしていおり、人間の領域を綺麗に推定するために、人間以外の付近の物を検出する場合もあります。

<div align="center">
<img src="https://user-images.githubusercontent.com/82640976/186804263-fd2e74bb-0c3c-4050-aa55-ae34722b9093.png" width="75%">
</div>

## 超解像

### ESRGAN

* [モデルDL](https://download.atmark-techno.com/armadillo-iot-g4/example/sample-models/super_resolution.tflite)
* [量子化 Colab Note](https://colab.research.google.com/github/atmark-techno/armadillo-iot-g4_model_zoo/blob/main/GoogleColabNotebooks/SuperResolution_Quantize.ipynb)
* [動作確認 Colab Note](https://colab.research.google.com/github/atmark-techno/armadillo-iot-g4_model_zoo/blob/main/GoogleColabNotebooks/SuperResolution_OperationCheck.ipynb)

[esrgan-tf2](https://tfhub.dev/captain-pool/lite-model/esrgan-tf2/1)をベースにtfliteに変換、量子化したモデルです。

50x50の解像度の画像を入力することで、200x200の解像度の画像を生成します。

<div align="center">
<img src="https://user-images.githubusercontent.com/82640976/186805749-b18984c6-8d15-461f-a5b4-872f13a1bb49.png" width="75%">
</div>

## 手指検知

### MediaPipe_Hands

* [モデルDLスクリプト(手の領域検出) (c.f. PINTO_model_zoo)](https://raw.githubusercontent.com/PINTO0309/PINTO_model_zoo/main/033_Hand_Detection_and_Tracking/03_integer_quantization/download.sh)
* [モデルDLスクリプト(手の骨格検知) (c.f. PINTO_model_zoo)](https://raw.githubusercontent.com/PINTO0309/PINTO_model_zoo/main/033_Hand_Detection_and_Tracking/03_integer_quantization/download_new.sh)
* [動作確認 Colab Note](https://colab.research.google.com/github/atmark-techno/armadillo-iot-g4_model_zoo/blob/main/GoogleColabNotebooks/HandEstimation_OperationCheck.ipynb)

[PINTO0309](https://github.com/PINTO0309)様がtfliteに変換、量子化したモデルです。具体的な量子化手順などの詳細は[PINTO_model_zoo](https://github.com/PINTO0309/PINTO_model_zoo/tree/main/082_MediaPipe_Meet_Segmentation)を参照してください。  
モデルの詳細については、[MediaPipe Hands Model Card](https://mediapipe.page.link/blazepose-mc)を参照してください。

以下の流れで手指の検出を行ないます。

1. 入力画像から手の領域を検出
1. 検出した領域を入力画像として骨格推定
1. 推定結果を元の入力画像に描画

このデモの特徴としまして、機械学習モデルを2つ(手の領域検出、手の骨格推定)使用しています。  
Armadillo-IoT ゲートウェイ G4上でも複数モデルをロードして推論を行なうことができます。

<div align="center">
<img src="https://user-images.githubusercontent.com/82640976/186815999-9ec4d0a5-4f55-405b-9797-32de29467ca9.png" width="75%">
</div>

