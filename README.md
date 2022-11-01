## Distribution

### What is it?

Distribution is contributed by [distribution](https://github.com/distribution/distribution).

### Example usages

- To build the image:

```console
$ docker build YOUR_VERSION/ --tag r3gistry/distribution:YOUR_VERSION
```

- To run the container in background:

```console
$ docker run -v distribution:/mnt/distribution/ -d --name YOUR_CONTAINER_NAME -p YOUR_PORT:YOUR_PORT r3gistry/distribution:YOUR_VERSION serve /mnt/distribution/config.yml
```

After first run, stop container and make changes to `config.yml` at `distribution`.

- To fetch logs of a container:

```console
$ docker logs YOUR_CONTAINER_NAME
```

### Donations

If you like to buy us coffee, you can donate to here:

- [Ko-fi](https://ko-fi.com/calvintam236)
- BTC: `1MTkPFtp3qxE4Y98pTHP3z767RGKmrT92a`
- ETH: `0x5896a85E8c175c563DC00087535582394d394838`
- XMR: `474adYsC8sLVM5gK8DbvtUVb237y9m5eMeRuYpJJVuoYUuMN5EYDuixHWxpEr6iNBb2zv3gowmJjcRoTrjhJLvMTRD1eKio`
- ETC: `0xFaBA3be3b3De5469C3F6C6185150928F3773C7b4`
- ZEC: `t1Z5Kc75JQ17txyaDUfwwyabTgsJMfuuSp4`
