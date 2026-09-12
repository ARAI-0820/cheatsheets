# パッチ適用状況の確認 (CVEの特定)
wmic qfe get Caption,Description,InstallDate,HotFixID,InstalledBy,OSName,ProductType,Revision,Status  # Windows Update履歴

# 実行中のサービス・不適切な権限の確認
sc query                     # サービスのリスト取得
sc qc [ServiceName]          # 特定のサービスの設定確認（実行パスの確認）

# ファイルシステムの権限確認
icacls [FilePath]            # 特定のファイルやディレクトリのACL（アクセス制御リスト）確認

# ユーザー権限（Privileges）の確認
whoami /priv                # 特権（SeImpersonatePrivilege等）の有無を確認


脆弱性スキャン・自動化ツール

    WinPEAS: Windows環境の構成ミス、パス、レジストリ、権限を自動でスキャンし、昇格の可能性が高い箇所を提示する。
    PrivescCheck: PowerShellベースのスクリプト。権限昇格の可能性のある設定（不適切なサービス、パス、レジストリ）を調査。
    Mimikatz: メモリからパスワード、ハッシュ、チケット（Kerberos）を抽出する。
