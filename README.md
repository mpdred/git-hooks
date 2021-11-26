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

3. Set new git hooks path, and mark the files as executable
```shell
git config core.hooksPath $TARGET_DIR
ls $TARGET_DIR | grep -iv -e 'readme' -e 'license' | xargs -n1 -I {} sh -c "chmod +x $TARGET_DIR/{}"
git add $TARGET_DIR
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
