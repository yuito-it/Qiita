---
title: 【暗号化】Keybaseのススメ # 記事のタイトル
tags:
  - "セキュリティ"
  - "E2EE"
  - "Keybase"
  - "暗号化"
  - "PGP" # タグ（ブロックスタイルで複数タグを追加できます）
private: true # true: 限定共有記事 / false: 公開記事
updated_at: "" # 記事を投稿した際に自動的に記事の更新日時に変わります
id: null # 記事を投稿した際に自動的に記事のUUIDに変わります
organization_url_name: null # 関連付けるOrganizationのURL名
slide: false # true: スライドモードON / false: スライドモードOFF
ignorePublish: false # true: `publish`コマンドにおいて無視されます（Qiitaに投稿されません） / false: `publish`コマンドで処理されます（Qiitaに投稿されます）
---

というわけでこんにちは。
S高等学校4期生のあかつきゆいとです。

最近、暗号同好会なるものを学園内に設立いたしまして、暗号同好会なら暗号同好会らしく、ガチガチに暗号化されたSNSを拠点にしようと考えました。
というわけで、今回は、同好会メンバー向けのものです。
ただ、他の人が見ても面白いようには作ったつもりです。

どうぞよろしくお願いします。

## まずN/S高生、N中等部生の方へ

#暗号同好会_仮 というチャンネルで活動しておりますので、どうぞ参加お待ちしております！！

活動内容としては、

- 古典暗号を研究する
- 近年のデジタルデータに対する暗号について研究する

などなど、ですね。
今回は2つ目の活動内容に当たるかと思います。

面白かったら覗いてくだけでも来てください！！

## keybase

暗号化されたものといえば、TelegramやSignalが思い浮かぶ人も多いでしょう。

**でもそれじゃあつまらん！！**

だって暗号化の原理理解せずに使えちゃうじゃないですか()

**[Keybase](https://keybase.io/)** はE2EE(End To End Encrypt)で暗号化された鍵管理やチャット、ファイル共有等ができるソフトウェアです。

※E2EEに関しては、こちらの記事をご覧ください。

https://qiita.com/yuito_it_/items/d7b88056b8ba53b25501

## 使い方

暗号化には公開鍵と秘密鍵が必要なんですよ。わからんという人は、E2EEに関する記事を読んでくだされ。

で、それを一元管理できるのがKeybaseです。

鍵はどのようにして手に入れるかですが、

1. 自分で鍵を生成する(PC必須)
2. Keybaseに自動生成させる(スマホでもおk)

の2つ方法があります。

めんどくさかったら、2を選べばいいでしょう。暗号化の仕組みをガッツリ勉強したくば、1をやったほうがいいとは思いますが。

### Keybaseとかのインストール

どちらにせよ、インストールしなければなりません。
以下の2つのソフトウェアをインストールしましょう。

スマホの人はKeybaseだけで良きです。

- [Keybase](https://keybase.io)
- [GPG Suite(Mac)](https://gpgtools.org/)
- [GPG4win (Windows)](https://www.gpg4win.org/)

Linuxの人は自分でわかると思うので割愛します。自分でなんとかしてくれ。

### Keybaseアカウントの作成

[keybase](https://keybase.io)で、アカウントを作成してください。
それから、アプリでログインした方がいいと思います。

ちなみに、アカウント名は後から変更できず、削除しても、そのアカウント名は誰も使えない状態になったままなので、 **よく考えて** 作ってください。

### 自分で鍵を生成する

自分で鍵を生成する。
これならば、自分の思い通り鍵が生成でき、暗号化をよりガッチガチにできます。

鍵生成に関しては、こちら下の記事を読んでもらいましょう。

https://qiita.com/shun-shobon/items/a944416bebb6207016fb#gnupg%E3%81%AE%E3%83%87%E3%83%BC%E3%82%BF%E3%81%AE%E4%BF%9D%E5%AD%98%E5%A0%B4%E6%89%80

では、お次に鍵の取り込みです。

お好きなターミナルで、
```sh
$ gpg --list-secret-keys --keyid-format=long
/Users/xxxxx/.gnupg/pubring.kbx
--------------------------------
sec   rsa4096/933DD24688B8DBC4 2024-02-13 [SC] [有効期限: 2025-02-12]
      8225CF065FE1F94B9FC8FAE9933DD24688B8DBC4
uid                 [  究極  ] Yuito Akatsuki <yuito_it@outlook.jp>
uid                 [  究極  ] Yuito Akatsuki <yuito.akatsuki.jp@gmail.com>
uid                 [  究極  ] Yuito Akatsuki <yuito@mail.uniproject-tech.net>
ssb   rsa4096/7A093BE16833643D 2024-02-13 [E] [有効期限: 2025-02-12]
ssb   rsa4096/40F7D801D80D037D 2024-02-15 [SEAR] [有効期限: 2025-02-14]

sec   rsa4096/3E65A223840C21B2 2024-02-11 [SCA] [有効期限: 2025-02-11]
      32A37D269F839146A2864C993E65A223840C21B2
uid                 [  究極  ] Tani Yutaka <yuito_24s1101644@nnn.ed.jp>
uid                 [  究極  ] Tani Yutaka <yutaka.tani.090304@outlook.jp>
uid                 [  究極  ] Tani Yutaka <cube.root.infinity@gmail.com>
ssb   rsa4096/4F60063AE9F62892 2024-02-11 [E] [有効期限: 2025-02-11]

$ gpg --armor --export 933DD24688B8DBC4(お好きな鍵のID)
-----BEGIN PGP PUBLIC KEY BLOCK-----

mQINBGXLOYMBEADFQhzKwnZxbjrnD9oCDoDfg8w/buoe9Z8WnvWeMgG6IEuhRgcS
==中略==
MBXJuoViiwKl6C65X1Xty0o4MsPyTEZ/Cw8TRnLy1Mm9258TpOMNZkpAd1Y0/uLb
oq4zIA2jINCeYuDjJ6bmSkmQYip2sA==
=ibRd
-----END PGP PUBLIC KEY BLOCK-----
```

これで公開鍵が取れましたね。
コピーして、Keybaseのユーザーページから、追加しましょう。

![userpage.png](https://qiita-image-store.s3.ap-northeast-1.amazonaws.com/0/3342262/85f53f11-7d95-26b0-2514-f3ddb46df059.png)

こんなページの鍵マークのところがおそらく空欄でしょう。
そこで追加を押して、公開鍵の入力欄が出てくるので、さっきコピーしたものを貼り付けましょう。

終わったら、次は、さっき追加した鍵のeditを押して、Host an encrypted copy of my private keyをクリックし、
お好きなターミナルで、

```sh
$ bash
$ gpg --export-secret-keys お好きな鍵のID
-----BEGIN PGP PRIVATE KEY BLOCK-----
(ここの文字列は絶対に他人に共有してはならない！！)
-----END PGP PRIVATE KEY BLOCK-----
```

そして、この、BEGINからENDまでを、keybaseの入力欄に入力。鍵のパスフレーズも入力する。

以上！！

### Keybaseくんに鍵を生成してもらう

さっきの鍵を追加するところで生成してもらうオプションがあったと思うからそれでやる。

以上！！

## 使ってみよう

### Chat

誰かとチャットしてみよう！
アプリのどこかにチャット欄があると思うので、yuito_it_にでもメッセージ送ってみてください。

「Qiita見ました！」

とか送ると、上機嫌で帰ってきます。

### Teams

チーム機能は、yuito_it_宛に、Slack名を送るとinvite送るので要問い合わせです。

## まとめ

基本的な使い方は以上です。

アカウント作成をするのは完全削除できないので忍びないと思い、やりませんでした。故に、新規作成とかのところが結構雑ですが、許してください。hi.

Let's enjoy Keybase Life!!!
