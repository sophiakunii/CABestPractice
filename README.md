# 条件付きアクセスのベストプラクティスポリシー
マイクロソフトの Azure AD Webinar の中で提供している条件付きアクセスのベストプラクティスポリシーについて
設定をJSONファイルにエクスポートしたものです。

### ベストプラクティスポリシーを紹介している Web ページ
詳説！Azure AD 条件付きアクセス - 設計のやり方編 Azure AD Conditional Access deep dive - Design methodology

https://github.com/yusukekodama/PMActivities/blob/master/Webinar/Schedule.md

**注** ここにあるJSONファイルはベストプラクティスポリシーと厳密には同一ではなく、一部設定を割愛しています。
#### Break Glass アカウント
Break Glass アカウントの名前は組織によってまちまちです。そのため、本ファイルにはBreak Glass アカウントの設定は含めませんでした。
#### P002~P003 ポリシー
P001と同様のポリシーであったため除外しました。
#### N002 ポリシー
マイクロソフト以外のクラウドサービスは組織によって使うものが異なります。そのため、Non-MSアプリのポリシーは N001 だけ作成し、残りは除外しました。

## ファイル一覧
#### P001.JSON
PIMを推奨するが利用できない場合には少なくとも以下のロールに対してMFAを強制することを強く推奨。PIMと同時に利用することも問題ない。対象ロールにはグローバル管理者を設定。

#### L001.JSON
全員がブロック対象。もし必要であれば、最低限のアカウントを除外。

#### L002.JSON
ExO側でもブロックすることを推奨。基本的にActiveSyncはブロック。利用可能な条件に大きな制限あり（例：場所ベースは利用不可）。

#### R001.JSON
一般ユーザーに必ず適用されるポリシー。この例は、社外からのアクセスには、準拠デバイス、ドメイン参加デバイス、MFA、のどれかを満たす必要がある。MFAを要求する、という制御をするとエンドユーザーにMFA登録を求める画面が出るため注意。一般ユーザーグループにはGeneralという名前のグループを指定。

#### M001.JSON
Intune MDMポリシーに準拠したのみアクセスを許可。この例はWindowsを除き、WindowsはM003で保護。MS以外のネイティブアプリは対応していない場合には除外して別ポリシーで保護。

#### M002.JSON
MAM対応アプリを必要とする。MS以外のネイティブアプリを必要とするものは除外。OSネイティブブラウザを許可するアプリも除外。

#### M003.JSON
社外からのPCアクセスは要HAADJ。HAADJ前は要VPN。

#### N001.JSON
Concur 向けポリシー。社外からは要MFA。この例だと、実際にはR001でこの要件を満たしているため不要。Concur を使わない組織では必要に応じて自組織利用のクラウドサービスに変更して利用。

#### G001.JSON
ゲストへはMFAを求める。ゲストのMFAサポート（リセット等）体制を構築する必要あり。


