# 🔴 RIESGO.SYS — Manual de Operaciones

```
██████╗ ██╗███████╗███████╗ ██████╗  ██████╗     ███████╗██╗   ██╗███████╗
██╔══██╗██║██╔════╝██╔════╝██╔════╝ ██╔═══██╗    ██╔════╝╚██╗ ██╔╝██╔════╝
██████╔╝██║█████╗  ███████╗██║  ███╗██║   ██║    ███████╗ ╚████╔╝ ███████╗
██╔══██╗██║██╔══╝  ╚════██║██║   ██║██║   ██║    ╚════██║  ╚██╔╝  ╚════██║
██║  ██║██║███████╗███████║╚██████╔╝╚██████╔╝    ███████║   ██║   ███████║
╚═╝  ╚═╝╚═╝╚══════╝╚══════╝ ╚═════╝  ╚═════╝    ╚══════╝   ╚═╝   ╚══════╝
```

```
> whoami
  Fernando Contreras // A.k.A Shiru
  eJPT | CEHPC™ | ISO 27001 | Purple Team | Risk Analyst
  Chile 🇨🇱

> cat mission.txt
  Piensa como Atacante, Decide como Negocio.

> ls -la modules/
  drwxr-xr-x  MOD_01  identificacion_escalamiento/
  drwxr-xr-x  MOD_02  comunicar_hacia_arriba/
  drwxr-xr-x  MOD_03  riesgo_en_el_tiempo/
  drwxr-xr-x  MOD_04  decidir_bajo_presion/
  drwxr-xr-x  MOD_05  marco_tecnico/
  drwxr-xr-x  MOD_06  artefactos/
  drwxr-xr-x  MOD_07  frameworks_referencia/

> ./init_charla.sh --no-bullshit --no-frameworks-theory --real-talk
  [OK] Cargando experiencia en terreno...
  [OK] Desactivando modo consultor...
  [OK] Activando modo comunidad...
  [!!] ADVERTENCIA: Puede contener verdades incómodas.
```

---

## `// ANTES DE EMPEZAR`

Este no es un workshop corporativo de esos donde te dan una carpeta, te sientan en un auditorio y te explican ISO 27001 en 200 diapositivas de texto.

Esto es una charla de comunidad.

Entre pares.

Sin filtro corporativo.

Lo que vas a leer acá viene de haber **roto sistemas a propósito**, de haber **construido lo que después tuve que proteger**, y de haber **tenido que convencer a gente que no quería escuchar** en más de una organización, en más de un sector, con más de un presupuesto distinto.

Si buscas el camino fácil, cierra este archivo.

Si buscas la respuesta "correcta" de manual, también.

Pero si quieres entender cómo funciona esto **en la vida real**... bienvenido.

---

## `// ARQUITECTURA DEL MATERIAL`

```
RIESGO.SYS/
├── charla/
│   ├── slides/           → HTML5 ciberpunk para presentar
│   └── notas/            → Lo que dices mientras presentas
│
├── modulos/
│   ├── 01_identificacion_escalamiento.md
│   ├── 02_comunicar_hacia_arriba.md
│   ├── 03_riesgo_en_el_tiempo.md
│   ├── 04_decidir_bajo_presion.md
│   ├── 05_marco_tecnico.md
│   └── 06_crear_artefactos.md
│
├── artefactos/
│   ├── 01_Levantamiento_Activos.xlsx
│   ├── 02_Metodologia_Riesgos.xlsx
│   ├── 03_Matriz_Riesgos.xlsx        ← con CVSS + CWE + OWASP + CIS
│   ├── 04_Seguimiento_Tratamiento.xlsx
│   └── 05_Formulario_Aceptacion.xlsx
│
└── referencia/
    └── 07_frameworks_referencia.md   ← 40+ frameworks mapeados
```

---

## `// MOD_01 — Identificaste algo. ¿Y ahora qué?`

```bash
$ nmap -sV target.empresa.com
$ nikto -h target.empresa.com
$ burpsuite --intercept
# ...
# Encontraste algo. Bien.
# Ahora viene la parte que nadie te enseñó.
```

**El hallazgo es solo el inicio.** Lo que importa es lo que haces con él.

El flujo real — el que de verdad funciona en las organizaciones — tiene seis pasos antes de poder escalar:

```
[VISTE ALGO]
     │
     ▼
[EVIDENCIA] ──── sin evidencia = sospecha, no riesgo
     │
     ▼
[SEVERIDAD EXTERNA] ──── CVSS, vendor advisory, NVD
     │
     ▼
[SEVERIDAD INTERNA] ──── ¿qué le duele AL NEGOCIO?
     │
     ▼
[CLASIFICAR EL ACTIVO] ──── info / tecnológico / físico / humano / IA
     │
     ▼
[¿QUIÉN ES EL DUEÑO?] ──── sin dueño = riesgo flotando
     │
     ▼
[ESCALAR] ──── ahora sí
```

### 🔴 La regla que más se ignora

> `CVSS 9.8 ≠ riesgo crítico para tu organización`

Un 9.8 en un servidor sin internet, sin datos sensibles, usado por el equipo de bodega = **severidad interna BAJA**.

Un 5.4 en el servidor que procesa todos los pagos de la empresa, expuesto a internet, sin parche en 6 meses = **severidad interna CRÍTICA**.

**El scanner no sabe dónde vive el riesgo. Tú sí.**

### El checklist antes de escalar

```
[ ] ¿Tengo evidencia con fecha, sistema y contexto?
[ ] ¿Tengo la severidad externa documentada (fuente)?
[ ] ¿Evalué el impacto en operación, plata, reputación y regulación?
[ ] ¿Identifiqué el activo y su criticidad para el negocio?
[ ] ¿Hay un responsable claro del activo?
[ ] ¿Tengo al menos una recomendación inicial?

→ Si no marcaste todo: no escalas aún. Consigue lo que falta.
→ Si marcaste todo: escalas con criterio, no con miedo.
```

---

## `// MOD_02 — Por qué siempre perdemos la reunión de directorio`

```python
def comunicar_riesgo(hallazgo):
    if audiencia == "gerente":
        return traducir_a_negocio(hallazgo)  # ← esto es lo que no hacemos
    elif audiencia == "jefe_ti":
        return detalle_tecnico(hallazgo)
    elif audiencia == "ciso":
        return impacto_operacional(hallazgo)
```

Tenemos el riesgo identificado. Tenemos la evidencia. Tenemos el análisis.

Y llegamos a la reunión y decimos:

> *"Tenemos una vulnerabilidad CVSSv3 9.8 en el servidor que corre Nginx 1.18.0 con OpenSSL desactualizado y hay un PoC público en GitHub desde hace tres semanas..."*

Y el gerente mira el techo. Y aprueba el mínimo. Y TI queda como el área que siempre pide plata y nunca cuenta qué hizo bien.

### 🔴 Los dos patrones que nos destruyen

**Patrón 1:** `"Todo está malo y necesitamos plata"`  
**Resultado:** Somos un costo fijo.

**Patrón 2:** `Solo aparecemos cuando algo falla`  
**Resultado:** Imagen reactiva. Nadie sabe que existimos cuando todo funciona.

### 💚 Lo que casi nunca hacemos: mostrar los wins

```
REGISTRO DE WINS — Q1 2025
─────────────────────────────────────────────────────────
• Ene: Bloqueamos campaña de phishing dirigida a gerencia
       → 0 credenciales comprometidas

• Feb: Rechazamos proveedor sin controles adecuados
       → evitamos exposición de datos de clientes

• Mar: Migración cloud sin incidentes de seguridad
       → proyecto entregado en plazo y sin brechas

• Abr: Reducimos superficie de ataque en red perimetral
       → 40% menos alertas este trimestre
─────────────────────────────────────────────────────────
ESTO ES TU CAPITAL POLÍTICO. ¿Lo estás usando?
```

### El mismo incidente, tres mensajes distintos

| Quién habla | Audiencia | El mensaje |
|---|---|---|
| Tú (analista) | Tu jefe | `"Logué acceso anómalo al fileserver, aisl&eacute; el equipo, abrí ticket #4821. ¿Escalamos?"` |
| Tu jefe | CISO | `"Acceso no autorizado contenido en < 1 hora. Puede activar notificación regulatoria. Necesito autorización."` |
| CISO | Gerencia | `"Esta mañana bloqueamos un intento de acceso a datos de clientes. El equipo lo detectó rápido. Te aviso antes de que llegue cualquier consulta externa."` |

**El hecho es el mismo. El nivel de detalle cambia. El impacto del mensaje también.**

---

## `// MOD_03 — El servidor que "siempre funcionó así"`

```
[SMTP SERVER — LEGACY]
Función: enviar y recibir documentos tributarios
Regla firewall: ANY → ANY | ALL PORTS | PERMIT
Estado: "siempre ha funcionado bien"
Última revisión: hace años
Responsable formal: nadie
```

Esta historia es real. Y termina con ransomware.

No el día que alguien tocó el servidor.

**Meses después.**

### Los tres nodos encadenados

```
NODO_01: Riesgo sin dueño
─────────────────────────
Lo identifiqué. Lo documenté. Presenté la evidencia.
Respuesta: "sí entendemos, pero no lo toquemos ahora".
Nadie firmó la aceptación del riesgo.
Nadie era responsable.
El riesgo quedó flotando.

         │
         ▼

NODO_02: El trade-off mal resuelto
──────────────────────────────────
Se decidió actuar. Se cerró la exposición.
La mensajería tributaria falló.
Presión inmediata.
Sin análisis, sin plan B:
"vuelvan al estado original".
El riesgo volvió. Ahora legitimado.
Antecedente: "la última vez que lo tocaron, se cayó todo".

         │
         ▼

NODO_03: La consecuencia diferida
───────────────────────────────────
Meses después.
No al día siguiente.
MESES.
Ransomware.
Nadie conectó los puntos.
El tiempo desvinculó causa y efecto.
```

### 🔴 La regla que salva organizaciones

> **El tiempo entre causa y efecto no elimina la relación.**  
> El ransomware de hoy puede ser la decisión de hace seis meses.

### En OT esto se multiplica

En IT, parcheas. Puede doler, pero parcheas.

En OT — PLCs, SCADA, sistemas industriales — no puedes simplemente parchear y listo.

Los ciclos de vida son décadas. Las ventanas de mantenimiento son estrechas. Un error puede parar una línea de producción, contaminar agua, o afectar infraestructura crítica.

En OT, **gestionar el riesgo en el tiempo no es una opción. Es el único modelo posible.**

```
Fecha de vencimiento de todo riesgo aceptado:
┌─────────────────────────────────────────────────────┐
│ Riesgo: [descripción]                               │
│ Decisión: ACEPTAR temporalmente                     │
│ Responsable: [nombre + cargo]                       │
│ Válido hasta: [fecha concreta — no "próximo Q"]     │
│ Trigger de re-evaluación: [qué eventos lo reactivan]│
└─────────────────────────────────────────────────────┘

Sin fecha → no es una decisión. Es un olvido.
```

---

## `// MOD_04 — La pregunta incómoda`

```
CONTEXTO:
Sector financiero.
Incidente crítico → músculo nunca antes visto.
FODA ✓  RACI ✓  BIA/RIA ✓  Controles ✓  Presupuesto ✓

RESULTADO DESPUÉS DE DOS CICLOS:
Riesgo inherente: ALTO
Estado: ROJO

Big Boss pregunta:
"¿Estamos saliendo siempre en rojo?
 Hemos puesto controles, reforzado todo.
 ¿Mi riesgo inherente no puede ser al menos MEDIO?
 ¿Sigue siendo ALTO?"
```

Esa pregunta me cambió la perspectiva.

Y tenía razón en hacerla.

### Las tres respuestas posibles

**A — El riesgo es genuinamente alto**  
Algunos sectores son así. Banco → objetivo permanente. Infraestructura crítica → impacto catastrófico posible.  
No es fracaso. Es contexto.  
Lo que hay que demostrar: que el **riesgo residual** bajó. Eso es diferente.

```
Riesgo INHERENTE = sin controles → puede ser CRÍTICO y no cambiar
Riesgo RESIDUAL  = con controles → eso es lo que tienes que mover
```

**B — El criterio está siendo demasiado ácido**  
```python
if todo_sale_en_rojo_siempre:
    problema = "metodología o criterio, no el entorno"
    consecuencia = "negocio deja de tomarte en serio"
    mensaje = "cuando todo es crítico, nada es crítico"
```

**C — La metodología necesita calibración**  
Una metodología que nunca se revisa se convierte en un ritual.  
Los rituales dan certeza. No necesariamente verdad.

### El stack que reduce el azar

```
Sin proceso = azar con consecuencias corporativas

FODA
(¿dónde estamos parados HOY?)
        ↓
BIA / RIA
(¿qué impacta REALMENTE al negocio?)
        ↓
RACI
(¿QUIÉN decide? ¿QUIÉN ejecuta? ¿QUIÉN asume?)
        ↓
DECISIÓN BAJO PRESIÓN
(ahora sí — con contexto, no con adrenalina)
```

### La escala que define dónde estás

```
REACTIVO ──────────── PREVENTIVO ──────────── PREDICTIVO
   │                       │                       │
"¿Qué pasó?"          "Puede pasar"           "¿Cuándo?"
Apaga incendios        Controles y            Threat intel
Post-incidente         procesos previos       + datos históricos
                                              + criterio experto
```

**No se salta etapas.** No puedes ser predictivo sin haber pasado por preventivo.

---

## `// MOD_05 — El marco técnico que nadie explica bien`

### Matrices de riesgo — lo que todos hacen mal

```python
# La mayoría de las matrices:
for riesgo in lista_riesgos:
    riesgo.nivel = "CRÍTICO"  # porque "es mejor prevenir"

# El resultado:
# Nadie prioriza nada.
# Todo parece igual de urgente.
# El negocio deja de leer los reportes.
```

Una matriz sin criterio definido es decoración con formato Excel.

Lo que necesita:
- **Probabilidad**: ¿en qué datos se basa ese "probable"? ¿threat intel? ¿histórico? ¿intuición?
- **Impacto**: en términos de negocio, no de TI. Operación, plata, reputación, regulación.
- **Criterio documentado**: que alguien más pueda aplicar la misma escala y llegar al mismo resultado.

### Inventario de activos — el mapa sin el cual navegas de memoria

```
TIPOS DE ACTIVOS:
┌─────────────────┬──────────────────────────────────────────┐
│ Información     │ Datos personales, financieros, contratos │
│ Tecnológicos    │ Servidores, apps, red, endpoints, OT     │
│ Físicos         │ Data center, racks, medios físicos        │
│ Humanos         │ Accesos, comportamiento, cultura          │
│ IA              │ Modelos, pipelines, datos entrenamiento   │
└─────────────────┴──────────────────────────────────────────┘

EL ESLABÓN QUE MÁS FALLA: las personas
No porque sean malas.
Porque el sistema no está diseñado para su error.
```

### Política vs lineamiento vs procedimiento

```
POLÍTICA          → el QUÉ y el POR QUÉ (firma la dirección)
     │
LINEAMIENTO       → el CÓMO en términos generales (criterios)
     │
PROCEDIMIENTO     → el PASO A PASO (quién, cuándo, con qué)
     │
GUÍA              → referencia operacional de apoyo
```

**El error más frecuente:** crear una metodología de 80 páginas cuando la organización necesita un lineamiento de 3 páginas que alguien realmente lea y aplique.

### Certificaciones — la verdad sin adorno

```
¿Necesito ISO 27001?
→ Si necesitas DEMOSTRAR cumplimiento a clientes/reguladores: sí.
→ Si quieres estructurar el programa: no es obligatorio, pero ayuda.
→ La cert es para la ORGANIZACIÓN, no para la persona.

¿Necesito conocer ISO 27005?
→ Si haces gestión de riesgos: SÍ. Es tu metodología de base.
→ ¿Certificarme? No existe cert personal de ISO 27005.

¿Necesito conocer ISO 31000?
→ Si quieres hablar con el negocio en su idioma: SÍ.
→ Es el lenguaje del riesgo corporativo. El CFO lo entiende.

Regla general:
Conocimiento > Certificado.
Experiencia > Conocimiento.
Las tres juntas: eso sí que vale.
```

---

## `// MOD_06 — Artefactos que realmente sirven`

```
v0.1  → Borrador sucio con preguntas abiertas (normal)
v0.2  → Incorpora revisión técnica
v0.N  → Revisiones hasta que cierre brechas
v1.0  → Aprobado. Vigente. Tiene dueño. Tiene fecha.
v1.X  → Cambios menores
v2.0  → Revisión mayor de fondo
```

**Si un documento no pasó por v0.1 y v0.2, probablemente nunca fue revisado.**

La versión cuenta la historia del documento. Esa historia puede salvarte en una auditoría.

### CID — no es solo para los activos del cliente

```
TUS PROPIOS DOCUMENTOS también tienen CID:

Confidencialidad → ¿Quién puede ver este registro de riesgos?
                   (tiene IPs, vulns sin parche, activos críticos)

Integridad       → ¿Cómo sabes que no fue alterado?
                   (versionado, hash, repositorio con historial)

Disponibilidad   → ¿Puedes acceder cuando lo necesitas?
                   (no en el laptop de quien se fue de vacaciones)
```

### La evidencia que se pierde siempre

```
❌ MAL: captura de pantalla de la alerta
✅ BIEN: captura + sistema + fecha + contexto + qué pasó después

❌ MAL: "decidimos en la reunión"
✅ BIEN: acta con asistentes, decisión, responsable, fecha y firma

❌ MAL: "el control está configurado"
✅ BIEN: log del control activo + resultado de prueba + fecha
```

### La pregunta final antes de cerrar cualquier artefacto

```
> ¿Si yo no estuviera mañana, alguien podría
  encontrar este documento y entenderlo?

  [ ] Sí  →  está terminado
  [ ] No  →  no está terminado, aunque tenga firma
```

---

## `// MOD_07 — El mapa completo de frameworks`

Más de 40 frameworks mapeados. Los más importantes:

```
PARA GESTIONAR RIESGOS:
  ISO 31000  →  el lenguaje del negocio
  ISO 27005  →  el proceso específico para SI
  NIST RMF   →  más prescriptivo, útil como referencia
  FAIR       →  cuando necesitas cuantificar en $$$

PARA IMPLEMENTAR CONTROLES:
  ISO 27002  →  el catálogo de 93 controles
  CIS v8     →  priorizado — empieza por IG1
  NIST 800-53 → el más completo (contexto federal)

PARA AMENAZAS Y VULNERABILIDADES:
  MITRE ATT&CK →  cómo atacan de verdad
  CVE/CVSS     →  severidad técnica (externa)
  CWE          →  causa raíz de la vulnerabilidad
  OWASP Top10  →  si tienes apps web, es obligado

PARA CLOUD:
  ISO 27017    →  responsabilidad compartida
  ISO 27018    →  PII en cloud

PARA OT/INDUSTRIAL:
  IEC 62443    →  el estándar. Sin alternativa seria.
  NERC CIP     →  si tocas infraestructura eléctrica

PARA IA:
  ISO 42001    →  el SGAI — gestión responsable de IA
  OWASP LLM    →  si tienes apps con LLMs
  NIST AI RMF  →  análisis de riesgos específico de IA
  EU AI Act    →  regulación — si operas en Europa

PARA DEMOSTRAR CUMPLIMIENTO:
  ISO 27001    →  mercado global, certificable
  SOC 2        →  mercado americano, reporte de auditoría
  PCI DSS      →  si tocas pagos con tarjeta
  HIPAA        →  si tocas datos de salud en EE.UU.
```

---

## `// ARTEFACTOS INCLUIDOS`

Cinco planillas semi-automáticas con validaciones, fórmulas y datos de ejemplo:

### `01_Levantamiento_Activos.xlsx`
```
HOJAS:
├── Físicos      → instalaciones, racks, hardware, medios
├── Documentos   → políticas, contratos, PI, regulados
├── Tecnología   → servidores, red, apps, cloud, OT
│                  + columnas CVSS, CWE, CIS Controls
├── Humanos      → accesos, phishing, riesgo, CIS 14
└── AI           → modelos, pipelines, OWASP LLM, CIS

INCLUYE:
✓ Validaciones desplegables en columnas clave
✓ Triada CID por activo tecnológico
✓ Factor humano como activo de riesgo
✓ Activos de IA con supervisión humana y OWASP LLM
```

### `02_Metodologia_Riesgos.xlsx`
```
HOJAS:
├── Marco ISO 27005 → 8 fases completas
├── Criterios     → probabilidad e impacto 1-5 con colores
├── Tratamiento   → mitigar/aceptar/transferir/evitar/compartir
├── Roles         → quién decide qué y hasta qué nivel
├── Glosario      → 18 términos clave definidos
└── Mapeo FW      → cómo CVSS, CWE, OWASP, CIS encajan
                   en cada fase ISO 27005

INCLUYE:
✓ Preguntas abiertas para resolver antes de v1.0
✓ Tabla de decisión por nivel de riesgo
✓ Mapeo completo frameworks ↔ fases del proceso
```

### `03_Matriz_Riesgos.xlsx`
```
HOJAS:
├── Registro     → 8 riesgos de muestra
│                  columnas: CVE, CVSS score, CWE,
│                  OWASP Top10, SAMM, CIS Control+subcontrol
│                  riesgo inherente/residual con fórmulas
│                  nivel calculado automático
├── Matriz 7x7   → probabilidad × impacto con colores
│                  + calculadora integrada
├── Amenazas     → 18 amenazas con MITRE ATT&CK,
│                  CVSS típico, CIS, OWASP AI
└── OWASP SAMM   → evaluación de madurez 0→3
                   con CIS y CWE por práctica

INCLUYE:
✓ Fórmulas automáticas de nivel de riesgo
✓ Colores condicionales por severidad
✓ SAMM con promedio de madurez calculado
✓ Tabla completa de amenazas con referencias cruzadas
```

### `04_Seguimiento_Tratamiento.xlsx`
```
HOJAS:
├── Seguimiento  → 8 tratamientos de muestra
│                  con CVE, CWE, OWASP, CIS por plan
│                  % avance, evidencias, estado coloreado
├── KPIs         → indicadores con fórmulas automáticas
│                  incluyendo cobertura de frameworks
└── Log cambios  → trazabilidad de decisiones

INCLUYE:
✓ Colores por estado (verde/azul/naranja/rojo)
✓ KPIs automáticos: % completado, % vencido, cobertura CIS
✓ Log de cambios para trazabilidad en auditorías
```

### `05_Formulario_Aceptacion.xlsx`
```
HOJAS:
├── Formulario   → campo a campo con instrucciones
│                  firmas: Dueño Negocio + CISO + Gerencia
│                  (Gerencia requerida para ALTO y CRÍTICO)
├── Registro     → histórico de aceptaciones con estados
└── Clasificación → cuándo SÍ y cuándo NO aceptar
                   mapa CVSS → ISO 27005 → decisión
                   controles CIS compensatorios

INCLUYE:
✓ Criterios formales de aceptación
✓ Situaciones donde NO se puede aceptar
✓ Tabla CVSS → nivel → SLA → ¿aceptable?
✓ Registro histórico con vigencia y resultado
```

---

## `// FRAMEWORKS — EL MAPA COMPLETO`

```
07_frameworks_referencia.md — 40+ frameworks organizados en:

1. Gestión de Riesgos Base
   ISO 31000, ISO 27005, NIST RMF, NIST CSF 2.0, FAIR

2. Familia ISO 27000
   27001, 27002, 27017, 27018, 27032, 27035, 27701

3. Ciberseguridad Técnica
   CIS v8, MITRE ATT&CK, D3FEND, CVE/NVD, CVSS, CWE, CAPEC

4. Seguridad en Desarrollo
   OWASP Top10 Web/API/LLM, OWASP SAMM, OWASP ASVS, BSIMM

5. Regulaciones
   GDPR, Ley 19.628/21.096 (Chile), PCI DSS v4.0, HIPAA

6. Auditoría
   SOC 1, SOC 2 Tipo I/II, SOC 3

7. Sectores Específicos
   IEC 62443, NERC CIP, TISAX, SWIFT CSCF

8. Inteligencia Artificial
   ISO 42001, EU AI Act, NIST AI RMF

9. Continuidad
   ISO 22301, ISO 22317, NIST SP 800-184
```

---

## `// LO QUE NO SE OLVIDA`

```python
principios = [
    "El riesgo no vive en el scanner — vive en el negocio",
    "Un riesgo aceptado sin documentar es un riesgo sin dueño",
    "El trabajo invisible no construye credibilidad",
    "Cuando todo es crítico, nada es crítico",
    "El tiempo entre causa y efecto no elimina la relación",
    "No gestionar riesgos ES una decisión",
    "Más control ≠ menos riesgo",
    "El impacto no lo define TI — lo define el negocio",
    "Decidir sin proceso es azar",
    "No es eliminar el riesgo — es decidir cómo convivir con él",
]

for p in principios:
    print(f"[!!] {p}")
```

---

## `// CRÉDITOS`

```
AUTOR:
  Fernando Contreras
  A.k.A Shiru
  eJPT | CEHPC™ | ISO 27001 Lead Auditor | Risk Analyst
  Pentesting → Ingeniería → Gobierno de Ciberseguridad
  Chile 🇨🇱

EXPERIENCIA:
  PyMEs | Retail | Banca | Industria OT | Sector Público
  Salud | Infraestructura Crítica | Cloud | Gobierno

DISCLAIMER:
  Esto no es teoría.
  Es lo que he vivido, roto, arreglado y documentado.
  Lo que funciona en mi contexto puede no funcionar en el tuyo.
  Adaptarlo a tu realidad es parte del trabajo.

  La gestión de riesgos no es un producto.
  No es un checklist.
  No es un gasto.

  Es una capacidad organizacional para tomar mejores
  decisiones bajo incertidumbre.

  Y eso no lo resuelve ninguna herramienta.
```

---

## `// CONEXIÓN`

```
> find /redes-sociales/ -name "shiru" -type hacker

  github   → github.com/[shiru]
  linkedin → linkedin.com/in/fernando-c-bb72881a4
  comunidad → siempre open to chat

> echo "¿Preguntas? ¿Casos de uso? ¿Discrepancias?"
  happy to talk. ese es el punto de una charla de comunidad.

> shutdown -h now
  [OK] Guardando contexto...
  [OK] Cerrando sesión...
  [!!] El riesgo sigue ahí. Mañana seguimos.
```

---

```
╔══════════════════════════════════════════════════════════════╗
║                                                              ║
║   RIESGO.SYS v1.0 — Piensa como Atacante, Decide como       ║
║   Negocio                                                    ║
║                                                              ║
║   "El riesgo siempre va a existir.                          ║
║    La diferencia no está en eliminarlo.                      ║
║    Está en cómo decides convivir con él."                    ║
║                                                              ║
║   — Fernando Contreras / Shiru                               ║
║                                                              ║
╚══════════════════════════════════════════════════════════════╝
```
