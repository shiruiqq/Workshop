# 05 — El Marco Técnico que Nadie Te Explica Bien

> **Piensa como Atacante, Decide como Negocio**  
> Parte 5 — *Matrices, activos, metodología y el eterno debate de las certificaciones*

---

## 🎯 De qué va esto

Antes de identificar un riesgo, escalarlo o comunicarlo hacia arriba, necesitas tener algo construido.  
No tiene que ser perfecto. Pero tiene que existir.

Este módulo es sobre los cimientos:  
qué herramientas usas, qué inventarías, cómo lo documentas y qué necesitas saber formalmente.

---

## 🟥 1. ¿Qué es una matriz de riesgos y por qué la mayoría está mal hecha?

Una **matriz de riesgos** es una herramienta para visualizar y priorizar riesgos según dos variables:

```
PROBABILIDAD (eje Y) × IMPACTO (eje X) = NIVEL DE RIESGO
```

### El modelo básico — 5×5

| | Insignificante | Menor | Moderado | Mayor | Catastrófico |
|---|---|---|---|---|---|
| **Casi seguro** | Medio | Alto | Alto | Crítico | Crítico |
| **Probable** | Bajo | Medio | Alto | Alto | Crítico |
| **Posible** | Bajo | Medio | Medio | Alto | Alto |
| **Improbable** | Bajo | Bajo | Medio | Medio | Alto |
| **Raro** | Bajo | Bajo | Bajo | Medio | Medio |

### El problema real con las matrices

No es el modelo. Es cómo se llena.

**Antipatrón 1 — Todo termina siendo "Alto" o "Crítico"**  
Cuando el criterio no está definido, el analista llena según su intuición o su nivel de ansiedad del día.  
Resultado: nadie prioriza nada porque todo parece igual de urgente.

**Antipatrón 2 — La probabilidad es un número inventado**  
¿En qué datos se basa ese "probable"? ¿Incidentes históricos? ¿Threat intelligence? ¿Nada?  
Si la probabilidad no tiene una fuente, es opinión disfrazada de método.

**Antipatrón 3 — El impacto es técnico, no de negocio**  
"Impacto alto porque el servidor es crítico" no es lo mismo que "impacto alto porque si cae este servidor se detienen todas las ventas por 6 horas".  
Uno lo entiende TI. El otro lo entiende el CFO.

> **La matriz no es el problema. La falta de criterio detrás de ella sí lo es.**

### ¿Cuándo sirve una matriz?

- Para comunicar riesgos de forma visual a audiencias no técnicas
- Para facilitar decisiones de priorización cuando hay muchos riesgos activos
- Para llevar un registro de evolución en el tiempo

### ¿Cuándo no sirve?

- Como sustituto de un análisis real
- Cuando los criterios de probabilidad e impacto no están definidos y documentados
- Cuando se usa para justificar decisiones que ya se tomaron antes de llenarla

---

## 💾 2. El inventario de activos — dónde vive tu riesgo

No puedes gestionar el riesgo de lo que no sabes que tienes.  
El inventario de activos es el mapa. Sin mapa, navegas de memoria.

### Tipos de activos

#### Activos de información (lo que se guarda, procesa o transmite)

| Tipo | Ejemplos |
|---|---|
| Datos personales | RUT, nombre, dirección, correo, biometría |
| Datos financieros | Cuentas, transacciones, nómina |
| Datos críticos del negocio | Contratos, propiedad intelectual, fórmulas |
| Credenciales | Usuarios, contraseñas, tokens, certificados |
| Configuraciones | Backups de dispositivos, scripts de automatización |

#### Activos tecnológicos (lo que procesa o transporta la información)

| Tipo | Ejemplos |
|---|---|
| Infraestructura | Servidores, storage, cloud instances |
| Red | Firewalls, switches, VPN, segmentos OT |
| Aplicaciones | ERP, CRM, APIs, microservicios |
| Endpoints | Laptops, móviles, workstations |
| OT/ICS | PLCs, SCADA, sensores industriales |

#### Activos físicos (el contenedor del resto)

| Tipo | Ejemplos |
|---|---|
| Instalaciones | Data centers, oficinas, salas de servidores |
| Hardware físico | UPS, racks, equipos sin conectividad |
| Medios físicos | USBs, discos externos, papel impreso |

### El eslabón que más falla: la gestión humana

Aquí es donde la mayoría pone el foco técnico y se olvida de algo evidente:

> **Las personas no son un activo. Son el factor de riesgo más complejo que tienes.**

No porque sean malas. Sino porque:

- Toman decisiones bajo presión sin contexto suficiente
- Tienen acceso a cosas que no necesitan tener
- Cometen errores que ningún firewall puede anticipar
- Son el vector principal de la mayoría de los incidentes reales

**Lo que se gestiona mal en las organizaciones:**

| Situación | Riesgo real |
|---|---|
| Empleado con acceso excesivo | Insider threat, accidente con consecuencias críticas |
| Offboarding mal gestionado | Credenciales activas de ex-empleados |
| Falta de entrenamiento | Phishing, ingeniería social, errores de configuración |
| Cultura de "yo no soy el responsable" | Riesgos sin dueño, decisiones sin respaldo |
| Shadow IT | Activos fuera del inventario que nadie monitorea |

> El inventario de activos que no incluye cómo las personas interactúan con ellos está incompleto.

### Atributos mínimos por activo

Cuando inventarías un activo, no basta con el nombre. Necesitas:

```
- Identificador único
- Nombre y descripción
- Tipo (información / tecnológico / físico)
- Clasificación (público / interno / confidencial / secreto)
- Dueño de negocio (no el de TI — el que responde si falla)
- Dueño técnico (quien lo administra)
- Criticidad para la operación (alta / media / baja)
- Ubicación (on-premise / cloud / híbrido)
- Fecha de última revisión
```

---

## 📋 3. ¿Construyo una metodología, un lineamiento, una política o un procedimiento?

Esta es la pregunta que más confusión genera — y donde más documentos inútiles se producen.

La respuesta corta: **dependen uno del otro. No son lo mismo y no son intercambiables.**

### La jerarquía documental

```
POLÍTICA
(el qué y el por qué — decisión de negocio)
     │
     ▼
ESTÁNDAR / LINEAMIENTO
(el cómo en términos generales — criterios técnicos)
     │
     ▼
PROCEDIMIENTO
(el paso a paso — quién hace qué, cuándo y cómo)
     │
     ▼
GUÍA / INSTRUCTIVO
(referencia operacional — opcional, de apoyo)
```

### ¿Qué es cada uno en la práctica?

**Política:**  
Documento corto. Establece la intención de la organización. Lo firma la dirección.  
Ejemplo: *"La organización gestionará los riesgos tecnológicos de forma sistemática para proteger la continuidad operacional."*  
No tiene pasos. No tiene detalles técnicos. Tiene dirección y compromiso.

**Lineamiento / Estándar:**  
Traduce la política a criterios aplicables.  
Ejemplo: *"Todos los activos críticos deben tener un dueño asignado, una evaluación de riesgo anual y controles documentados."*  
Tiene criterios pero no tiene procedimientos paso a paso.

**Procedimiento:**  
El instructivo operacional. Quién, qué, cuándo, cómo y con qué herramienta.  
Ejemplo: *"Proceso de gestión de incidentes de seguridad: 1) Detección y registro, 2) Clasificación..."*  
Este es el que más necesita mantenimiento porque cambia con la operación.

**Metodología:**  
Es el marco conceptual que sostiene los procedimientos.  
Ejemplo: usar ISO 27005 o NIST RMF como base para evaluar riesgos.  
No se crea desde cero — se adopta, se adapta y se documenta la adaptación.

### ¿Quién es el dueño del documento?

Este es el punto que más se evade. Y es crítico.

| Documento | Dueño ideal | Por qué |
|---|---|---|
| Política | Dirección / Gerencia General | Necesita autoridad para que se cumpla |
| Lineamiento | CISO / Gerente de Seguridad | Criterio técnico con respaldo directivo |
| Procedimiento | Área operativa (TI, Seguridad, etc.) | Quienes lo ejecutan deben poder actualizarlo |
| Metodología | CISO / Comité de Riesgos | Debe tener visión transversal |

> **Un procedimiento sin dueño es un documento que nadie actualiza, nadie sigue y nadie sabe si existe.**

### El error más común

Crear una metodología compleja de 80 páginas cuando la organización necesita primero un lineamiento de 3 páginas que alguien realmente lea.

Empieza por lo mínimo viable que puedas sostener operacionalmente.  
Un buen lineamiento simple, aplicado, es infinitamente más valioso que una metodología perfecta que nadie usa.

---

## 🎓 4. ¿Necesito certificarme? ¿Qué normas tengo que conocer?

La respuesta honesta: **depende de qué quieres hacer con eso.**

### Las normas más relevantes en gestión de riesgos

#### ISO 27001 — El estándar de gestión de seguridad de la información

**¿Qué es?** Un estándar certificable que define los requisitos para un Sistema de Gestión de Seguridad de la Información (SGSI).

**¿Necesito certificarme?**  
Solo si tu organización necesita demostrar cumplimiento a clientes, reguladores o socios.  
La certificación es para la organización, no para la persona.

**¿Qué valor tiene conocerla como profesional?**  
Alto. Te da el marco de controles (Anexo A), el lenguaje común del sector y la estructura para armar un SGSI.  
Pero conocerla no requiere certificación — requiere estudio y aplicación.

#### ISO 27005 — Gestión de riesgos de seguridad de la información

**¿Qué es?** La norma que complementa a ISO 27001 con el proceso específico de evaluación y tratamiento de riesgos.

**¿Necesito certificarme?**  
No existe certificación personal de ISO 27005. Es una guía, no un estándar certificable.

**¿Qué valor tiene?**  
Alto si haces gestión de riesgos tecnológicos. Define el proceso: identificación, análisis, evaluación, tratamiento, aceptación y revisión.  
Es la base metodológica que te da el "cómo" cuando la 27001 solo te dice el "qué".

#### ISO 31000 — Gestión de riesgos (marco general)

**¿Qué es?** El estándar de gestión de riesgos para cualquier tipo de organización, no específico de seguridad de la información.

**¿Necesito certificarme?**  
No existe certificación personal de ISO 31000.

**¿Qué valor tiene?**  
Te da el lenguaje y el marco para hablar de riesgo con el negocio, no solo con TI.  
Si quieres conectar ciberseguridad con gestión de riesgos corporativos, esta es la norma que habla el mismo idioma que el CFO o el directorio.

### El mapa de decisión

```
¿Quieres trabajar en gestión de riesgos de seguridad?
     │
     ├── Lee ISO 27005 + ISO 31000 (no requiere certificación)
     │
¿Tu organización quiere demostrar cumplimiento a clientes?
     │
     ├── Considera implementar ISO 27001 (certificación organizacional)
     │
¿Quieres validar tu conocimiento personalmente?
     │
     ├── ISO 27001 Lead Implementer / Lead Auditor (Bureau Veritas, BSI, etc.)
     ├── CISM (ISACA) — más orientado a gestión
     └── CRISC (ISACA) — específico en riesgo de TI
```

### Lo que nadie te dice sobre las certificaciones

- Una certificación valida que conoces el marco. No valida que sabes aplicarlo.
- La experiencia en terreno pesa más que el certificado en la mayoría de los contextos reales.
- Conocer bien ISO 27005 sin certificación vale más que tener el certificado sin haber gestionado un riesgo real nunca.
- El valor real de certificarse es el proceso de estudio y la señal hacia el mercado, no el papel.

> **Certifícate cuando tenga sentido para tu contexto. Aprende siempre.**

---

## 🔑 Lo que debes llevarte de este módulo

1. **Una matriz sin criterios es decoración.** Define primero cómo se mide probabilidad e impacto, luego llénala.
2. **El inventario incompleto es el inventario inútil.** Si no incluye dueños, criticidad y la dimensión humana, no sirve como base de gestión.
3. **Las personas son el factor de riesgo más complejo.** No porque fallen — sino porque el sistema no está diseñado para su error.
4. **Antes de una metodología, necesitas un lineamiento.** Empieza por lo que puedas sostener.
5. **El dueño del documento no es TI.** Si TI es el único responsable, el documento no tiene autoridad para cambiar el comportamiento del negocio.
6. **ISO 27005 e ISO 31000 son lectura obligada.** Certificación, opcional según contexto.

---

> *Siguiente → README 06: Crear artefactos — borradores, validaciones, CID y el arte de guardar evidencia correctamente*

---

*Piensa como Atacante, Decide como Negocio — Charla de comunidad por Fernando Contreras / Shiru*
