# hibiyaScheduler

- まずサンプルを作る
- シンプルなUI

1. 講座一覧
2. 講座選択
3. 時間割作成（かぶらないように）
4. 時間割・申込票（1枚ずつ）印刷
5. （電子申請）
6. Googleカレンダー等に出力 

- Tokyo EducationのMicrosoftアカウントでログイン（できれば日比谷の生徒であることを確認したい）

-  同内容講座で複数開講の場合はそのうち1つが取れるように
- 規定コマ数に達しているか？チェック
→書き出して田嶋さんのアプリに取り込める形式に！

- 講座のお気に入り機能
- 色々な項目（教科，単元）から講座を検索できる
- 重なっている講座を選べるようにする．
	- どんな選び方のパターンがあるのか比較できる
- ノーコードでつくれるん？
- 共通テスト朝テストのように重複が許容される講座について，「この回だけ休む」を実装
- 自分で各講座にメモを追加できる欄をつくる
- 後から講座の変更があっても対応できるように．
- 情報保護をどこまで気をつける？
	- 講座名は出して良い？
	- 先生の名前は隠した方が良い？
	- 日比谷生だけがアクセスできるように出来る？
	- 講座内容を載せる必要はある？
---

### 参考

- Reactで時間割アプリを作ってみた - Qiita
- 時間割表を作成するサイトを作ってみた | Zenn
	- 時間割表を作成するサイトをバージョンアップ！
- 大学の時間割をカレンダーアプリで表示出来るようにするアプリを作った
- 時間割変更アプリの説明 - Qiita

- 筑波大学 KdBっぽいなにか
	- 筑波大シラバス「KdBもどき」を作ったその後どうなった？ - 11/13開催 関西オープンフォーラム2021 / Kansai Open Forum
	- 筑波大の授業DBがメンテ、困った新入生が代替ツールを“爆速開発”　その背景を本人に聞いた（1/2 ページ） - ITmedia NEWS

## Build Setup

```bash
# install dependencies
$ yarn install

# serve with hot reload at localhost:3000
$ yarn dev

# build for production and launch server
$ yarn build
$ yarn start

# generate static project
$ yarn generate
```

For detailed explanation on how things work, check out the [documentation](https://nuxtjs.org).

## Special Directories

You can create the following extra directories, some of which have special behaviors. Only `pages` is required; you can delete them if you don't want to use their functionality.

### `assets`

The assets directory contains your uncompiled assets such as Stylus or Sass files, images, or fonts.

More information about the usage of this directory in [the documentation](https://nuxtjs.org/docs/2.x/directory-structure/assets).

### `components`

The components directory contains your Vue.js components. Components make up the different parts of your page and can be reused and imported into your pages, layouts and even other components.

More information about the usage of this directory in [the documentation](https://nuxtjs.org/docs/2.x/directory-structure/components).

### `layouts`

Layouts are a great help when you want to change the look and feel of your Nuxt app, whether you want to include a sidebar or have distinct layouts for mobile and desktop.

More information about the usage of this directory in [the documentation](https://nuxtjs.org/docs/2.x/directory-structure/layouts).


### `pages`

This directory contains your application views and routes. Nuxt will read all the `*.vue` files inside this directory and setup Vue Router automatically.

More information about the usage of this directory in [the documentation](https://nuxtjs.org/docs/2.x/get-started/routing).

### `plugins`

The plugins directory contains JavaScript plugins that you want to run before instantiating the root Vue.js Application. This is the place to add Vue plugins and to inject functions or constants. Every time you need to use `Vue.use()`, you should create a file in `plugins/` and add its path to plugins in `nuxt.config.js`.

More information about the usage of this directory in [the documentation](https://nuxtjs.org/docs/2.x/directory-structure/plugins).

### `static`

This directory contains your static files. Each file inside this directory is mapped to `/`.

Example: `/static/robots.txt` is mapped as `/robots.txt`.

More information about the usage of this directory in [the documentation](https://nuxtjs.org/docs/2.x/directory-structure/static).

### `store`

This directory contains your Vuex store files. Creating a file in this directory automatically activates Vuex.

More information about the usage of this directory in [the documentation](https://nuxtjs.org/docs/2.x/directory-structure/store).
