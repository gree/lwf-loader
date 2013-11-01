lwf-loader.js リソースガイドライン
===============================

### lwf-loader固有ルール

デフォルトの状態でのリソースは以下の状態のように配置することを想定しています。

* 画像の配置
    * LWF再生に必要なすべての画像を`prefix`もしくは`imagePrefix`で指定したディレクトリ内に配置する。
    * LWFの仕様上、`prefix`のみが定義されていた場合、`imagePrefix`に`prefix`の値が代入される。


### imageMapで画像pathを直接指定する

デフォルトのルールに従わずに、直接`imageMap`のパラメータにリンケージ名とそのパスを指定することもできます。

* imageMapを定義する(例)

```javascript
    var setting = {
        imageMap: {
            "lwf_foo.png": "/IMG_PATH/foo.png",
            "misc_item_1.png": "/IMG_PATH/1.png"
        };
    };
    
    var myLwfElement = document.querySelector('.lwf');
    myLwfElement.setAttribute("data-lwf-image-map", JSON.stringify(setting.imageMap));
    
    var myLwfLoader = new LwfLoader();    
    myLwfLoader['playLWF'](myLwfElement);
```

上記のサンプルでは指定されたパスから画像を取得をするようになります。


### getImageMapper_関数を直接書き換える

画像パスを取得するための関数、getImageMapperを直接overrideして使う方法もあります。

* getImageMapper_をoverrideする(例)

```javascript
    var myLwfLoader = new LwfLoader();
    myLwfLoader.getImageMapper_ = function() {
        return function(pImageId) {
            return pImageId.replace(/REGEX/, 'IMG_PATH');
        };
    };
    
    var myLwfElement = document.querySelector('.lwf');
    myLwfLoader['playLWF'](myLwfElement);
```
