# various
some various notes that I want in one place

## generating ssh keys for git 

```
#Generating a new SSH key
ssh-keygen -t rsa -b 4096 -C "your_email@example.com"

#Adding your SSH key to the ssh-agent
eval "$(ssh-agent -s)"
ssh-add ~/.ssh/id_rsa

```



