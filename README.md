This repository is used to maintain a simple container with all that's required to use `bedrock`, from https://github.com/SUSE/bedrock-toolkit

Using podman, you just need to pull the image, then run it with a couple of volumes (one for the AWS login info, one to bind a folder the content you want to use with claude

```bash
IMAGE=ghcr.io/multi-linux-manager/bedrock-container:latest
podman pull ${IMAGE}
podman run \
       --userns=keep-id \
       -ti --rm \
       -v bedrock-aws:/home/bedrock/.aws \
       -v bedrock-claude:/home/bedrock/.claude \
       -v <PATH_TO_DIR_WITH_YAML>:/home/bedrock/bedrock-configs:Z \
        ${IMAGE}
```

For convenience, you can also use the script `bedrock` from this repository.
```bash
./bedrock -h
```

You can place it somewhere in your PATH, so you can call it from anywhere.
