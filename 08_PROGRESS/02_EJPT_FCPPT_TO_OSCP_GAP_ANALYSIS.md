# Gap Analysis — eJPT / ruta FCPPT-eCPPT → OSCP+

## Respuesta corta

Sí: una base eJPT y una preparación centrada en Active Directory son **muy aprovechables** para OSCP+. El valor real está en reutilizar fundamentos y elevarlos desde un nivel guiado a un nivel autónomo y cronometrado.

> Las denominaciones de certificaciones de INE pueden cambiar con el tiempo; aquí se usa “ruta FCPPT/eCPPTv3” como referencia a la formación práctica intermedia/avanzada que estás siguiendo.

## Matriz de transferencia

| Conocimiento previo | Transferencia a OSCP | Qué falta llevar a nivel OSCP |
|---|---:|---|
| Redes TCP/IP | Alta | velocidad de lectura de superficie y routing |
| Nmap | Alta | full scans + interpretación, no sólo sintaxis |
| Web básica | Alta | enumeración manual y ataques comunes sin walkthrough |
| SMB | Alta | combinar shares, credenciales, Windows y AD |
| Shells | Alta | estabilización, transferencias, Windows/Linux |
| Metasploit | Media | depender menos de automatización y respetar reglas de examen |
| Linux | Alta | PrivEsc sistemático |
| Windows | Alta | PrivEsc sistemático, ACLs, servicios, tokens |
| Active Directory | Muy alta | cadenas completas, BloodHound, Kerberos, movimiento, pivoting |
| Kerberos | Muy alta | elegir técnica por evidencia y documentar el camino |
| BloodHound | Muy alta | interpretar edges y convertirlos en decisiones concretas |
| Cracking offline | Media/Alta | priorización y límites de tiempo |
| Reporting | Variable | convertir notas técnicas en informe reproducible |

## Solapamiento conceptual estimado

Esta tabla es una **estimación de estudio**, no un dato oficial de OffSec ni INE.

| Área OSCP | Posible base previa | Riesgo de gap |
|---|---|---|
| Enumeración | fuerte | medio |
| Explotación inicial | fuerte | medio |
| Linux PrivEsc | media | alto |
| Windows PrivEsc | media | alto |
| Active Directory | creciente/fuerte | medio |
| Pivoting | media | medio/alto |
| Reporting | variable | alto |
| Simulacro bajo tiempo | baja | muy alto |

## El salto mental

### eJPT-style

```text
“Reconozco la técnica y sé utilizar las herramientas.”
```

### OSCP-style

```text
“Sin pistas, decido qué enumerar, justifico cada hipótesis, adapto lo necesario, consigo acceso, escalo, cambio de rumbo cuando toca y dejo un informe reproducible.”
```

## Qué aprovechar inmediatamente

### De eJPT
- redes;
- Nmap;
- web básica;
- servicios;
- shells;
- lógica de pentest.

### De tu estudio de AD
- dominios/DC;
- Kerberos;
- LDAP;
- SMB;
- usuarios/grupos;
- AS-REP/Kerberoasting a nivel de laboratorio;
- Impacket;
- NetExec;
- BloodHound;
- PowerView;
- WinRM.

## Qué añadir ya

Prioridad recomendada:

1. Windows PrivEsc.
2. Linux PrivEsc.
3. Reporting.
4. AD encadenado de principio a fin.
5. Pivoting.
6. Web manual profunda.
7. Adaptación de PoCs.
8. Simulacros.

## Test de transferencia

Para cada técnica que ya conozcas, no vuelvas a “estudiarla” desde cero. Haz esta prueba:

- ¿puedo explicarla en 2 minutos?
- ¿puedo reconocer sus precondiciones?
- ¿puedo usarla en un lab sin copiar una receta?
- ¿sé qué output espero?
- ¿sé qué hacer si falla?
- ¿puedo documentarla?

Si respondes “sí” a 5–6 → pasa a práctica.

Si respondes “sí” a 3–4 → repaso dirigido.

Si respondes “sí” a 0–2 → estudiar capítulo completo.

## Resultado esperado

Tu ventaja no es “tener otra certificación”, sino llegar a PEN-200 sin gastar semanas reaprendiendo fundamentos. El tiempo ahorrado debe reinvertirse en **PrivEsc, AD, reporting y simulacros**, que son los componentes que más diferencian una base junior de una preparación OSCP sólida.
