# Scroll

## QScrollBar

- スクロールバー相互接続(同期)
```cpp
//Qt4
constructor｛
    connect(ui->objname1->verticalScrollBar(), SIGNAL(valueChanged(int)), ui->objname2->verticalScrollBar(), SLOT(setValue(int)));
    connect(ui->objname2->verticalScrollBar(), SIGNAL(valueChanged(int)), ui->objname1->verticalScrollBar(), SLOT(setValue(int)));
}

//Qt5
constructor｛
    connect(ui->objname1->verticalScrollBar(), &QAbstractSlider::valueChanged, ui->objname2->verticalScrollBar(), &QAbstractSlider::setValue);
    connect(ui->objname2->verticalScrollBar(), &QAbstractSlider::valueChanged, ui->objname1->verticalScrollBar(), &QAbstractSlider::setValue);
}

```

- スクロール自動追尾
```cpp
リストを追加する関数など{
    ui->~~~~~->insertPlainText("hohoge \n"); //add list
    ui->objname->verticalScrollBar()->setValue(ui->objname->verticalScrollBar()->maximum());
}
```
