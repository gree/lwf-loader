lwf-loader.js リソースガイドライン
===============================

### lwf-loader固有ルール

デフォルトの状態でのリソースは以下の状態のように配置することを想定しています。

* 画像の配置
    * リンケージ名を、`lwf_<lwf id>_foo.jpg` のように設定する
    * `lwf/<lwf id>/` 以下に、 `lwf/<lwf id>/foo.jpg`のように配置

* LWF固有の画像 (texture atlas)
    * リンケージ名を、`lwf_<lwf id>_atlas.jpg` のように設定する
    * `lwf/<lwf id>` 以下に、lwf/<lwf id>/atlas.jpgのように配置

* LWFの外で置き換えを想定している画像
    * リンケージ名を、`param_item_large_1.jpg` のように設定する
    * `param/` 以下に、`param/***.jpg` のように配置
    * 例えば上記のリンケージ名のケースなら、`param/item/large/1.jpg` などとする
    * 連番で指定するようなものは、0から始まるようにする

* LWF外の画像
    * リンケージ名を、misc_item_1.jpgのように設定する
    * `/img/misc/item/1.jpg` を参照したい場合は、SWFでは `misc/item/1.jpg` に配置する


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
