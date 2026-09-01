# Command Index — sólo para laboratorios autorizados

> Índice de referencia rápida. No sustituye a los capítulos ni a comprender qué hace cada comando.

## Nmap

```bash
nmap -Pn -p- --min-rate 3000 -T4 <IP> -oA scans/all
nmap -Pn -sC -sV -p <PORTS> <IP> -oA scans/services
sudo nmap -Pn -sU --top-ports 100 <IP> -oA scans/udp
```

## HTTP

```bash
curl -i http://<IP>/
whatweb http://<IP>/
ffuf -u http://<IP>/FUZZ -w <WORDLIST>
```

## SMB

```bash
smbclient -L //<HOST>/ -N
smbclient -L //<HOST>/ -U '<USER>%<PASS>'
smbclient //<HOST>/<SHARE> -U '<USER>%<PASS>'
```

## DNS

```bash
dig @<DNS_SERVER> <DOMAIN> A
dig @<DNS_SERVER> <DOMAIN> ANY
```

## LDAP

```bash
ldapsearch -x -H ldap://<DC> -s base namingcontexts
```

## Searchsploit

```bash
searchsploit <PRODUCT> <VERSION>
searchsploit -x <ID>
searchsploit -m <ID>
```

## Linux local enumeration

```bash
id
sudo -l
uname -a
cat /etc/os-release
ss -lntup
ps auxww
find / -perm -4000 -type f 2>/dev/null
getcap -r / 2>/dev/null
cat /etc/crontab
```

## Windows local enumeration

```powershell
whoami /all
systeminfo
ipconfig /all
route print
netstat -ano
sc query
schtasks /query /fo LIST /v
cmdkey /list
```

## ACLs Windows

```powershell
icacls <PATH>
Get-Acl <PATH> | Format-List
```

## SSH tunnels

```bash
ssh -L <LOCAL_PORT>:<INTERNAL_HOST>:<INTERNAL_PORT> user@pivot
ssh -D 1080 user@pivot
```

## Listener básico en lab

```bash
nc -lvnp <PORT>
```

## File transfer — servidor temporal

```bash
python3 -m http.server 8000
```

## Toma de notas

Guardar siempre:

```text
command:
output:
interpretation:
next hypothesis:
evidence file:
```

## Regla de oro

Si no puedes explicar:

- qué hace;
- qué tráfico genera;
- qué permisos requiere;
- qué output esperas;
- qué significa un error;

entonces el comando todavía no forma parte de tu metodología.
