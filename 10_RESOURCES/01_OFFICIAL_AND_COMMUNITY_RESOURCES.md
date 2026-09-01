# Recursos OSCP+ — catálogo curado

> Prioridad: documentación oficial primero; comunidad después. Revisa fechas porque el formato y las reglas cambian.

# 1. Fuentes oficiales OffSec — lectura obligatoria

## Exam Guide
https://help.offsec.com/hc/en-us/articles/360040165632-OSCP-Exam-Guide

Úsalo para:
- requisitos;
- estructura;
- documentación;
- reglas;
- submission.

## Exam FAQ
https://help.offsec.com/hc/en-us/articles/4412170923924-OSCP-Exam-FAQ

Úsalo para:
- escenarios de puntos;
- herramientas;
- IA;
- Metasploit;
- AD;
- pivoting.

## Candidate Handbook
https://help.offsec.com/hc/en-us/articles/40393367449108-OSCP-Candidate-Handbook

Úsalo para:
- registro;
- scheduling;
- proctoring;
- políticas;
- retakes;
- mantenimiento.

## Body of Knowledge
https://help.offsec.com/hc/en-us/articles/38543335188756-OSCP-Body-of-knowledge

Úsalo como índice curricular.

## Authoritative References List
https://help.offsec.com/hc/en-us/articles/37192004980628-Authoritative-References-List-OSCP

Muy importante porque publica los pesos:
- vulnerabilities 12%;
- exploitation 11%;
- PrivEsc 18%;
- AD 26%;
- reporting 33%.

## Reporting Requirements
https://help.offsec.com/hc/en-us/articles/360046787731-OSCP-Reporting-Requirements

## Exam Changes
https://help.offsec.com/hc/en-us/articles/29865898402836-OSCP-Exam-Changes

## PEN-200 12-week plan
https://help.offsec.com/hc/en-us/articles/15541765522196-OffSec-PEN-200-Learning-Plan-12-Week

## PEN-200 24-week plan
https://help.offsec.com/hc/en-us/articles/15545672357780-OffSec-PEN-200-Learning-Plan-24-Week

# 2. Laboratorios y práctica

## OffSec Proving Grounds
Prioridad alta por cercanía al ecosistema OffSec.

## PEN-200 Challenge Labs
Especialmente importantes para adaptación al estilo del curso.

## Hack The Box
Útil para volumen y técnicas variadas. Elegir máquinas con propósito, no perseguir únicamente un contador.

## HTB Academy Penetration Tester Path
Recomendado repetidamente en experiencias comunitarias como complemento metodológico.

## VulnLab
Puede aportar práctica de entornos Windows/AD. Mantener siempre el trabajo dentro del scope de la plataforma.

## TryHackMe
Útil especialmente para repasar fundamentos o temas concretos de forma guiada.

# 3. Recursos técnicos

## IppSec
https://www.youtube.com/@ippsec

Excelente para aprender proceso mental y enumeración en máquinas públicas de HTB. No consumir vídeos pasivamente: pausar antes de cada decisión y formular tu propia hipótesis.

## 0xdf
https://0xdf.gitlab.io/

Write-ups técnicos claros. Úsalos después de intentar la máquina o para estudiar una técnica concreta.

## HackTricks
https://book.hacktricks.xyz/

Referencia amplia. No usar como sustituto de metodología.

## GTFOBins
https://gtfobins.github.io/

Referencia para comportamiento de binarios Unix en contextos de PrivEsc autorizados.

## LOLBAS
https://lolbas-project.github.io/

Referencia defensiva/ofensiva sobre binarios nativos de Windows. Aplicar sólo dentro de entornos autorizados.

## Exploit-DB / Searchsploit
https://www.exploit-db.com/

Aprender a revisar y adaptar PoCs, no sólo ejecutarlos.

## PayloadsAllTheThings
https://github.com/swisskyrepo/PayloadsAllTheThings

Referencia amplia para labs web. Validar siempre el contexto.

# 4. Active Directory

- BloodHound documentation.
- SpecterOps material público.
- Impacket.
- PowerView.
- Microsoft Learn para fundamentos de AD/Kerberos/Windows.

Estudia también la perspectiva defensiva: comprender el modelo de seguridad evita memorizar ataques como recetas.

# 5. Experiencias públicas recientes guardadas en este repo

Ver:
`07_EXAM/02_PUBLIC_EXPERIENCES_AND_LESSONS.md`

# 6. Cómo elegir recursos

Usa esta jerarquía:

```text
1. OffSec oficial
2. Documentación del producto/protocolo
3. Fuente primaria del investigador/CVE
4. Write-up técnico fiable
5. Cheatsheet
6. Vídeo/comentario comunitario
```

# 7. Evitar

- dumps de examen;
- “exact boxes”;
- flags compartidas;
- filtraciones;
- repositorios que prometen reconstruir el examen real;
- material sin fecha sobre reglas del examen;
- herramientas que no entiendes.

# 8. Regla para añadir una nueva fuente al repo

Registrar:

```markdown
## Nombre
URL:
Fecha consultada:
Tema:
Nivel: oficial / primaria / comunidad
Por qué merece estar aquí:
Qué NO asumir de esta fuente:
```
