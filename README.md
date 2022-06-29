# Cloudflare DDNS

## What is Cloudflare Dynamic DNS?

DNS records are inherently static, and it does not play well with dynamic IP addresses. Now, to solve that problem, you’ll need to set up dynamic DNS. Fortunately, Cloudflare provides an API that allows you to manage DNS records programmatically.

To set up a Cloudflare dynamic DNS, you’ll need to run a process on a client inside your network that does two main actions: get your network’s current public IP address and automatically update the corresponding DNS record.

The image below shows the high-level diagram of how the Cloudflare dynamic DNS update flow happens.

![](https://adamtheautomator.com/wp-content/uploads/2021/09/image-243.png)

it's now possible to update DNS records (A and/or AAAA) of a domain on Clouldflare via API Token.

To do so you need to:

1. Go to the [My Account -> API Tokens](https://dash.cloudflare.com/profile/api-tokens).

![](https://i.imgur.com/PawdohI.png)

2. Create an API with the template "Edit Zone DNS".

![](https://i.imgur.com/wKcyTeA.png)

3. Make sure that permissions are **ZONE** > **DNS** > **Edit**

4. Select the zone (domain name), **Sofiane.email** in my case.

![](https://i.imgur.com/z8NUJ4o.png)


## Use the API on **Linux**

1. Download the bash script in a file, e.g. `cloudflare.sh`.

```
wget -O cloudflare.sh https://raw.githubusercontent.com/SofianeHamlaoui/cloudflare-DDNS/main/cloudflare.sh
```
2. Make it executable.

`chmod +x /path/to/cloudflare.sh`.

3. Run `crontab -e` and add a line like `@weekly /path/to/cloudflare.sh` to the end of the file to run the script periodically. Use tools like [Crontab Guru](https://crontab.guru/) to define the frequency properly.

## Use the API on **Windows**

1. Download and install Powershell 7.1+ 
  - https://github.com/PowerShell/powershell/releases
![](https://i.imgur.com/p651581.png)

2. Download the **cloudflare.ps1** script 

3. run the script with the right information

![](https://i.imgur.com/vqrH5Jn.png)
