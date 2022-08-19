# Armadillo-IoT G4 model zoo

Armadillo-IoT ゲートウェイ G4 + NPUで動作が確認できた、量子化された機械学習モデルをまとめたリポジトリです。

## モデルリスト

| ベースモデル | モデルの説明 | DL link | 量子化手順/動作確認手順(Google Colaboratory) |
|:-:|-|:-:|-|
| ssd_mobilenet_v1 | [Tensorflow Liteの物体検出サンプル](https://www.tensorflow.org/lite/models/object_detection/overview)(当該ページは削除済み)にて使用されているモデルです。COCOデータセットでトレーニングし、uint8で量子化されています。<br>※使用されているモデルは異なりますが、[こちら](https://www.tensorflow.org/lite/examples/object_detection/overview?hl=ja)にTensorflow Liteの物体検出についてのページが新しく作成されています。 | [モデルDL](http://storage.googleapis.com/download.tensorflow.org/models/tflite/coco_ssd_mobilenet_v1_1.0_quant_2018_06_29.zip) | [動作確認 Colab Note](https://colab.research.google.com/github/atmark-techno/armadillo-iot-g4_model_zoo/blob/main/GoogleColabNotebooks/ObjectDetection_OperationCheck.ipynb) |
| posenet | [posenet-python](https://github.com/atomicbits/posenet-python)をベースにtfliteに変換、量子化したモデルです。 | [モデルDL](https://download.atmark-techno.com/armadillo-iot-g4/example/sample-models/posenet.tflite) | [量子化 Colab Note](https://colab.research.google.com/github/atmark-techno/armadillo-iot-g4_model_zoo/blob/main/GoogleColabNotebooks/PoseEstimation_Quantize.ipynb)<br>[動作確認 Colab Note](https://colab.research.google.com/github/atmark-techno/armadillo-iot-g4_model_zoo/blob/main/GoogleColabNotebooks/PoseEstimation_OperationCheck.ipynb) |
| MediaPipe_Meet_Segmentation | [PINTO0309](https://github.com/PINTO0309)様がtfliteに変換、量子化したモデルです。具体的な量子化手順や、モデルのダウンロード方法などの詳細は[PINTO_model_zoo](https://github.com/PINTO0309/PINTO_model_zoo/tree/main/082_MediaPipe_Meet_Segmentation)を参照してください。 | - | [動作確認 Colab Note](https://colab.research.google.com/github/atmark-techno/armadillo-iot-g4_model_zoo/blob/main/GoogleColabNotebooks/ImageSegmentation_OperationCheck.ipynb) |
| ESRGAN | [esrgan-tf2](https://tfhub.dev/captain-pool/lite-model/esrgan-tf2/1)をベースにtfliteに変換、量子化したモデルです。 | [モデルDL](https://download.atmark-techno.com/armadillo-iot-g4/example/sample-models/super_resolution.tflite) | [量子化 Colab Note](https://colab.research.google.com/github/atmark-techno/armadillo-iot-g4_model_zoo/blob/main/GoogleColabNotebooks/SuperResolution_Quantize.ipynb)<br>[動作確認 Colab Note](https://colab.research.google.com/github/atmark-techno/armadillo-iot-g4_model_zoo/blob/main/GoogleColabNotebooks/SuperResolution_OperationCheck.ipynb) |
