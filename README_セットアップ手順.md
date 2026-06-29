# 自分専用ポッドキャスト（全8話）セットアップ手順

## 同梱ファイル
- `ep0.mp3` … EP0 イントロ＋合格論文の型（約1分25秒）
- `ep1.mp3` … EP1 基礎知識① 大綱・教育ビジョン（約2分55秒）
- `ep2.mp3` … EP2 基礎知識② 教師像・働き方改革・主任教諭制度（約1分51秒）
- `ep3.mp3` … EP3 基礎知識③ 論文の評価・データ・施策（約3分44秒）
- `ep4.mp3` … EP4 採用版 前半 第1〜6編（約10分21秒）
- `ep5.mp3` … EP5 採用版 後半 第7〜12編（約9分08秒）
- `ep6.mp3` … EP6 主任版 前半 第13〜17編（約8分16秒）
- `ep7.mp3` … EP7 主任版 後半 第18〜22編（約9分36秒）
- `cover.jpg` … カバー画像（3000×3000）
- `feed.xml` … RSSフィード（全8話・serial／itunes:block で非公開）

声は先生（低め）＝出題・解説、受験生（高め）＝解答・確認。基礎知識編は問いのあとに考える間を入れています。

---

## 手順（GitHub Pages・無料）

### 1. Publicリポジトリを作る
無料アカウントのGitHub PagesはPublicリポジトリ限定。例：kikinagashi
ベースURL = https://<ユーザー名>.github.io/kikinagashi/

### 2. ファイルをリポジトリ直下にアップロード
ep0.mp3〜ep7.mp3・cover.jpg・feed.xml を直下に置く（サブフォルダ不可）。
各mp3は最大7MB台で、1ファイル100MB上限の範囲内。

### 3. feed.xml のURLを置換
feed.xml 内の https://USERNAME.github.io/REPO を自分のベースURLに一括置換
（link・itunes:image・各enclosure の計10か所）。macOSなら:

    sed -i '' 's#https://USERNAME.github.io/REPO#https://taro.github.io/kikinagashi#g' feed.xml

### 4. Pagesを有効化
Settings → Pages → Source「Deploy from a branch」→ Branch「main」/「/ (root)」→ Save。初回反映に数分。

### 5. 配信確認

    curl -I https://taro.github.io/kikinagashi/feed.xml
    curl -I https://taro.github.io/kikinagashi/ep0.mp3   # content-type: audio/mpeg

### 6. Apple Podcastsに登録
- Mac：Podcasts →「ファイル」→「URLで番組を追加」→ ベースURL+/feed.xml
- iPhone/iPad：「ライブラリ」→「…」→「URLで番組を追加」→ 同じURL

serial 指定なので EP0 から順に並びます。同じApple IDで全端末同期。

---

## 注意
- mp3を差し替えたら、feed.xml の該当 length=（バイト数）も更新（stat -f%z ep4.mp3）。
- GitHub PagesはURLを知れば誰でも開ける“実質プライベート”。厳密な制御が必要なら有料の配信ホストへ。
- 声をもっと自然にしたくなったら、台本（都立教員論文_聞き流し台本_完全版.md）をVOICEVOX等で読み上げ直し、同じファイル名で差し替えればfeedはそのまま使えます。
