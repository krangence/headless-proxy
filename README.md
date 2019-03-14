# Headless Desktop

### Install Docker (Ubuntu)
```
curl -fsSL https://download.docker.com/linux/ubuntu/gpg | sudo apt-key add -
sudo add-apt-repository "deb [arch=amd64] https://download.docker.com/linux/ubuntu $(lsb_release -cs) stable edge"
sudo apt-get install -y git docker-ce docker-compose
```

### Clone repo
```
git clone https://github.com/krangence/headless-proxy.git && cd headless-proxy
```

### Change variables
```
# Replace youruser and yourpass with your user and your pass
sed -i 's/{{creds}}/youruser yourpass/g' volumes/docker-gen/templates/caddy.tmpl
# Replace your@email.org with your email
sed -i 's/{{email}}/your@email.org/g' docker-compose.yml
# Replace your.domain.org with your domain
sed -i 's/{{domain}}/your.domain.org/g' docker-compose.yml
```

### Create network and compose up!
```
docker network create -d bridge caddy-proxy
docker-compose up -d
```

### Profit!
