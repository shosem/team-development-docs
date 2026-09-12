## Github関連

リポジトリ：[https://github.com/shosem/planest](https://github.com/shosem/planest)

### ブランチルール

main：本番用。直接pushしない
develop：開発統合用。ここからブランチを切り出し、マージする

### ブランチ命名規則

すべて小文字英数字。以下形式を使用

```ruby
# 形式
[アクション]/[イシュー番号]-[アクション内容]

# 例
feature/12-add-users
fix/15-login-error
```

### アクション一覧
| **Prefix** | **意味** |
| --- | --- |
| `feature` | 新機能の追加 |
| `fix` | バグ修正 |
| `refactor` | リファクタリング |
| `docs` | ドキュメント修正 |
| `chore` | 環境設定・Gemfileなど |
| `test` | テストの追加・修正 |
| `style` | スタイル関連 |

### コミットルール

| **Prefix** | **意味** |
| --- | --- |
| add | ちょっとしたファイル・コードの追加 ex)画像ファイル |
| change | ちょっとしたファイル・コードの変更 ex)画像差し替え |
| feat | ユーザーが利用する機能の追加。`add/change`を内包しても良い。 |
| style | 機能部分を変更しない、コードの見た目の変化 ex)CSS |
| refactor | リファクタリング |
| fix | バグ修正 |
| remove | ファイルなどの削除 |
| test | テスト関連 |
| chore | 環境設定、ビルド、補助ツール、ライブラリ関連 |

```ruby
# 例
feat: Userモデルを追加
fix: ログインエラーを修正
```

### PRルール

- 最低ひとりのレビュー
- mainへの直push禁止。developへ
