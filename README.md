# wireguard-configs-for-ai-services

This repository provides sample WireGuard configuration files designed to facilitate access to AI services such as **Apple Intelligence**, **Google Gemini/NotebookLM**and **OpenAI** from *regions where these services are not restricted*, with WireGuard configuration profiles utilizing Include Tunneling. These configuration files can help users securely connect and access AI resources through **split tunneling**.

See also: <https://github.com/gabrielkoo/openvpn-configs-for-ai-services> if you are using OpenVPN instead.

## Why Bother Use Include Tunneling?

You may have wondered - *I could have just used a normal WireGuard config profile!*

If you are turning on a always-on VPN just for the sake of securely connecting to AI resources via *an unrestricted region*, it might slow down your entire web browsing experience as a whole, also it might affect your access to security-aware services like e-banking or your company resources, which are sensitive to VPN IP addresses. If you are using a split tunnel instead, you are only routing the traffic to the VPN only when it connects to the AI service - this essentially reduces the traffic load on your VPN server, and minimizes the interruption to your other normal browsing activities.

## How It Works

Open your `*.conf` WireGuard configuration file in your favourite text editor.

For each services, research for it's public IP ranges. Try to reduce the list of IP CIDR blocks into broader CIDR blocks.

Add them into the `Peer.AllowedIPs` block.

That's it!

## AI Services Included in This Repository

AI Service | Sub Services | Details
---|---|---
Apple Intelligence | iCloud Private Relay, Writing Tools (iOS 18.1), ChatGPT Integration (iOS 18.2) | [Apple's `17.0.0.0/8` IPv4 Prefix](https://support.apple.com/en-us/101555#:~:text=Yes-,Firewalls,-If%20your%20firewall) and [Apple Intelligence, Siri, and Search](https://support.apple.com/en-us/101555#:~:text=Yes-,Apple%20Intelligence,-%2C%20Siri%2C%20and%20Search)
Google Gemini | Gemini Web App, NotebookLM | Condensed from <https://www.gstatic.com/ipranges/goog.json>.
OpenAI | ChatGPT.com, platform.openai.com | By Trial and Error.

## Disclaimer**

The use of these configuration files is at your own risk. This repository is intended only for users whose home country is **permitted** to access these AI services. The author takes no responsibility for any misuse or legal implications that may arise from the use of these files.
