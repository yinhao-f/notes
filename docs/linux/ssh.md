# Generate SSH Key (for GitHub)

## Check existing keys

```
ls -al ~/.ssh
# keys may look like:
# id_rsa.pub
# id_ecdsa.pub
# id_ed25519.pub
```

## Generate a new key

```
ssh-keygen -t ed25519 -C "email@address.com"
```

## Add the key to the ssh-agent

```
eval "$(ssh-agent -s)"
ssh-add ~/.ssh/id_ed25519
```

## Add the key to GitHub

```
cat ~/.ssh/id_ed25519.pub
```

Then copy the contents and paste it to GitHub