# Serial
シリアル通信ライブラリ関連
## QSerialPort
```cpp
#include <QSerialPort> //ポート関連ヘッダー
```

- 受信割り込み関数(mainwindow.h)
```cpp
private slots:
  void event(){
    QByteArray receiveData = serial->readAll();  //受信データ代入
    
    //表示プログラムとか
    
  }
```

- mainwindow.cpp
```cpp
QSerialPort *serial; //conect関数に渡すため

コンストラクタ{
    serial = new QSerialPort(this);
    connect(serial, &QIODevice::readyRead, this, &MainWindow::event); //関数設定
    serial->setPortName("com3"); //ポート番号(QString)
    serial->setBaudRate(115200); //通信速度
    serial->setDataBits(QSerialPort::Data8);
    serial->setParity(QSerialPort::NoParity);
    serial->setStopBits(QSerialPort::OneStop);
    serial->setFlowControl(QSerialPort::NoFlowControl);
    serial->open(QIODevice::ReadWrite); //ポートを開く
}
```
- その他関数

`bool serial->isOpen()` ポートが開いているかどうか

`void serial->close()` ポート閉じる


## QSerialPortInfo
```cpp
#include <QSerialPortInfo> //使用可能なポート情報をくれるヘッダー
```

```cpp
QString portName;
QString portData;
foreach (const QSerialPortInfo &info, QSerialPortInfo::availablePorts()){
    portName = info.portName(); //使用可能ポートをすべて取得
    portData = info.description(); //ポートの情報?を取得
}
```
- その他関数

`QSerialPortInfo::availablePorts()` ポート情報のリストを返す

- ポート数求める
```cpp
QList<QSerialPortInfo> portList = QSerialPortInfo::availablePorts();
int portNum = portList.count();
```
