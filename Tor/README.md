<h1>Tor</h1>

### Install tor
```xml
sudo pacman -S tor
```

### Enable and Start tor
```xml
sudo systemctl enable --now tor.service
```

### Status tor
```xml
sudo systemctl status tor
```

### Restart tor
```xml
sudo systemctl restart tor
```

<h2>Configuring Connection</h2>

### SOCKS5 Domain
```xml
127.0.0.1
```

### SOCKS5 Port
```xml
9050
```
