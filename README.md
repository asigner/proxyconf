# Proxy configuration for developers

When working in a bigger company, you probably will need to configure your tools to bypass the corporate proxy.

Depending on your operating system and programs different configurations might be needed.

## Basics

Let's assume that your proxy consist out of the following parts:

- user
- pass
- host
- port

This results in a proxy URL: http://user:pass@host:port or if the proxy doesn't need authentication the simpler version http://host:port might be sufficient.


## Configurations

## Git

Use these Git commands:

```bash
git config --global http://user:pass@host:port
git config --global https.proxy http://user:pass@host:port
```

Or you can edit directly your ```~/.gitconfig``` file:

```bash
[http]
        proxy = http://user:pass@host:port
[https]
        proxy = http://user:pass@host:port
```

