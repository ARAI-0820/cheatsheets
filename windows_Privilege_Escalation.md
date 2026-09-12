# Windows Privilege Escalation & Vulnerability Assessment Cheat Sheet

Windows環境におけるセキュリティ監査、設定確認、および権限昇格（Privilege Escalation）の調査で使用する基本的なコマンドとツールのまとめです。

## 目次
- [1. パッチ適用状況の確認 (CVEの特定)](#1-パッチ適用状況の確認-cveの特定)
- [2. 実行中のサービス・不適切な権限の確認](#2-実行中のサービス不適切な権限の確認)
- [3. ファイルシステムの権限確認](#3-ファイルシステムの権限確認)
- [4. ユーザー権限 (Privileges) の確認](#4-ユーザー権限-privileges-の確認)
- [5. 脆弱性スキャン・自動化ツール](#5-脆弱性スキャン自動化ツール)

---

## 1. パッチ適用状況の確認 (CVEの特定)
システムに適用されている更新プログラムやホットフィックスを確認し、既知の脆弱性（CVE）が存在するかを調査します。

```powershell
wmic qfe get Caption,Description,InstallDate,HotFixID,InstalledBy,OSName,ProductType,Revision,Status

2. 実行中のサービス・不適切な権限の確認

権限昇格の標的になりやすい、脆弱な権限が設定されたサービスや実行パスを調査します。

    サービスの一覧取得
    DOS

    sc query

    特定サービスの詳細・実行パスの確認
    DOS

    sc qc [ServiceName]

3. ファイルシステムの権限確認

特定のファイルやディレクトリに対するアクセス制御リスト（ACL）を確認し、不適切な書き込み権限などがないかを調査します。
DOS

icacls [FilePath]

4. ユーザー権限 (Privileges) の確認

現在のアカウントに付与されている特権（SeImpersonatePrivilege など）を確認し、昇格に利用できる権限があるかを特定します。
DOS

whoami /priv

5. 脆弱性スキャン・自動化ツール

手動での調査を効率化・自動化するためによく使用される代表的なツールです。

    WinPEAS

        Windows環境の構成ミス、パス、レジストリ、権限などを自動でスキャンし、昇格の可能性が高い箇所を色分けして提示します。

    PrivescCheck

        PowerShellベースのスクリプト。権限昇格の可能性のある設定（不適切なサービス、パス、レジストリなど）を網羅的に調査します。

    Mimikatz

        メモリからパスワード、ハッシュ、Kerberosチケットなどを抽出し、資格情報の収集を行います。
