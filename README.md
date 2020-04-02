# various
some various notes that I want in one place

## Making and trusting your own certificates
[source](https://letsencrypt.org/docs/certificates-for-localhost/)
Anyone can make their own certificates without help from a CA. The only difference is that certificates you make yourself won’t be trusted by anyone else. For local development, that’s fine.

The simplest way to generate a private key and self-signed certificate for localhost is with this openssl command:

```bash
openssl req -x509 -out localhost.crt -keyout localhost.key \
  -newkey rsa:2048 -nodes -sha256 \
  -subj '/CN=localhost' -extensions EXT -config <( \
   printf "[dn]\nCN=localhost\n[req]\ndistinguished_name = dn\n[EXT]\nsubjectAltName=DNS:localhost\nkeyUsage=digitalSignature\nextendedKeyUsage=serverAuth")

```
You can then configure your local web server with localhost.crt and localhost.key, and install localhost.crt in your list of locally trusted roots.
* * *


## generating ssh keys for git 


### Generating a new SSH key
```bash
ssh-keygen -t rsa -b 4096 -C "your_email@example.com"
```

### Adding your SSH key to the ssh-agent
```bash
eval "$(ssh-agent -s)"
ssh-add ~/.ssh/id_rsa

```



