[<< BackToTop](README.md)

# Concept Of Classes

## シーンの概念・概要。シーン管理について

画面の実処理を記載したクラスをSceneと呼びます。  
基本的に、一画面につき一つのSceneを作成します。

example : [aoba-examples/src/scenes/](https://github.com/drecom/aoba-examples/tree/master/src/scenes)

作成したSceneはSceneManagerクラスで管理します。

## シーン構築時の主要クラスについて
|クラス            |詳細                                              |
|---              |---                                               |
|[Scene.js](https://github.com/drecom/aoba.js/blob/master/src/core/Scene.js)         |アプリケーション側でSceneクラスを作る祭に継承するクラス  |
|[SceneManager.js](https://github.com/drecom/aoba.js/blob/master/src/core/SceneManager.js)  |Sceneの管理や切り替えを行うためのクラス                |
|[LoadingScene.js](https://github.com/drecom/aoba.js/blob/master/src/core/LoadingScene.js)  |ロード中画面クラス。必ずSceneManagerに追加される       |
|[Game.js](https://github.com/drecom/aoba.js/blob/master/src/core/Game.js)          |画面サイズの設定や、Sceneの実行などを行うクラス         |
|*[Container.js](https://github.com/drecom/aoba.js/blob/master/src/pixi/core/display/Container.js)    |オブジェクトのコレクションクラス。aoba.jsでは、位置や大きさの変更など、<br>コンテナを画面上の一つのオブジェクトとして扱うための機能を追加している    |
|*[Sprite.js](https://github.com/drecom/aoba.js/blob/master/src/pixi/core/sprites/Sprite.js)       |テクスチャを扱うオブジェクトクラス。aoba.jsでは、コンテナクラスと<br>同様の機能を追加している|
|*[Text.js](https://github.com/drecom/aoba.js/blob/master/src/pixi/core/text/Text.js)         |テキストを表示するクラス。aoba.jsでは、タイプライターのように<br>テキストを一文字ずつ表示する機能を追加している        |
*pixi.jsの同名クラスを継承しているクラス

## ルーティングについて
アプリケーション側でpage.js（ルーティングライブラリ）を使用して実装します。  
ルーティングを設定する流れは以下の通りです。
   
1. パスとコールバック関数を定義する  
example : [aoba-examples/src/routers](https://github.com/drecom/aoba-examples/tree/master/src/routers)

2. page.jsを使ってパスとコールバック関数を紐付ける  
example : [aoba-examples/src/app.js](https://github.com/drecom/aoba-examples/blob/master/src/app.js)  

## production/develop 用の切り替え

+ production: minifyしたものを読み込むなど、リリースのことを考えた形となっている
+ develop: 開発用で、FPSを表示するなどデバッグしやすい形となっている

production/developの切り替えは、ビルド実行時に  
環境変数「NODE_ENV」を指定することで行います。

上記の設定はpackage.jsonに記載しています。

    "build": "NODE_ENV=development webpack",
    "build:min": "NODE_ENV=production webpack",
