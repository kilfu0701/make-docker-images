## env
```yaml
Ubuntu:     18.04
Python:     3.6.x
tensorflow: latest
```

## build & upload
```sh
docker build -t <YOURNAME>/py3-tensorflow .
docker push <YOURNAME>/py3-tensorflow
```

## Run image
```sh
docker run -it <YOURNAME>/py3-tensorflow /bin/bash
```
