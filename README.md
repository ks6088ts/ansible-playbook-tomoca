# セットアップ

[ssh公開鍵認証設定まとめ](https://qiita.com/ir-yk/items/af8550fea92b5c5f7fca) を参考に、
公開鍵設定をします。

```bash
# 秘密鍵・公開鍵を作成
cd ~/.ssh
ssh-keygen -t rsa -f sakura_vps -N ''

# 秘密鍵をキーチェインに登録
ssh-add -K ~/.ssh/sakura_vps

# 公開鍵をリモートサーバに配置
ssh-copy-id ubuntu@ip_address

# Playbook 実行
ansible-playbook \
	-i inventories/production/hosts webservers.yml \
	--user ubuntu \
	--ask-become-pass \
	# --ask-pass \
```
