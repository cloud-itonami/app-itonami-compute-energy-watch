# データ源の利用条件 (JUN-523)

確認日: 2026-10-28。公式ページ（または検索で得た公式説明）を読んだ結果で、**法的助言ではない**。
条件は変わりうるため、`verified` でも取得時に当該データセットのページで個別条件を再確認する。

## 区分

| 区分 | 意味 | bot の扱い |
|---|---|---|
| `verified` | 公開条件が、出典付きの取得・要約・再掲を許すと読める | 承認を得た上で取得してよい |
| `restricted` | 一部のみ許される、または別規約・別手続きが必要 | 許される部分だけ。範囲外は取得しない |
| `excluded` | 有料、または許諾がなければ再利用できない | 取得しない |
| `unverified` | 条件を読めていない | 取得しない |

## 結果

| 源 | 区分 | 根拠 | 条件・注意 |
|---|---|---|---|
| EIA (米エネルギー情報局) | `verified` | https://www.eia.gov/about/copyrights_reuse.php | データ・報告書は米国政府著作物で、通常は自由に利用・再配布できる。出典表示（EIA と公表日）が求められる。第三者の資料・写真・ロゴは対象外 |
| Ember | `verified` | https://ember-energy.org/about/licensing/ | サイトの全コンテンツが CC BY 4.0。出典表示が必要。名称は商標。個別データのページも取得時に確認する |
| Epoch AI | `verified` | https://epoch.ai/data | データセット（GPU クラスタ、ML ハードウェア等）は CC BY。出典・著者表示が必要。外部リンク先の資料は別扱い。取得時に各データセットのページで再確認 |
| IEA | `restricted` | https://www.iea.org/terms | 無料の本文・報告書・単独の図は CC BY 4.0。**単独のデータセット、data explorer、データベース、WEO のデータ annex は CC BY 4.0 の対象外**で別規約。ロゴ・画像も対象外。自動アクセスは拒否されうる。AI エージェントには別の AI Agent Terms がある |
| ITU | `restricted` | https://www.itu.int/en/Pages/copyright.aspx | 一般規定のみ。統計・出版物の再利用は許諾の申請が必要（jur@itu.int）。報道資料は ITU を出典に明記すれば可 |
| TeleGeography | `excluded` (データ) / `restricted` (地図) | https://www2.telegeography.com/cite-telegeography-map | 公開地図は CC BY-SA 4.0。背後のデータは有料ライセンス。地図の再利用は SA の条件を満たす場合のみ |
| WSTS | `excluded` | https://www.wsts.org/ | 全出版物が WSTS の著作物で、許諾なしの複製は禁止。無料の Historical Billings Report にも再利用の明示許諾はない。月次レポートは会員限定 |
| ENTSO-E Transparency Platform | `unverified` | (現行の利用規約ページを読めなかった) | 過去の資料では、再利用の可否が項目ごとに異なり、制限が付いたことがある。現行条件を確認するまで取得しない |
| TOP500 | `unverified` | https://www.top500.org/ | 利用条件の記載を確認できなかった（著作権表記のみ）。取得しない。条件ページ（Imprint 等）の確認が次の手順 |
| SIA, SEMI | `unverified` | — | 今回は確認していない。取得しない |

## 帰結

- 今すぐ取得してよい候補は **EIA、Ember、Epoch AI** のみ（いずれも承認を得た上で）。
- 電力は EIA と Ember、GPU/計算は Epoch AI でカバーできる。**CPU、network、storage は、現時点で `verified` な源がない。** これらの軸は `UNKNOWN` のままにする。
- IEA は、無料報告書の CC BY 4.0 部分のみ。データセットの自動取得はしない。
- 半導体（CPU・storage の出荷・製造）と network の公開データは、許諾を取るか、別の源（各社決算など、出典ごとの確認）を探す必要がある。これは JUN-524 の指標表で扱う。
- `unverified` の源の確認を進める場合は、各源の運営者の利用条件ページを読む。判断が割れる場合は owner 判断として記録する。
