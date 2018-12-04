## env
```yaml
alpine:     3.8
Python:     3.6.x
```

## build & upload
```sh
docker build -t <YOURNAME>/py3-cx .

# create a tag if needed
docker tag <YOURNAME>/py3-cx <YOURNAME>/py3-cx:181204

docker push <YOURNAME>/py3-cx
```

## Run image
```sh
docker run -it <YOURNAME>/py3-cx
```
