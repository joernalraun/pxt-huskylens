# HuskyLens

[HuskyLens is an easy-to-use ai vision sensor with six built-in functions: face recognition, object tracking, object recognition, line tracking, color recognition, and label (qr code) recognition.](https://www.dfrobot.com.cn/goods-2050.html)

## Basic usage

* HuskyLens I2C initialization and pattern selection.（HuskyLens I2C初始化和模式选择。）

```blocks

    huskylens.initI2c()
    huskylens.initMode(protocolAlgorithm.ALGORITHM_FACE_RECOGNITION)

```

* HuskyLens requests the data and stores the requested data in the result for later use.（HuskyLens请求数据并将请求的数据存储在结果中以供以后使用。）

```blocks

    basic.forever(function () {
        huskylens.request()
    })

```

* HuskyLens retrieves the desired result from the result（For example, get the X center of the ID1 box）（HuskyLens从结果中检索所需的结果）

```blocks

    huskylens.initI2c()
    huskylens.initMode(protocolAlgorithm.ALGORITHM_FACE_RECOGNITION)
    basic.forever(function () {
        huskylens.request()
        if (huskylens.isLearned(1)) {
            if (huskylens.isAppear(1, HUSKYLENSResultType_t.HUSKYLENSResultBlock)) {
                serial.writeValue("box", huskylens.readeBox(1, Content1.xCenter))
            }
        }
    })

```

* HuskyLens retrieves the parameters of the center box on the screen from the result（HuskyLens从结果中检索屏幕中央框的参数）

```blocks

    huskylens.initI2c()
    huskylens.initMode(protocolAlgorithm.ALGORITHM_FACE_RECOGNITION)
    basic.forever(function () {
        huskylens.request()
        serial.writeValue("box", huskylens.readBox_s(Content3.ID))
    })

```

* HuskyLens takes the parameters of the NTH box from the result（HuskyLens从结果中获取第n个框的参数）

```blocks
    huskylens.initI2c()
    huskylens.initMode(protocolAlgorithm.ALGORITHM_FACE_RECOGNITION)
    basic.forever(function () {
        huskylens.request()
        serial.writeValue("box", huskylens.readBox_ss(1, Content3.ID))
    })

```
## License

MIT

Copyright (c) 2020, microbit/micropython Chinese community  

## Supported targets

* for PXT/microbit
(The metadata above is needed for package search.)
