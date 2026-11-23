# シーサー スケッチ
Hi3Dで作ったシーサー2体の3Dモデルを、好きな角度に回してスケッチできる単一HTML（美術のテスト・スケッチ題材用、Chromebook向け）。

- 公開: https://choppermoon1623-tech.github.io/shisa-sketch/ （デプロイ元 devppsshisa-sketch）
- 使い方: `index.html` を開く。左上で「シーサー1／シーサー2」を切りかえ。向きが決まったら「向きを固定」
- 1体だけ見せるとき: URLの末尾に `?m=1`（または `?m=2`）。切りかえボタンが消える
- 機能: 向きを固定／石こう（色なし）／マス目（4×4）／決まった向き（正面・ななめ・横・上から）／自動で回す／全画面。向きは体ごとに端末へ保存され、開き直しても同じ角度になる
- 元データ: Downloads の Hi3D_スタイリッシュな手作りセラミックシーサ…_20261123_234719.glb（1）／Hi3D_手作り陶磁器スタイル伝統民俗守護獣…_20261123_234533.glb（2）
- 作り方（_work で）:
  1. `npx @gltf-transform/cli optimize 元.glb opt_a.glb --compress meshopt --texture-compress webp --texture-size 2048 --simplify-ratio 0.12 --simplify-error 0.0007`（200万→24万ポリゴン、約2MB）
  2. esbuild で main.js → bundle.js（three は `01_アプリ/figure-viewer/_work/node_modules` を NODE_PATH で借りる）
  3. `python build.py opt_a.glb opt_b.glb ../index.html`
