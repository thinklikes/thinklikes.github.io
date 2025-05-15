+++
lastmod = '2025-05-09T14:39:04+08:00'
date = '2025-05-09T14:39:04+08:00'
draft = false
title = '在本地環境安裝 n8n'
tags = ['n8n', '自動化']
topics = ['我在現實生活中用 n8n 開外掛過上平凡生活']
+++

{{< mermaid >}}
flowchart TD
   c1-->a2
{{< /mermaid >}}

## 前言
n8n 作為一套自動化管理工具，目前在 GitHub 上有超過 4 萬顆星星，十分火熱，而肥宅我也想朝聖，於是有了這些筆記的出現。這一系列的文章會是提供給應用程式開發已有基礎的朋友們，讓你們能夠快速上手 n8n 的使用，並且能夠在日常生活中使用 n8n 來幫助你們的工作。

### 使用工具
在這邊文章中，我們會使用這些工具在本地安裝並且設定 n8n。
- 容器管理工具：[Docker + Docker Compose](https://docs.docker.com/get-started/get-docker/)，MacOS 上也可以使用 [OrbStack](https://orbstack.dev/dashboard)
- ngrok：[ngrok](https://ngrok.com/) 是一個可以將本地端的服務公開到網路上的工具，這邊我們會使用 ngrok 來讓 n8n 的 webhook 可以被外部存取。
- 準備你的編輯器，可用 VSCode 或者是 JetBrains 的 IDE






## 拿出你的鍵盤吧！

### 註冊 ngrok 帳號

### 設置 Docker 環境
1. 下載 Docker Desktop，並且安裝
2. 建立一個空白專案資料夾並放入下列檔案
    ```ㄩ
    # n8n Configuration
    N8N_PORT=5678
    N8N_BASIC_AUTH_USER=admin
    N8N_BASIC_AUTH_PASSWORD=12345678

    # ngrok Configuration
    NGROK_AUTHTOKEN=1W3CqoImkaCeJFdRGYfxkUZrt7T_ukJjQa7VtzZDLdT33h6P
    NGROK_URL=https://golden-assured-pigeon.ngrok-free.app
    ```

```yaml
services:
    n8n:
        image: n8nio/n8n:latest
        restart: unless-stopped
        ports:
            - "${N8N_PORT:-5678}:5678" 
        environment:
            # Authentication
            - N8N_BASIC_AUTH_ACTIVE=true
            - N8N_BASIC_AUTH_USER=${N8N_BASIC_AUTH_USER:-admin}
            - N8N_BASIC_AUTH_PASSWORD=${N8N_BASIC_AUTH_PASSWORD:-change_this_password}
            - N8N_RUNNERS_ENABLED=true

            # Host configuration
            - N8N_HOST=${N8N_HOST:-localhost}
            - N8N_PORT=${N8N_PORT:-5678}
            - WEBHOOK_URL=${NGROK_STATIC_URL:-http://localhost:5678}

            # Execution settings
            - GENERIC_TIMEZONE=Asia/Taipei
            - TZ=Asia/Taipei
        volumes:
            - n8n_data:/home/node/.n8n
        depends_on:
            -  ngrok
        networks:
            - n8n_network

    ngrok:
        image: ngrok/ngrok:3-alpine
        restart: unless-stopped
        ports:
            - 4040:4040
        command:
            - "http"
            - "http://host.docker.internal:5678"
            - "--url"
            - "${NGROK_STATIC_URL}"
        environment:
            - NGROK_AUTHTOKEN=${NGROK_AUTHTOKEN}
        networks:
            - n8n_network
networks:
    n8n_network:
        name: n8n_network
        driver: bridge

volumes:
    n8n_data:
        name: n8n_public_data

```

### 說明


## 小結
