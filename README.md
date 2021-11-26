# git-hooks

# define environment variables
```shell
SOURCE_ALIAS=mpdred/git-hooks
SOURCE_URL=https://github.com/mpdred/git-hooks
TARGET_DIR=.githooks
```

# configure
1. Define a new remote
```shell
git remote add $SOURCE_ALIAS $SOURCE_URL
```

2. Copy files from remote
```shell
git subtree add --prefix=$TARGET_DIR $SOURCE_ALIAS main                                                                                                             
```

3. Set new git hooks path
```shell
git config core.hooksPath $TARGET_DIR
```

# pull new changes
```shell
git subtree pull --prefix=$TARGET_DIR $SOURCE_ALIAS main
```

# cleanup
```shell
rm -rfv $TARGET_DIR || true
git remote remove $SOURCE_ALIAS
```
