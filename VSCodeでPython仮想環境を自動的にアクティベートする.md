
# VS Codeのプロジェクト固有の設定

VS Codeで特定のプロジェクトにおいてPythonの仮想環境を自動的にアクティベートするには、プロジェクトのルートディレクトリに `.vscode` ディレクトリ内の `settings.json` ファイルを設定します。

## 設定ファイルの作成または編集

1. **プロジェクトディレクトリに `.vscode` ディレクトリを作成**
   もしまだ `.vscode` ディレクトリがない場合は、プロジェクトのルートディレクトリで以下のコマンドを実行して作成します。
   ```bash
   mkdir .vscode
   ```

2. **settings.json ファイルを作成または開く**
   `.vscode` ディレクトリ内に settings.json ファイルを作成または開きます。
   ```bash
   notepad .vscode/settings.json  # Windowsの場合
   nano .vscode/settings.json     # macOS/Linuxの場合
   ```

3. **仮想環境の自動アクティベーションの設定を追加**
   settings.json ファイルに以下の内容を追加または編集します。
   ```json
   {
       "terminal.integrated.profiles.windows": {
           "PowerShell": {
               "path": "powershell.exe",
               "args": [
                   "-NoExit",
                   "-Command",
                   "& "C:\YourProjectPath\YourProjectName\venv\Scripts\Activate.ps1""
               ]
           }
       },
       "terminal.integrated.defaultProfile.windows": "PowerShell"
   }
   ```
   ここで、`C:\YourProjectPath\YourProjectName\venv\Scripts\Activate.ps1` は仮想環境の Activate.ps1 スクリプトへの実際のパスに置き換えてください。

4. **設定を保存**
   変更を加えたら、settings.json ファイルを保存します。

5. **仮想環境の自動アクティベーションのテスト**
   VS Codeでプロジェクトを開きます。
   VS Codeの内蔵ターミナルを開きます。Ctrl + ` (バッククォート) を使用するか、メニューから「表示」->「ターミナル」を選択します。
   ターミナルが開いたときに、指定した仮想環境が自動的にアクティベートされていることを確認します。

この設定は、特定のプロジェクトにのみ適用されます。`settings.json` ファイル内で指定されたパスや設定は、そのプロジェクトに固有です。
