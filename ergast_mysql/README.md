```
docker build -t f1db .
```

```
docker run --name f1db -v ./initdb:/docker-entrypoint-initdb.d -P -d f1db
```

I haven't actually figured out how to remote connect to it with python yet.
