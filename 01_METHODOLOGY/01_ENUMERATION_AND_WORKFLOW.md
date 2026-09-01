# Enumeración y metodología profesional

## Objetivo

Construir una metodología que reduzca la improvisación. En OSCP, enumerar bien suele ser más valioso que probar exploits al azar.

## 1. Preparación de cada objetivo

Crear una carpeta por host:

```text
TARGET/
├── scans/
├── web/
├── loot/
├── screenshots/
├── notes.md
└── commands.log
```

Registrar desde el principio:

- IP/hostname.
- Puertos.
- Servicios/versiones.
- DNS/nombres virtuales.
- Credenciales obtenidas.
- Hipótesis abiertas.
- Intentos fallidos.
- Evidencias de foothold/root/Administrator.

## 2. Escaneo de red en laboratorio

Ejemplos típicos para entornos autorizados:

```bash
nmap -Pn -p- --min-rate 3000 -T4 <IP> -oA scans/all-ports
nmap -Pn -sC -sV -p <PORTS> <IP> -oA scans/services
sudo nmap -Pn -sU --top-ports 100 <IP> -oA scans/udp-top100
```

No te quedes únicamente con el `-sC -sV`. El objetivo es construir un inventario de superficie de ataque.

## 3. Tabla de decisión por servicio

| Servicio | Preguntas iniciales |
|---|---|
| HTTP/HTTPS | ¿Virtual hosts? ¿Tecnología? ¿Login? ¿Uploads? ¿API? ¿Directorios? |
| SMB | ¿Shares? ¿Anonymous/guest? ¿Usuarios? ¿Permisos? |
| SSH | ¿Versión? ¿Usuarios/credenciales obtenidas? ¿Claves encontradas? |
| FTP | ¿Anonymous? ¿Write? ¿Contenido relacionado con web? |
| SMTP | ¿Usuarios enumerables? ¿Información interna? |
| SNMP | ¿Community strings? ¿Procesos/usuarios/interfaces? |
| LDAP | ¿Dominio? ¿Objetos accesibles? ¿Naming contexts? |
| Kerberos | ¿Usuarios válidos? ¿Preauth? ¿SPNs? |
| WinRM | ¿Credenciales válidas? ¿Acceso remoto interactivo? |
| SQL | ¿Credenciales? ¿Permisos? ¿Funciones peligrosas/configuración? |

## 4. Enumeración web

Checklist:

- headers y redirecciones;
- tecnologías;
- robots/sitemap;
- vhosts/subdominios de laboratorio;
- directorios y ficheros;
- parámetros GET/POST;
- cookies/sesiones;
- endpoints API;
- uploads;
- autenticación/recuperación de contraseña;
- referencias a rutas locales;
- credenciales/secrets expuestos;
- backups y archivos de configuración.

Herramientas habituales:

```bash
curl -i http://<IP>/
whatweb http://<IP>/
ffuf -u http://<IP>/FUZZ -w <WORDLIST>
ffuf -u http://<IP>/ -H 'Host: FUZZ.example.lab' -w <WORDLIST> -fs <BASELINE_SIZE>
```

La herramienta nunca sustituye a la inspección manual.

## 5. Hipótesis

Usa una tabla como ésta:

| # | Hipótesis | Evidencia | Prueba | Estado |
|---|---|---|---|---|
| H1 | vhost oculto | certificado/nombre | fuzz Host header | pendiente |
| H2 | LFI | parámetro `page` | traversal controlado | pendiente |
| H3 | credencial reutilizada | contraseña encontrada | validar en servicios permitidos del lab | pendiente |

## 6. Foothold

Antes de buscar un payload, contesta:

1. ¿Qué entrada controlo?
2. ¿Dónde llega esa entrada?
3. ¿Qué contexto/usuario ejecuta el proceso?
4. ¿Qué defensa o restricción puede interferir?
5. ¿Cómo demostraré el impacto de forma mínima y reproducible?

## 7. Enumeración post-explotación

### Linux

```bash
id
uname -a
cat /etc/os-release
sudo -l
ss -lntup
ps aux
find / -perm -4000 -type f 2>/dev/null
getcap -r / 2>/dev/null
```

Buscar también:

- cron/systemd;
- permisos débiles;
- credenciales en configs;
- claves SSH;
- servicios locales;
- grupos interesantes;
- binarios SUID/capabilities;
- montajes/NFS;
- versiones vulnerables cuando la evidencia lo justifique.

### Windows

```powershell
whoami /all
systeminfo
ipconfig /all
netstat -ano
sc query
schtasks /query /fo LIST /v
cmdkey /list
```

Buscar:

- servicios modificables;
- rutas de servicio inseguras;
- tareas programadas;
- privilegios del token;
- credenciales y archivos de configuración;
- historial de PowerShell;
- shares/unidades;
- software instalado;
- procesos y puertos locales.

## 8. Registro de intentos fallidos

No borrar los fallos. Un buen log evita repetir la misma prueba bajo estrés:

```text
14:10 H2 LFI: ../../../../etc/passwd -> 200 pero contenido idéntico baseline.
14:17 encoding doble -> 403.
Conclusión: aparcar hasta encontrar evidencia adicional.
```

## 9. Métricas útiles

Tras cada máquina registrar:

- tiempo hasta inventario de puertos;
- tiempo hasta vector correcto;
- tiempo hasta foothold;
- tiempo hasta PrivEsc;
- número de rabbit holes >20 min;
- número de hints usados;
- si el informe se podría reproducir desde cero.

## 10. Criterio de progreso

**Nivel 1:** necesitas walkthrough.

**Nivel 2:** necesitas hints.

**Nivel 3:** resuelves con documentación propia.

**Nivel 4:** resuelves cronometrado, documentas a la vez y puedes explicar por qué funcionó.

El objetivo de examen es aproximarse a Nivel 4.
