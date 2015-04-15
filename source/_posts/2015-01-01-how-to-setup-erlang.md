title: "how to setup erlang"
date: 2015-01-01T01:32:21.196+0800
tags: [howto, erlang]
---


要開始玩 erlang 首先第一步就是要先安裝程式。
Basho 有一份詳細的[步驟](http://docs.basho.com/riak/latest/ops/building/installing/erlang/) ,可以先從這裡開始。
也可以從 https://www.erlang-solutions.com/downloads/download-erlang-otp 下載已經打包好的安裝包。
如果讀者用的是 Linux 平台，那可能套件庫中就已經有打包好的了，直接用套件管理員安裝就好。

在這裡我簡單介紹一下用 kerl 來安裝的步驟。使用 kerl 安裝的最大好處是可以在系統上同時存在多個 erlang 版本。
有時候新的 erlang 版本做了比較大的更新，而開發的程式還沒跟上，這時候就可以先用舊的版本來開發，同時安裝新的版本來玩玩新功能。
目前 kerl 應該是只能應用在 Linux/Mac OS/FreeBSD/Solaris 的環境下， windows+cygwin 我沒試過，有興趣的可以自己試試。

<!-- more -->

下載 kerl
==============

首先，先下載 kerl 這個指令碼

```sh
curl -O https://raw.github.com/spawngrid/kerl/master/kerl; chmod a+x kerl
```

執行 kerl
==========

接著在家目錄下建立一個 .kerlrc 的檔案，並在其中寫入以下內容。

```sh
KERL_CONFIGURE_OPTIONS="--disable-hipe --enable-smp-support --enable-threads --enable-kernel-poll  --enable-darwin-64bit"
```
在 FreeBSD/Solaris 下 erlang 並不支援 HIPE，所以這裡將他設成 `--disable-hipe`。如果在你的 OS 上有支援 HIPE 且你也想試試你可以把他改成 `--enable-hipe`。

再來執行 `./kerl update releases` 來取得目前可以使用的 erlang 版本列表。執行的結果大概如下：

```html
Getting the available releases from erlang.org...
The available releases are:
R10B-0 R10B-2 R10B-3 R10B-4 R10B-5 R10B-6 R10B-7 R10B-8 R10B-9 R11B-0 R11B-1 R11B-2 R11B-3 R11B-4 R11B-5 R12B-0 R12B-1 R12B-2 R12B-3 R12B-4 R12B-5 R13A R13B R13B01 R13B02 R13B03 R13B04 R14A R14B R14B01 R14B02 R14B03 R14B04 R15B R15B01 R15B02 R15B03 R16B R16B01 R16B02
```

在編譯想要使用的版本前我們需要確認編譯所需的套件是否都已經安裝，如果使用的是 Ubuntu 可以用下列指令

```sh
sudo apt-get install build-essential libncurses5-dev openssl libssl-dev fop xsltproc unixodbc-dev
```

如果是其他 Linux 版本，應該也有類似的套件庫，就請讀者自己搜尋一下。如果你需要使用 erlang 的一些支援 UI 的函式庫，則你要額外安裝

```bsh
sudo apt-get install libwxbase2.8 libwxgtk2.8-dev libqt4-opengl-dev
```

現在假設我們想要使用 R15B01 的版本，我們可以執行 `./kerl build R15B01 r15b01`。
第一個 "R15B01" 是我們要編譯的版本，第二個 "r15b01" 是我們給這個版本取的名字。
我們可以給同樣的版本取不同的名字，例如我想要作一個有支援 HIPE 而另一個沒有支援 HIPE 的 R15B01 。
我可以透過修改 .kerlrc 來設定不同的編譯選項，然後給他們分別命名，這樣我就可以隨時切換這兩個版本。

編譯過程中 kerl 會自動下載 erlang 的程式碼，編譯過程中如果出現錯誤螢幕上會提示訊息，你可以去看紀錄檔，了解大概是哪裡出了問題。
編譯完成後再接著執行 `./kerl install r15b01 ~/erlang/r15b01` 將編譯好的項目（r15b01）安裝到指定的目錄下。

最後在使用 erlang 前執行 `. ~/erlang/r15b01/activate` 來啟動要使用的版本即可。

kerl 指令
=========

*  build   - Build specified release or git repository
*  install - Install the specified release at the given location
*  deploy  - Deploy the specified installation to the given host and location
*  update  - Update the list of available releases from erlang.org
*  list    - List releases, builds and installations
*  delete  - Delete builds and installations
*  active  - Print the path of the active installation
*  status  - Print available builds and installations
*  prompt  - Print a string suitable for insertion in prompt
*  cleanup - Remove compilation artifacts (use after installation)


