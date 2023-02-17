# my-documents

github上でMermaidとやらのルールに従ってテキストを書くと図ができるということで、やってみた

LN pay InvoiceではLN送金と書いてざっくり省略してたのをもう少し詳しく図解した。

シークレットは受取人が作るから、支払人ノードまでシークレットが届かなくてもZapノートが作れちゃうんだよね。だからZapノートは支払証明にならないっていってるんだよきっと。

LNURLもLightning Addressも結局はLNURLサーバにgetリクエストする。</br>
LAの方はドメイン名とユーザ名で分解して以下のようにURLに置き換えているだけ。lud16を見よ。</br>
https://ドメイン名/.well-known/lnurlp/ユーザ名

LNURLはbech32でエンコーディングされている。</br>
lud17でエンコードなしにして、LNURLを機能別にスキームを使い分けようとしている。</br>
LNURL-pay なら lnurlp:// として 通信するときはlnurlpをhttpsに置き換える。
