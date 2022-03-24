# Scroll

## QScrollBar

- スクロールバー相互接続(同期)
- 
```cpp
コンストラクタ｛
    connect(ui->objname1->verticalScrollBar(), SIGNAL(valueChanged(int)), ui->objname2->verticalScrollBar(), SLOT(setValue(int)));
    connect(ui->objname2->verticalScrollBar(), SIGNAL(valueChanged(int)), ui->objname1->verticalScrollBar(), SLOT(setValue(int)));
}
```

- スクロール自動追尾

```cpp
リストを追加する関数など{
    ui->objname->verticalScrollBar()->setValue(ui->objname->verticalScrollBar()->maximum());
}
```
