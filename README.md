# SSH Plus Manager RO (Ubuntu 22.04 / 24.04 / 26.04)

Panou complet de administrare tunel SSH / SSL / WebSocket în limba română, compatibil cu **Oracle Cloud (ARM64)**, **x86_64** și **Python 3.12+**.

## Funcționalități incluse
- **Port 443 (`stunnel4`):** Terminare SSL/TLS + SNI cu certificat Let's Encrypt și reînnoire automată.
- **Port 8081 (`dispatcher.py`):** Separă automat traficul SSH direct de cel HTTP/WebSocket.
- **Port 80 (`wsproxy.py`):** Proxy WebSocket compatibil Cloudflare (Proxied / CDN) și payload-uri custom.
- **Port 7300 (`badvpn-udpgw`):** Suport UDP pentru apeluri și jocuri.
- **Meniu complet (`menu`):** Monitorizare trafic GB/MB fără pâlpâire, IP-uri conectate + viteză live DL/UL per user, Auto-Limiter și Backup utilizatori.

---

## 1. Instalare pe un server nou (de la zero)
Rulează această comandă în terminal (funcționează direct atât de pe contul `ubuntu`, cât și de pe `root`):

```bash
sudo bash -c "$(curl -fsSL https://raw.githubusercontent.com/network5gplus/sshplus-manager-ro/main/install-sshplus-ro.sh)"
```

## 2. Actualizare pe un server existent (păstrează utilizatorii și SSL-ul)
Rulează această comandă pe orice server unde ai deja instalat SSH Plus Manager:

```bash
sudo bash -c "$(curl -fsSL https://raw.githubusercontent.com/network5gplus/sshplus-manager-ro/main/update.sh)"
```
### 3. Configurare Payload
Payload stabil pentru porturile 80 și 443
Copiază codul de mai jos și înlocuiește 
`<DOMENIU_VPS>` și `<SNI>` cu datele tale:

```text
GET / HTTP/1.1[crlf]Host: <DOMENIU_VPS>[crlf]X-Online-Host: <SNI>[crlf]X-Forward-Host: <SNI>[crlf]User-Agent: Mozilla/5.0 (Windows NT 10.0; Win64; x64) AppleWebKit/537.36 (KHTML, like Gecko) Chrome/121.0.0.0 Safari/537.36[crlf]Upgrade: websocket[crlf]Connection: Upgrade[crlf][crlf]
```
