# 01 — Identificación y Escalamiento de Riesgo

> **Workshop: Gestión de Riesgos en el Mundo Real**  
> Módulo 1 de N — *Del hallazgo a la decisión*

---

## 🎯 Objetivo de este módulo

Que el equipo técnico entienda qué hacer **desde el momento en que identifica un riesgo** hasta que llega a quien puede tomar una decisión.

No es teoría. Es el camino real.

---

## 🔍 ¿De dónde viene el riesgo?

El riesgo no aparece solo en un scanner.  
Aparece cuando alguien lo ve.

| Fuente | Ejemplo |
|---|---|
| Herramienta técnica | Nessus, Burp, Qualys, SIEM alerta |
| Conocimiento experto | "Esto no debería estar así" |
| Ethical hacking / pentest | Hallazgo en ejercicio controlado |
| Incidente previo | "Ya nos pasó algo parecido" |
| Cambio en el entorno | Nuevo proveedor, migración, actualización |

> **Regla clave:** Si lo ves y no lo documentas, no existe.

---

## 🔁 El flujo completo

```
IDENTIFICACIÓN
      │
      ▼
¿Tenemos un proceso?
  ├── Sí → seguirlo
  └── No → documentar igual (⚠️ riesgo de gobierno)
      │
      ▼
¿Tenemos evidencia?
  ├── Sí → adjuntarla
  └── No → conseguirla antes de escalar
      │
      ▼
SEVERIDAD EXTERNA
(Lo que dice el mundo técnico)
      │
      ▼
SEVERIDAD INTERNA
(Lo que le importa al negocio)
      │
      ▼
CLASIFICACIÓN DEL ACTIVO
(¿Qué es? ¿Qué valor tiene?)
      │
      ▼
¿Tiene responsable?
  ├── TI → escalar internamente
  ├── Negocio → involucrar al área dueña
  └── Nadie → problema de gobierno (⚠️ escalar igual)
      │
      ▼
ESCALAMIENTO FORMAL
```

---

## 🔴 Paso 1 — ¿Tenemos un proceso?

Antes de hacer cualquier cosa, la primera pregunta es si existe un camino definido.

| Situación | Qué hacer |
|---|---|
| Existe proceso | Seguirlo. Documentar que lo seguiste. |
| No existe proceso | Igual documentas. Igual escalas. Y luego propones el proceso. |

> **Por qué importa:** Si no hay proceso y algo sale mal, la pregunta será "¿por qué no avisaste?" — la respuesta siempre debe ser "sí avisé, acá está la evidencia".

---

## 📎 Paso 2 — ¿Tenemos evidencia?

Sin evidencia, no hay riesgo. Hay una sospecha.

**Qué cuenta como evidencia:**
- Captura de pantalla con fecha y contexto
- Log exportado con marca de tiempo
- Reporte de herramienta (con parámetros usados)
- Correo o registro que demuestre el hallazgo

**Qué NO es evidencia suficiente:**
- "Vi algo raro en el sistema"
- Un hallazgo sin fecha ni contexto
- Una alerta sin investigar

> **Regla:** Si no puedes mostrarlo, no puedes escalarlo.

---

## 🌐 Paso 3 — Severidad Externa

Es la clasificación que viene de afuera: del vendor, del mundo técnico, de la comunidad.

**Fuentes comunes:**
- **CVSSv3 / CVSSv4** — puntuación técnica estándar
- **Vendor Advisory** — lo que dice el fabricante
- **NVD / CVE** — base de datos pública
- **CVSS-B (Base Score)** — sin contexto de tu entorno

**Escala de referencia:**

| Rango CVSS | Clasificación |
|---|---|
| 9.0 – 10.0 | Crítico |
| 7.0 – 8.9 | Alto |
| 4.0 – 6.9 | Medio |
| 0.1 – 3.9 | Bajo |

> ⚠️ **Trampa frecuente:** Un CVSS 9.8 no significa que sea catastrófico para TU organización. Es el punto de partida, no la decisión.

---

## 🏢 Paso 4 — Severidad Interna *(el paso que cambia todo)*

Aquí es donde el riesgo técnico se convierte en riesgo de negocio.

**Las 4 dimensiones de impacto interno:**

| Dimensión | Pregunta clave |
|---|---|
| **Operación** | ¿Para la operación si esto se explota? ¿Cuánto tiempo? |
| **Dinero** | ¿Cuánto cuesta si ocurre? ¿Multas, pérdida de venta, recuperación? |
| **Reputación** | ¿Sale en los medios? ¿Afecta la confianza del cliente? |
| **Regulación** | ¿Hay un marco regulatorio que nos obliga a actuar? |

**Ejemplo de contraste externo vs interno:**

> *Sistema con CVSSv3 9.8 (Crítico externo)*  
> — Sin exposición a internet  
> — Sin datos sensibles  
> — Usado solo por el equipo de bodega  
> — Con compensating controls activos  
>
> **Severidad interna → Media o Baja**

> *Sistema con CVSSv3 5.4 (Medio externo)*  
> — Expuesto a internet  
> — Procesa pagos en tiempo real  
> — Afecta a todos los clientes  
>
> **Severidad interna → Crítica**

> **Regla:** El impacto no lo define el scanner. Lo define el negocio.

---

## 💾 Paso 5 — Clasificación del Activo

Antes de escalar, hay que saber exactamente qué está en riesgo.

### Activo de Información
Datos, registros, configuraciones, documentos.

| Tipo | Ejemplos |
|---|---|
| Datos personales | RUT, nombre, dirección, correo |
| Datos financieros | Números de cuenta, transacciones |
| Datos críticos del negocio | Contratos, propiedad intelectual |
| Credenciales | Usuarios, contraseñas, tokens |

### Activo Tecnológico
Infraestructura, sistemas, servicios.

| Tipo | Ejemplos |
|---|---|
| Servidor / infraestructura | On-premise, cloud, contenedor |
| Aplicación | Web, móvil, API, microservicio |
| Red | Firewall, switch, VPN, segmento |
| Endpoint | Laptop, workstation, dispositivo móvil |
| OT/ICS | PLC, SCADA, sensor industrial |

**Pregunta adicional clave:**  
¿Cuál es la criticidad de este activo para la operación?

| Criticidad | Definición |
|---|---|
| Alta | Si falla, para la operación |
| Media | Si falla, degrada el servicio |
| Baja | Si falla, impacto marginal |

---

## 👤 Paso 6 — ¿Quién es el responsable?

El último paso antes de escalar: identificar a quién le pertenece el problema.

| Escenario | Acción |
|---|---|
| Responsable TI identificado | Escalar internamente con evidencia |
| Responsable de negocio (área dueña) | Involucrar al área antes de escalar arriba |
| Responsable compartido (TI + Negocio) | Coordinar ambos en el escalamiento |
| Sin responsable claro | Escalar igual + marcar como problema de gobierno |

> ⚠️ **Si nadie asume el riesgo, eso también es un riesgo.**  
> Y alguien tiene que documentarlo.

---

## 📋 Checklist de escalamiento

Antes de escalar, valida que tienes:

- [ ] Descripción clara del hallazgo (qué encontré, cuándo, cómo)
- [ ] Evidencia adjunta (log, captura, reporte)
- [ ] Severidad externa documentada (fuente + puntuación)
- [ ] Severidad interna evaluada (impacto en negocio)
- [ ] Activo afectado identificado y clasificado
- [ ] Responsable del activo identificado
- [ ] Recomendación inicial (aunque sea preliminar)

---

## ❌ Anti-patrones frecuentes

| Lo que hacemos | Por qué es un problema |
|---|---|
| Escalar sin evidencia | Nadie puede tomar una decisión |
| Usar CVSS como decisión final | El contexto del negocio no está en el CVSS |
| No identificar al dueño del activo | El riesgo queda flotando sin dueño |
| No documentar cuando no hay proceso | Si algo pasa, no hay trazabilidad |
| Escalar todo como "crítico" | Se pierde credibilidad y se genera ruido |

---

## 🔑 Lo que debes llevarte de este módulo

1. **Identificar no es suficiente** — hay que documentar y evidenciar
2. **La severidad externa es el punto de partida**, no la decisión
3. **La severidad interna es la que importa** al momento de escalar
4. **El activo define el contexto** del riesgo
5. **Sin responsable, hay un problema de gobierno** — igual se escala

---

> *Siguiente módulo → Cómo comunicar el riesgo hacia arriba: hablar en el idioma del negocio*

---

*Workshop: Gestión de Riesgos en el Mundo Real — Módulo 01*
