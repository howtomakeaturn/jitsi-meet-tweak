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

---

Developer notes

```
/**
 * Modification by @howtomakeaturn
 */
 .filmstrip {
    width: 100%;
    max-width: none;
    right: -50%;
    z-index: 2;
    padding: 0;
}

#localVideoWrapper video {
    width: 50%;
}

#largeVideoWrapper video {
    width: 50%;
}
```

```
make || { echo "Make failed"; exit 1; }
make source-package || { echo "Make source-package failed"; exit 1; }

echo "Moving and unzipping Jitsi-Meet package archive into Docker build context" && sleep 1

mv $TELEHEALTH_JITSI_MEET_DIR/jitsi-meet.tar.bz2 $REPO_ROOT/Docker/web || { echo "Failed to move packages to destination"; exit 1; }
cd $REPO_ROOT/Docker/web || { echo "Failed to find $REPO_ROOT/Docker/Web"; exit 1; }
tar -xvf jitsi-meet* || { echo "Failed to unzip archive"; exit 1; }
rm -rf $REPO_ROOT/Docker/web/jitsi-meet.tar.bz2

echo "Rebuilding Jitsi-Meet web Docker image" && sleep 1

docker build -t jitsi/web . || { echo "Docker operation failed"; exit 1; }
```
