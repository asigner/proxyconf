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

## Git configuration

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

## Gradle configuration

HTTP Only Proxy configuration
```bash
gradlew -Dhttp.proxyHost=127.0.0.1 -Dhttp.proxyPort=3128
```

HTTPS Only Proxy configuration
```bash
gradlew -Dhttps.proxyHost=127.0.0.1 -Dhttps.proxyPort=3129
```

Or to persist the proxy configuration add the properties below in your ```gradle.properties``` file and in your ```gradle/wrapper/gradle-wrapper.properties``` file if you are downloading the wrapper over a proxy.

If you want to set these properties globally then add it in ```~/.gradle/gradle.properties``` file.

```bash
## Proxy setup
systemProp.proxySet="true"
systemProp.http.keepAlive="true"
systemProp.http.proxyHost=host
systemProp.http.proxyPort=port
systemProp.http.proxyUser=user
systemProp.http.proxyPassword=pass
systemProp.http.nonProxyHosts=localhost|another.example.com

systemProp.https.keepAlive="true"
systemProp.https.proxyHost=host
systemProp.https.proxyPort=port
systemProp.https.proxyUser=user
systemProp.https.proxyPassword=pass
systemProp.https.nonProxyHosts=localhost|another.example.com
## end of proxy setup
```

## Maven configuration

Edit the proxies session in your ```~/.m2/settings.xml``` file:

```xml
<proxies>
    <proxy>
        <id>id</id>
        <active>true</active>
        <protocol>http</protocol>
        <username>user</username>
        <password>pass</password>
        <host>host</host>
        <port>port</port>
        <nonProxyHosts>localhost</nonProxyHosts>
    </proxy>
</proxies>
```

## Apt configuration

Edit ```/etc/apt/apt.conf.d/proxy.conf``` file:

```bash
Acquire::http::Proxy "http://user:pass@host:port/";
Acquire::https::Proxy "http://user:pass@host:port/";
```

## NPM configuration

Use these NPM commands:

```bash
npm config set proxy http://user:pass@host:port
npm config set https-proxy http://user:pass@host:port
```

Or you can edit directly your ```~/.npmrc``` file:

```bash
proxy=http://user:pass@host:port
https-proxy=http://user:pass@host:port
https_proxy=http://user:pass@host:port
```