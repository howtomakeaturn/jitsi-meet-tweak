更新流程

1. jitsi-meet-tweak 更新前端 UI 程式碼

2. 將程式碼更新到另一個 repo: docker-jitsi-meet-tweak

3. 連線到正式機的 repo: docker-jitsi-meet-tweak

4. git pull

5. 最後重新 build image

```
cd web/
docker build --no-cache -t jitsi/web:tweak .
```
