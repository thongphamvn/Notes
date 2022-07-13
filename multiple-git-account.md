
## Config multiple github accounts on the same machine
1. Gennerate ssh key: `ssh-keygen`
3. Add private key to ssh agent: `ssh-add ~/.ssh/<private_key_file>`
4. Add public key to Github config
5. Repeat for for 2nd account
6. Modify ~/.ssh/config file, example:
```
#Me
Host me.github.com
  HostName github.com
  User git
  PreferredAuthentications publickey
  IdentityFile ~/.ssh/id_rsa_me


#Work
Host work.github.com
  HostName github.com
  User git
  #PreferredAuthentications publickey
  IdentityFile ~/.ssh/id_rsa_work
```
7. When clone a repo, modify the `host` accordingly
ex: `git@github.com:thongphamvn/notes.git` => `git@me.github.com:thongphamvn/notes.git` to use personal cred
8. Short explaination: The public key in Github config will be validated against private key added in the ssh-agent
