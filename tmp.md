SharePointの列の書式設定で他の列の値や任意の文字列を表示する方法についてご説明します。

SharePointでは、JSON形式の書式設定を使って列の表示をカスタマイズできます。他の列の値や任意の文字列を表示するには、主に以下の方法があります：

## 1. 他の列の値を表示する方法

JSON書式設定で`$` 記号を使って他の列を参照します：

```json
{
  "$schema": "https://developer.microsoft.com/json-schemas/sp/v2/column-formatting.schema.json",
  "elmType": "div",
  "txtContent": "=[$OtherColumnName]"
}
```

ここで `OtherColumnName` は参照したい他の列の内部名です。

## 2. 任意の文字列と他の列の値を組み合わせる方法

文字列と列の値を組み合わせて表示することもできます：

```json
{
  "$schema": "https://developer.microsoft.com/json-schemas/sp/v2/column-formatting.schema.json",
  "elmType": "div",
  "txtContent": "='固定テキスト: ' + [$OtherColumnName]"
}
```

## 3. 条件に基づいて異なる値を表示する方法

`operator` と `?` を使って条件分岐を実装できます：

```json
{
  "$schema": "https://developer.microsoft.com/json-schemas/sp/v2/column-formatting.schema.json",
  "elmType": "div",
  "txtContent": "=if([$Status] == '完了', '完了しました', '進行中: ' + [$Progress] + '%')"
}
```

## 実装手順

1. 書式設定したい列の設定を開きます
2. 「列の書式設定」を選択
3. 「詳細モード」をクリックしてJSONエディタを開く
4. 上記のJSONサンプルを適宜修正して貼り付ける

これらの方法を組み合わせることで、かなり複雑な表示をカスタマイズすることができます。
