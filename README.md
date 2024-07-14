# Cpolar K8S 部署

[Cpolar](https://i.cpolar.com/m/4eW6) 是一个内网穿透服务商，无限免费试用，绑定自己域名要付费。可用于将没有公网 IP 的服务器上的网站提供给公网用户，并基于香港服务器提供免备案访问。

## 用法

整个仓库下载到本地为 `./cpolar` 文件夹后，如下安装到 `cpolar` 命名空间里。

注意替换 `<YOUR_TOKEN>` 为你实际的 token，获取方法详见 Cpolar 官网。

```sh
helm upgrade --install cpolar ./cpolar -n cpolar --create-namespace --set cpolarToken=<YOUR_TOKEN>
```

如果要启用 Ingress，如下设置证书，可以在 [OHTTPS](https://www.ohttps.com?invitationCode=g6vy5rwdm5m82937) 上申请免费的泛域名证书。

证书下载到 `~/fullchain.cer` 和 `~/cert.key` 后，如下添加到 `cpolar` 命名空间里。

```sh
kubectl create secret tls tls-secret --cert='~/fullchain.cer' --key='~/cert.key' -n cpolar
```
