# How To Use `iitd-proxy`

Ye guide Ubuntu machine par IIT Delhi proxy configure karne ke liye hai.

## 1. Script Ko Executable Banao

Project directory me jao:

```bash
cd /home/hp/LAB
```

Agar script executable nahi hai, to ye command chalao:

```bash
chmod +x iitd-proxy
```

## 2. Proxy Install / Setup

Basic command:

```bash
sudo ./iitd-proxy install ROLE USERID
```

Example:

```bash
sudo ./iitd-proxy install btech 2024xyz1234
```

Password command me dene ki zarurat nahi hai. Script hidden password prompt dikhayegi:

```text
IITD proxy password:
```

## 3. Supported Roles

Available roles:

```text
btech
mtech
phd
staff
```

Examples:

```bash
sudo ./iitd-proxy install btech YOUR_USERID
sudo ./iitd-proxy install mtech YOUR_USERID
sudo ./iitd-proxy install phd YOUR_USERID
sudo ./iitd-proxy install staff YOUR_USERID
```

## 4. Full Test Ke Saath Run Karna

Agar setup ke baad `apt-get update` bhi test karna hai:

```bash
sudo ./iitd-proxy install btech YOUR_USERID --full-test
```

Ye command proxy configure karne ke baad APT internet access bhi verify karegi.

## 5. Old Style Command Bhi Chalega

Backward compatible format:

```bash
sudo ./iitd-proxy btech YOUR_USERID
```

Password hidden prompt me manga jayega.

## 6. Kya Configure Hoga

Script ye cheezein configure karegi:

```text
APT proxy
System environment proxy
Login shell proxy
Systemd proxy
Snap proxy, agar snap pehle se installed hai
GNOME desktop proxy, agar desktop session available hai
```

Script unnecessary packages install nahi karegi.

Mandatory packages sirf ye hain:

```text
python3
python3-requests
ca-certificates
```

Agar ye packages already installed hain, next run par dobara install nahi honge.

## 7. Proxy Remove Karna

Proxy configuration clean karne ke liye:

```bash
sudo ./iitd-proxy remove
```

Ye APT, environment, systemd, snap aur desktop proxy settings clean karega.

## 8. Log File

Har run ka log yahan save hota hai:

```bash
/var/log/iitd_proxy_setup.log
```

Log dekhne ke liye:

```bash
sudo less /var/log/iitd_proxy_setup.log
```

## 9. Release Upgrade Ke Liye Use

Proxy setup ke baad normal Ubuntu commands chala sakte ho:

```bash
sudo apt update
sudo apt upgrade
sudo do-release-upgrade
```

Agar release upgrade ke beech reboot ho, proxy persistent rahegi kyunki system-wide config files me save hoti hai.

## 10. Recommended Flow

Fresh machine par:

```bash
cd /home/hp/LAB
chmod +x iitd-proxy
sudo ./iitd-proxy install btech YOUR_USERID --full-test
sudo apt update
sudo apt upgrade
sudo do-release-upgrade
```

Next time sirf proxy login/config verify karni ho:

```bash
sudo ./iitd-proxy install btech YOUR_USERID
```

