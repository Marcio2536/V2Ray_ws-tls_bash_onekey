### 準備工作
* 準備一個域名，並將A記錄添加好。
* [V2ray官方說明](https://www.v2ray.com/)，瞭解 TLS WebSocket 及 V2ray 相關信息
* 安裝好 wget

### 安裝/更新方式（h2 和 ws 版本已合併）
Vmess+websocket+TLS+Nginx+Website
```
wget -N —no-check-certificate -q -O install.sh “https://raw.githubusercontent.com/wulabing/V2Ray_ws-tls_bash_onekey/master/install.sh” && chmod +x install.sh && bash install.sh
```

### 注意事項
* 如果你不瞭解腳本中各項設置的具體含義，除域名外，請使用腳本提供的默認值
* 使用本腳本需要你擁有 Linux 基礎及使用經驗，瞭解計算機網絡部分知識，計算機基礎操作
* 目前支持Debian 9+ / Ubuntu 18.04+ / Centos7+ ，部分Centos模板可能存在難以處理的編譯問題，建議遇到編譯問題時，請更換至其他系統模板
* 群主僅提供極其有限的支持，如有問題可以詢問群友
* 每周日的凌晨3點，Nginx 會自動重啓以配合證書的簽發定時任務進行，在此期間，節點無法正常連接，預計持續時間為若干秒至兩分鐘

### 更新日誌
> 更新內容請查看 CHANGELOG.md

### 鳴謝
* ~~本腳本的另一個分支版本（Use Host）地址： https://github.com/dylanbai8/V2Ray_ws-tls_Website_onekey 請根據需求進行選擇~~ 該作者可能已停止維護
* 本腳本中 MTProxy-go TLS 版本項目引用 https://github.com/whunt1/onekeymakemtg 在此感謝 whunt1
* 本腳本中 銳速4合1腳本原項目引用 https://www.94ish.me/1635.html 在此感謝
* 本腳本中 銳速4合1腳本修改版項目引用 https://github.com/ylx2016/Linux-NetSpeed 在此感謝 ylx2016

### 證書
> 如果你已經擁有了你所使用域名的證書文件，可以將 crt 和 key 文件命名為 v2ray.crt v2ray.key 放在 /data 目錄下（若目錄不存在請先建目錄），請注意證書文件權限及證書有效期，自定義證書有效期過期後請自行續簽

腳本支持自動生成 let’s encrypted 證書，有效期3個月，理論上自動生成的證書支持自動續簽

### 查看客戶端配置
`cat ~/v2ray_info.txt`

### V2ray 簡介

* V2Ray是一個優秀的開源網絡代理工具，可以幫助你暢爽體驗互聯網，目前已經全平台支持Windows、Mac、Android、IOS、Linux等操作系統的使用。
* 本腳本為一鍵完全配置腳本，在所有流程正常運行完畢後，直接按照輸出結果設置客戶端即可使用
* 請注意：我們依然強烈建議你全方面的瞭解整個程序的工作流程及原理

### 建議單服務器僅搭建單個代理
* 本腳本默認安裝最新版本的V2ray core
* V2ray core 目前最新版本為 4.22.1（同時請注意客戶端 core 的同步更新，需要保證客戶端內核版本 >= 服務端內核版本）
* 建議使用默認的443端口作為連接端口
* 偽裝內容可自行替換。

### 注意事項
* 推薦在純淨環境下使用本腳本，如果你是新手，請不要使用Centos系統。
* 在嘗試本腳本確實可用之前，請不要將本程序應用於生產環境中。
* 該程序依賴 Nginx 實現相關功能，請使用 [LNMP](https://lnmp.org) 或其他類似攜帶 Nginx 腳本安裝過 Nginx 的用戶特別留意，使用本腳本可能會導致無法預知的錯誤（未測試，若存在，後續版本可能會處理本問題）。
* V2Ray 的部分功能依賴於系統時間，請確保您使用V2RAY程序的系統 UTC 時間誤差在三分鐘之內，時區無關。
* 本 bash 依賴於 [V2ray 官方安裝腳本](https://install.direct/go.sh) 及 [acme.sh](https://github.com/Neilpang/acme.sh) 工作。
* Centos 系統用戶請預先在防火牆中放行程序相關端口（默認：80，443）


### 啓動方式

啓動 V2ray：`systemctl start v2ray`

停止 V2ray：`systemctl stop v2ray`

啓動 Nginx：`systemctl start nginx`

停止 Nginx：`systemctl stop nginx`

### 相關目錄

Web 目錄：`/home/wwwroot/3DCEList`

V2ray 服務端配置：`/etc/v2ray/config.json`

V2ray 客戶端配置: `~/v2ray_info.inf`

Nginx 目錄： `/etc/nginx`

證書文件: `/data/v2ray.key 和 /data/v2ray.crt` 請注意證書權限設置

