# 条件付きアクセスのベストプラクティスポリシー
マイクロソフトの Azure AD Webinar の中で提供している、条件付きアクセスのベストプラクティスポリシーについて
設定をJSONファイルにエクスポートしたものです。

### ベストプラクティスポリシーを紹介している Web ページ
詳説！Azure AD 条件付きアクセス - 設計のやり方編 Azure AD Conditional Access deep dive - Design methodology

https://github.com/yusukekodama/PMActivities/blob/master/Webinar/Schedule.md

ここにあるJSONファイルはベストプラクティスポリシーと厳密には同一ではなく、一部設定を割愛しています。

#### Break Glass アカウント
Break Glass アカウントの名前は組織によってまちまちです。そのため、本ファイルにはBreak Glass アカウントの設定は含めませんでした。
#### N00x ポリシー
マイクロソフト以外のクラウドサービスは組織によって使うものが異なります。そのため、Non-MSアプリのポリシーは除外しました。

## ファイル一覧
#### P001.JSON
P001_Require MFA for highest privileged admins

#### L001.JSON
L001_Block legacy authentication

#### L002.JSON
L002_Block ActiveSync

#### R001.JSON
R001_Safety net policy Require MFA or Managed device from off-net

#### M001.JSON
M001_Require Compliant iOS/Android Device

#### M002.JSON
M002_Require Approved Clients on iOS/Android for MS Apps

#### M003.JSON
M003_Require DJ Win10 from non-Trusted location

#### N001.JSON
N001_Require MFA for Concur from non-trusted locations

#### G001.JSON
G001_Require MFA for Guests
