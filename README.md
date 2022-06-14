## Dockerのアンインストール（既にインストールしたものがある場合）
１．インストールされているパッケージを特定する。
```
dpkg -l | grep -i docker
```

２．特定したパッケージを全て削除
```
sudo apt-get purge -y docker-engine docker docker.io docker-ce docker-ce-cli
sudo apt-get autoremove -y --purge docker-engine docker docker.io docker-ce
```

３．イメージファイル等を削除
```
sudo rm -rf /var/lib/docker /etc/docker
sudo rm /etc/apparmor.d/docker
sudo groupdel docker
sudo rm -rf /var/run/docker.sock
```

４．現行版（DockerCE）のアンインストール
```
sudo apt-get purge docker-ce
sudo apt autoremove
```

５．古いバージョンのDockerのアンインストール
```
sudo apt-get remove docker docker-engine docker.io containerd runc
```

## Dockerのインストール
参考URL：https://docs.docker.com/engine/install/ubuntu/

１．必要なものをインストール
```
 sudo apt-get update
 sudo apt-get install \
    ca-certificates \
    curl \
    gnupg \
    lsb-release
```

２．公式DockerのGPGキーを設定
```
sudo mkdir -p /etc/apt/keyrings
 curl -fsSL https://download.docker.com/linux/ubuntu/gpg | sudo gpg --dearmor -o /etc/apt/keyrings/docker.gpg
```

３．リポジトリセット
```
echo \
  "deb [arch=$(dpkg --print-architecture) signed-by=/etc/apt/keyrings/docker.gpg] https://download.docker.com/linux/ubuntu \
  $(lsb_release -cs) stable" | sudo tee /etc/apt/sources.list.d/docker.list > /dev/null
```

４．インストール
```
 sudo apt-get update
 sudo apt-get install docker-ce docker-ce-cli containerd.io docker-compose-plugin
```

## このGithubリポジトリをクローンする
※WSL2上から行うと思うので、コマンドで操作することになります。
１．Gitのインストール
```
sudo apt install git
```
２．Gitの初期設定を行う
```
git config --global user.name [任意のユーザ名]
git config --global user.email [任意のユーザ名]
```
３．リポジトリがあるか確認（念のため）
```
git remote 
```
４．リポジトリがあれば削除
```
git remote rm orgin
```
５．リポジトリを追加
```
git remote add 
```
