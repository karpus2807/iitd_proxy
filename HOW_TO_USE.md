# How To Use `iitd-proxy`

Short guide for IIT Delhi proxy setup on Ubuntu.

## 1. Make Script Executable

```bash
cd /home/hp/LAB
chmod +x iitd-proxy
```

## 2. Install / Enable Proxy

Format:

```bash
sudo ./iitd-proxy install ROLE USERID
```

Example:

```bash
sudo ./iitd-proxy install btech 2024xyz1234
```

Password command me mat do. Script hidden prompt me password mangegi.

## 3. Supported Roles

```text
btech
mtech
phd
staff
faculty
visitor
```

Examples:

```bash
sudo ./iitd-proxy install btech YOUR_USERID
sudo ./iitd-proxy install mtech YOUR_USERID
sudo ./iitd-proxy install phd YOUR_USERID
sudo ./iitd-proxy install staff YOUR_USERID
sudo ./iitd-proxy install faculty YOUR_USERID
sudo ./iitd-proxy install visitor YOUR_USERID
```

Old style bhi chalega:

```bash
sudo ./iitd-proxy btech YOUR_USERID
```

## 4. What It Configures

Script ye sab configure karti hai:

```text
IITD proxy login
APT proxy
Snap proxy, if snap is installed
Ubuntu desktop proxy, GNOME Settings proxy on/off
System environment proxy
Login shell proxy
Systemd proxy
wget proxy
curl proxy
Cursor proxy, if Cursor settings folder exists
```

Ubuntu Settings me proxy `Off` ho to install command usko automatically `Manual` enable karegi.

## 5. Full Test

APT update test bhi chahiye ho:

```bash
sudo ./iitd-proxy install btech YOUR_USERID --full-test
```

Manual checks:

```bash
sudo apt update
snap debug connectivity
source /etc/profile.d/iitd-proxy.sh
wget google.com
```

Note: `apt update` hamesha `sudo` ke saath run karo.

## 6. Remove / Disable All Proxy

Single command:

```bash
sudo ./iitd-proxy remove
```

Ye clean karega:

```text
APT proxy
Snap proxy
Ubuntu desktop proxy, turns it off
System environment proxy
Login shell proxy
Systemd proxy
wget proxy
curl proxy
Cursor proxy set by this script
```

Remove ke baad already-open apps restart karo. GUI apps ke liye logout/login ya reboot best hai.

## 7. Release Upgrade

Proxy setup ke baad:

```bash
sudo apt update
sudo apt upgrade
sudo do-release-upgrade -c
sudo do-release-upgrade
```

## 8. Logs

Log file:

```bash
/var/log/iitd_proxy_setup.log
```

View:

```bash
sudo less /var/log/iitd_proxy_setup.log
```

## 9. Quick Recommended Flow

```bash
cd /home/hp/LAB
chmod +x iitd-proxy
sudo ./iitd-proxy install btech YOUR_USERID --full-test
sudo apt update
sudo do-release-upgrade -c
```

