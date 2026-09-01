# Windows Privilege Escalation — OSCP

## Objetivo

Convertir un foothold de bajo privilegio en acceso administrativo mediante configuración insegura, privilegios del token, servicios, tareas, credenciales o software vulnerable dentro de entornos autorizados.

## 1. Baseline

```powershell
whoami
whoami /all
hostname
systeminfo
ipconfig /all
net user
net localgroup administrators
```

Registrar:

- usuario y grupos;
- integrity level;
- privilegios del token;
- versión/build;
- arquitectura;
- dominio o workgroup.

## 2. Privilegios del token

```powershell
whoami /priv
```

Los privilegios especiales son pistas, no exploits automáticos. Debes reconocer qué privilegios están habilitados y qué clase de abuso sería posible en un laboratorio.

Especialmente relevantes para estudio:

- SeImpersonatePrivilege;
- SeAssignPrimaryTokenPrivilege;
- SeBackupPrivilege;
- SeRestorePrivilege;
- SeTakeOwnershipPrivilege.

## 3. Servicios

```powershell
sc query
wmic service get name,displayname,pathname,startmode
```

Analizar:

- binario o directorio editable;
- configuración modificable;
- rutas con espacios y quoting inseguro;
- cuenta bajo la que se ejecuta;
- posibilidad de reiniciar el servicio.

La cadena completa importa: **capacidad de modificar + ejecución privilegiada + posibilidad de disparar la ejecución**.

## 4. Tareas programadas

```powershell
schtasks /query /fo LIST /v
```

Buscar ejecutables/scripts editables o rutas donde el usuario tenga permisos de escritura.

## 5. Credenciales y secretos

```powershell
cmdkey /list
Get-ChildItem -Path C:\Users -Recurse -ErrorAction SilentlyContinue -Include *.config,*.xml,*.ini,*.txt,*.ps1
```

Revisar:

- PowerShell history;
- archivos de configuración;
- scripts;
- backups;
- unattended install files;
- credenciales guardadas;
- claves privadas.

PowerShell history suele encontrarse bajo el perfil del usuario en la ruta de PSReadLine.

## 6. Permisos ACL

Aprender a leer permisos con:

```powershell
icacls <PATH>
Get-Acl <PATH> | Format-List
```

Diferenciar:

- lectura;
- escritura;
- modificación;
- full control;
- herencia.

## 7. Software instalado y servicios locales

```powershell
Get-CimInstance Win32_Product | Select-Object Name,Version
netstat -ano
Get-Process
```

`Win32_Product` puede ser lento y provocar efectos secundarios en algunos sistemas; úsalo con criterio. Alternativas: claves de registro de uninstall y directorios instalados.

## 8. AlwaysInstallElevated

Conocer el concepto y cómo verificar la configuración, pero no asumir que aparece con frecuencia. El punto de estudio es reconocer una política insegura que permite instalaciones MSI elevadas cuando se cumplen las condiciones correspondientes.

## 9. Automatización

WinPEAS/PowerUp/Seatbelt pueden ayudar a identificar pistas. En entrenamiento:

1. enumeración manual;
2. ejecutar herramienta;
3. explicar cada hallazgo relevante;
4. reproducir manualmente el hallazgo.

## 10. Kernel/software exploits

Último recurso. Verificar siempre build, parcheado, arquitectura, precondiciones y estabilidad. OSCP recompensa más una metodología sólida que disparar PoCs al azar.

## Checklist de dominio

- [ ] identidad, grupos e integrity level.
- [ ] token privileges.
- [ ] servicios y ACLs.
- [ ] scheduled tasks.
- [ ] credenciales/secrets.
- [ ] software y puertos locales.
- [ ] registry/configuraciones relevantes.
- [ ] herramientas automáticas interpretadas.
- [ ] capacidad de documentar paso a paso.
