# SignalSlot

## 自作signal関数

- Q_OBJECTをヘッダーファイルに記述(マクロ)
- qmake実行(メニューバーのビルド>qmake実行)

```cpp
//hearder

class hoge : public QObject
{
  Q_OBJECT

public;
  hoge(); //constructor
  
  void hogehoge();
  
signal:
  void valueChange();

}

```

```cpp
//cpp

#include "hearder.h"

void hoge::hogehoge(){

  if(ahoge)
    emit valueChange();

}
