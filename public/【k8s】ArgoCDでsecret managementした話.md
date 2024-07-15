---
title: 【k8s】GitOps構築してsecret managementもした話 〜ArgoCD編〜
tags:
  - 'ArgoCD'
  - 'k8s'
  - 'CICD'
  - 'GitOps'
  - 'Security'
private: false
updated_at: ''
id: null
organization_url_name: null
slide: false
ignorePublish: false
---

こんにちは。
UniProjectのあかつきゆいとです。
今回は、GitOpsでシークレットごちゃごちゃする話です。

# 背景

うちのサークルでは、Mediawikiをサークル内Wikiにしています。
公式のDockerイメージだと、extention周りとかが納得いかないので、Dockerイメージも自作して、GitHubにも載せていますね。(GitHubは、一番下に載っけてます。)
そこで、k8sにわざわざ毎回デプロイするためにごちゃごちゃするのがめんどくさいわけですよ。
なので、GitHubにプッシュしたら、いい感じにK8sに乗っけてくれるやつを構築しました！！

# 前提

環境はこちらです。

- OS: Ubuntu24
- microk8s
- Proxomox VM

# 準備

今回準備するものは、

- ArgoCD(GitOps)
- SealedSecret

の2つです

## ArgoCD

### インストール

ArgoCDのマニフェストファイルを直で引っ張ってきましょうか。

```sh
# ネームスペースを作成
kubectl create namespace argocd
# マニフェストファイルを適用
kubectl apply -n argocd -f https://raw.githubusercontent.com/argoproj/argo-cd/stable/manifests/install.yaml
```

ここから、ダッシュボードにアクセスしていきましょう。
ただ、うちのサークルは、サークルメンバーの家で動いているので、リバースプロキシを通しましたね。

普通の人は、こちらのコマンドでポートフォワードを...

```sh
kubectl port-forward svc/argocd-server -n argocd 8080:443
```

これで、localhost:8080で接続できますね。

### ログインする

ユーザーIDはadmin、パスワードは以下のコマンドで、初期PWが取れます。

```sh
kubectl -n argocd get secret argocd-initial-admin-secret -o jsonpath="{.data.password}" | base64 -d
```

### GitHubとの連携

GitHubとは、左側の歯車から、Repogitory > Connect Repo Using HTTPSをクリック。
必要事項を入力します。

### デプロイ

リポジトリの一覧から、右の...をクリックし、Create Applicationをクリック。
プロジェクトネームはdefault、Sync policyはAUTOで構いません。
Pathには、manifestsファイルのあるディレクトリを指定します。

これで、デプロイが完了するはずですね。

# 最後に

今回はここまでです。
次回は、SealedSecretの設定の話を書きます...

GitHubはこちらです。

https://github.com/UniPro-tech/Mediwaiki
