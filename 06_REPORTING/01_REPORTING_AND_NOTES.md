# Reporting y toma de notas — OSCP+

## Importancia

OffSec asigna **33% del Body of Knowledge** al dominio `Documenting Findings`, el peso individual más alto de su lista de referencias autoritativas. Además, para obtener la certificación debes entregar un informe de pentest que permita reproducir los pasos que justifican los objetivos alcanzados.

## 1. Regla principal

**No documentes al final: documenta mientras trabajas.**

Cada hallazgo debe responder:

1. ¿Qué observé?
2. ¿Qué hipótesis generó?
3. ¿Qué comando/acción ejecuté?
4. ¿Qué output relevante obtuve?
5. ¿Cómo condujo al siguiente paso?
6. ¿Qué evidencia demuestra el objetivo?

## 2. Plantilla de notas por máquina

```markdown
# Host: 192.0.2.10

## Summary
- Hostname:
- OS:
- User foothold:
- PrivEsc:
- Flags/evidencias:

## Ports
| Port | Service | Version | Notes |
|---|---|---|---|

## Enumeration
### HTTP 80
...

## Hypotheses
- [ ] H1 ...
- [ ] H2 ...

## Initial Access
### Evidence
### Commands
### Explanation

## Privilege Escalation
### Evidence
### Commands
### Explanation

## Credentials / Loot

## Lessons learned
```

## 3. Capturas

Una captura buena:

- muestra el comando relevante;
- muestra el resultado relevante;
- mantiene contexto suficiente para identificar host/usuario;
- evita recortes que hagan imposible entender la secuencia.

Guarda nombres útiles:

```text
01_nmap_services.png
02_web_admin_panel.png
03_initial_shell_whoami.png
04_privesc_evidence.png
05_proof.png
```

## 4. Reproducibilidad

Antes de cerrar una máquina, imagina que otra persona sólo recibe tu informe. Debe poder reconstruir:

- dirección del objetivo;
- endpoint/servicio afectado;
- parámetros;
- payload o PoC modificado;
- transferencia de archivos;
- listener;
- credenciales;
- comandos de escalada;
- resultado final.

## 5. Estructura profesional de un finding

### Título
Nombre claro de la vulnerabilidad o cadena.

### Impacto
Qué obtuvo el atacante: acceso inicial, ejecución de comandos, privilegios administrativos, movimiento lateral, etc.

### Evidencia
Capturas y output mínimo necesario.

### Reproducción
Pasos numerados y comandos.

### Causa
Configuración o vulnerabilidad que permitió el ataque.

### Remediación
Acción concreta y verificable.

## 6. Tabla de evidencias

| ID | Host | Objetivo | Evidencia | Capturada | Reproducible |
|---|---|---|---|---|---|
| E01 | host1 | foothold | shell + usuario | ✅ | ✅ |
| E02 | host1 | admin | proof + identity | ✅ | ✅ |

## 7. Checklist antes de entregar

- [ ] PDF final correcto.
- [ ] máquinas en el orden deseado.
- [ ] todos los objetivos documentados.
- [ ] comandos legibles.
- [ ] capturas legibles.
- [ ] credenciales necesarias incluidas.
- [ ] no faltan pasos intermedios.
- [ ] no hay secretos personales o datos ajenos.
- [ ] cada ataque puede reproducirse.
- [ ] nombres de archivos y referencias coherentes.

## 8. Entrenamiento

Cada lab completado debe generar un mini-informe. Una vez por semana, escoger una máquina antigua y reconstruirla **sólo desde tus notas**. Si no puedes, las notas no son suficientemente buenas.

## 9. Reporting bajo tiempo

Durante simulacros:

- notas completas durante la explotación;
- capturas en el instante correcto;
- tabla de flags/evidencias;
- escribir el borrador técnico inmediatamente después de cada objetivo;
- revisar al final, no reconstruir desde memoria.

## Fuentes oficiales

- Reporting Requirements: https://help.offsec.com/hc/en-us/articles/360046787731-OSCP-Reporting-Requirements
- Exam Guide: https://help.offsec.com/hc/en-us/articles/360040165632-OSCP-Exam-Guide
- Authoritative References: https://help.offsec.com/hc/en-us/articles/37192004980628-Authoritative-References-List-OSCP
