# Armadillo-IoT G4 model zoo

Armadillo-IoT ゲートウェイ G4のNPU上で動作できるように量子化された機械学習モデルをまとめたリポジトリです。

## モデルリスト

| ベースモデル | モデルの説明 | DL link | 量子化手順/動作確認手順(Google Colaboratory) |
|:-:|-|:-:|-|
| ssd_mobilenet_v1 | [Tensorflow Liteの物体検出サンプル](https://www.tensorflow.org/lite/models/object_detection/overview)(当該ページは削除済み)にて使用されているモデルです。COCOデータセットでトレーニングし、uint8で量子化されています。<br>※使用されているモデルは異なりますが、[こちら](https://www.tensorflow.org/lite/examples/object_detection/overview?hl=ja)にTensorflow Liteの物体検出についてのページが新しく作成されています。 | [モデルDL](https://download.atmark-techno.com/armadillo-iot-g4/example/sample-models/ssd_mobilenet_v1_quant.tflite) | [動作確認 Colab Note]() |
