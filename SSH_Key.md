## Adding a new `SSH` key to your GitHub account
Open your Terminal

### Step 1

```bash
ssh-keygen -t ed25519 -C "kubilaydogan.us@gmail.com"
```

> Enter passphrase: {`create a password for code commit`}

### Step 2

```zsh
eval "$(ssh-agent -s)"
```
### Step 3

```zsh
ssh-add --apple-use-keychain ~/.ssh/id_ed25519
```
### Step 4

```zsh
pbcopy < ~/.ssh/id_ed25519.pub
```

### Step 5 

Open **GitHub** click on **New SSH key** under "Settings/SSH and GPG keys" menu and <br>
paste your key into the "Key" field.