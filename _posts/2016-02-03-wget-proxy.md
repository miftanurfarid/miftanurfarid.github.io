---
layout: post
title: Configuring Wget for Proxy-Restricted Campus Networks
date: 2016-02-03 15:06:00
description: The internet at my campus, Institut Teknologi Sepuluh Nopember, uses a proxy, which makes downloading files with wget challenging. This post provides guidance on configuring wget with proxy settings to facilitate downloads in such an environment.
tags: linux wget proxy
categories: linux
---

Open the `wgetrc` file in the `etc` folder by using the following command in the terminal:

```bash
sudo gedit /etc/wgetrc
```

You can replace `gedit` with the editor you prefer, such as `nano`, `vim`, etc.

Search for the text that looks like this:

```plaintext
# You can set the default proxies for Wget to use for http, https, and ftp.
# They will override the value in the environment.
#https_proxy = http://proxy.yoyodyne.com:18023/
#http_proxy = http://proxy.yoyodyne.com:18023/
#ftp_proxy = http://proxy.yoyodyne.com:18023/
```

Then, remove the hash symbol (`#`) and edit the `https_proxy`, `http_proxy`, and `ftp_proxy` sections according to the proxy you use. For example:

```plaintext
# You can set the default proxies for Wget to use for http, https, and ftp.
# They will override the value in the environment.
https_proxy = http://proxy.mycampus.com:8023/
http_proxy = http://proxy.mycampus.com:8023/
ftp_proxy = http://proxy.mycampus.com:8023/
```

If the proxy you use requires authentication with a username and password, set it up as follows:

```plaintext
# You can set the default proxies for Wget to use for http, https, and ftp.
# They will override the value in the environment.
https_proxy = http://username:password@proxy.mycampus.com:8023/
http_proxy = http://username:password@proxy.mycampus.com:8023/
ftp_proxy = http://username:password@proxy.mycampus.com:8023/
```

Then, remove the hash symbol (`#`) from `use_proxy = on` to enable it:

```plaintext
# If you do not want to use proxy at all, set this to off.
use_proxy = on
```

Finally, save the file.
