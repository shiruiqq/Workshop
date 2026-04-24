# 06 — Crear Artefactos que Realmente Sirvan

> **Piensa como Atacante, Decide como Negocio**  
> Parte 6 — *Borradores, validaciones, CID, versionado y el arte de guardar evidencia*

---

## 🎯 De qué va esto

En gestión de riesgos, un artefacto es cualquier documento, registro o entregable que formaliza una decisión, un análisis o un control.

El problema no es crearlos. El problema es crearlos bien.

Un artefacto mal construido tiene el mismo valor que uno que no existe: cuando lo necesitas para defenderte, para auditar o para demostrar que hiciste tu trabajo, no sirve.

---

## ✏️ 1. Primero los borradores — por qué empezar en sucio es la única forma correcta

El error más común al crear documentación de riesgos es intentar producir el documento final desde el inicio.

No funciona así. Nunca.

### El ciclo real de un artefacto

```
BORRADOR v0.1
(sucio, incompleto, con preguntas abiertas)
        │
        ▼
REVISIÓN INTERNA
(el equipo técnico lo cuestiona)
        │
        ▼
BORRADOR v0.2 → v0.N
(incorpora correcciones, cierra brechas)
        │
        ▼
VALIDACIÓN FORMAL
(las partes interesadas lo revisan y aprueban)
        │
        ▼
VERSIÓN APROBADA v1.0
(entra en vigor, tiene dueño, tiene fecha)
        │
        ▼
CICLO DE REVISIÓN
(cada X tiempo o ante cambios de contexto)
```

### Lo que va en un borrador v0.1

No te paralices buscando la perfección.  
Un borrador funcional necesita al menos:

- **Alcance:** ¿de qué estamos hablando y qué queda fuera?
- **Objetivo:** ¿para qué sirve este documento?
- **Supuestos:** ¿qué estamos asumiendo que es verdad?
- **Preguntas abiertas:** lo que aún no sabes y necesitas resolver

> **Las preguntas abiertas son parte del borrador, no una señal de que no está listo.**  
> Un borrador que oculta las dudas es peor que uno que las explicita.

### Tipos de artefactos más comunes en gestión de riesgos

| Artefacto | Para qué sirve |
|---|---|
| Inventario de activos | Base de todo — sin esto no hay análisis |
| Matriz de riesgos | Visualizar y priorizar |
| Registro de riesgos (risk register) | Seguimiento y trazabilidad en el tiempo |
| Plan de tratamiento | Qué se va a hacer con cada riesgo y cuándo |
| Política / lineamiento / procedimiento | Marco normativo interno |
| Informe de evaluación | Resultado de un análisis puntual |
| Acta de aceptación de riesgo | Formalización de decisión de negocio |
| BIA (Business Impact Analysis) | Impacto de interrupción de procesos críticos |
| Checklist de controles | Verificación operacional periódica |

---

## ✅ 2. Las validaciones — quién tiene que firmar y por qué importa

Un documento sin validación es una opinión con formato bonito.

La validación no es solo una firma. Es el proceso mediante el cual las partes interesadas:

1. **Confirman que el contenido es correcto** (exactitud técnica y de negocio)
2. **Confirman que están de acuerdo con las decisiones** que implica
3. **Asumen su parte de responsabilidad** sobre lo que el documento establece

### Los tres niveles de validación

#### Nivel 1 — Revisión técnica

**Quién:** El equipo que va a ejecutar o implementar lo que describe el documento.  
**Para qué:** Detectar errores técnicos, inconsistencias o pasos imposibles de seguir en la práctica.  
**Resultado esperado:** El documento es técnicamente correcto y ejecutable.

#### Nivel 2 — Revisión de negocio

**Quién:** El dueño del proceso o activo afectado (no TI — el área de negocio).  
**Para qué:** Confirmar que el impacto está bien dimensionado y que las decisiones de tratamiento son viables operacionalmente.  
**Resultado esperado:** El negocio reconoce el riesgo y valida la respuesta propuesta.

#### Nivel 3 — Aprobación formal

**Quién:** La persona con autoridad para tomar la decisión final (CISO, Gerencia, Directorio según el nivel de riesgo).  
**Para qué:** Darle vigencia al documento y asignar responsabilidades formales.  
**Resultado esperado:** Firma, fecha y versión aprobada. Sin eso, no existe formalmente.

### El acta de aceptación de riesgo — el artefacto más ignorado

Cuando el negocio decide **no tratar** un riesgo identificado, eso tiene que quedar documentado.

No es un formulario burocrático. Es la diferencia entre:

> *"Nadie avisó que había un riesgo"*

y

> *"El riesgo fue identificado, comunicado y el área aceptó convivir con él bajo estas condiciones y hasta esta fecha."*

**Contenido mínimo de un acta de aceptación:**

```
- Descripción del riesgo
- Severidad evaluada (externa e interna)
- Activo afectado
- Razón por la que se acepta (en lugar de tratarlo)
- Condiciones de la aceptación (controles compensatorios si aplica)
- Fecha de revisión comprometida
- Firma del responsable de negocio que acepta
- Firma del responsable de seguridad que notifica
```

> **Si nadie firma la aceptación del riesgo, nadie lo asumió.**  
> Y los riesgos sin dueño explotan solos.

---

## 🔐 3. Los principios básicos CID — y por qué la versión importa tanto como el contenido

### CID: Confidencialidad, Integridad, Disponibilidad

Son los tres pilares de la seguridad de la información. No son conceptos abstractos — son criterios de clasificación y diseño de controles para cada artefacto que produces.

#### Confidencialidad

> *¿Quién puede ver este documento?*

Un registro de riesgos con vulnerabilidades no corregidas es información sensible.  
Un inventario de activos con IPs y configuraciones es un mapa para un atacante.  
Un informe de BIA revela los procesos más críticos de la organización.

**Lo que debes definir por artefacto:**

| Clasificación | Acceso |
|---|---|
| Público | Cualquiera, sin restricción |
| Interno | Solo personal de la organización |
| Confidencial | Solo las personas con necesidad de saber |
| Restringido / Secreto | Lista explícita de personas autorizadas |

#### Integridad

> *¿Cómo sé que este documento no fue alterado?*

Un artefacto de riesgos sin integridad garantizada no es confiable para auditorías ni para decisiones.

**Controles básicos de integridad:**

- Control de versiones (ver sección siguiente)
- Firma digital o sello de aprobación con fecha
- Repositorio con historial de cambios (git, SharePoint con versioning, etc.)
- Hash del documento en auditorías críticas

#### Disponibilidad

> *¿Puedo acceder a este documento cuando lo necesito?*

Especialmente crítico en escenarios de respuesta a incidentes, auditorías o continuidad de negocio.

**Lo que falla habitualmente:**

- Documentos guardados solo en el equipo de quien los creó
- Documentos en plataformas sin backup
- Documentos cuya ubicación solo conoce una persona
- Documentos inaccesibles cuando la red está caída (y justo en ese momento los necesitas)

### El versionado — la práctica que más se descuida

Un documento sin control de versiones es un documento que miente sobre su estado actual.

**Esquema simple de versionado:**

```
v0.X  →  Borrador (en revisión, no vigente)
v1.0  →  Primera versión aprobada y vigente
v1.X  →  Modificaciones menores sin cambio de fondo
v2.0  →  Revisión mayor o cambio de alcance significativo
```

**Metadatos mínimos en todo artefacto:**

```
Nombre del documento:
Versión:
Fecha de creación:
Fecha de última modificación:
Autor:
Revisado por:
Aprobado por:
Próxima revisión:
Clasificación:
```

> **Un documento v1.0 que nunca tuvo v0.1 ni v0.2 probablemente nunca fue revisado.**  
> La versión cuenta la historia del documento.

---

## 🧾 4. Cuidar las evidencias — lo que distingue la gestión real de la gestión de papel

Una evidencia es cualquier registro que demuestra que algo ocurrió, que algo fue decidido o que un control funciona.

En gestión de riesgos, las evidencias no son opcionales.  
Son lo que te protege cuando alguien pregunta:

> *"¿Por qué no avisaron?"*  
> *"¿Quién aprobó eso?"*  
> *"¿Cuándo se hizo la última revisión?"*

### Los tres tipos de evidencia que más se pierden

#### Tipo 1 — Evidencia de identificación

*"Yo lo vi y lo reporté."*

- Log o ticket de detección con fecha y hora
- Correo enviado al área responsable
- Captura de pantalla con contexto (no solo la alerta — el sistema, la fecha, el origen)
- Registro en la herramienta de gestión (ITSM, GRC, lo que usen)

**Error frecuente:** Guardar solo la captura de la alerta, sin contexto. Tres meses después nadie sabe qué sistema era, qué hora era ni qué estaba pasando.

#### Tipo 2 — Evidencia de decisión

*"Se tomó esta decisión, este día, por esta persona."*

- Acta de reunión donde se discutió el riesgo
- Correo de aprobación (aunque sea informal, es evidencia)
- Ticket cerrado con comentario de resolución
- Acta de aceptación firmada

**Error frecuente:** Las decisiones se toman en reuniones presenciales o por Teams/Slack y nadie las formaliza. Después no existe registro de quién decidió qué.

#### Tipo 3 — Evidencia de control

*"El control está implementado y funciona."*

- Logs del control activo (firewall, antivirus, MFA, monitoreo)
- Resultado de prueba o ejercicio (pentest, DR test, simulacro de phishing)
- Reporte periódico de efectividad
- Registro de excepción cuando el control no se pudo aplicar

**Error frecuente:** Asumir que si el control está configurado, está funcionando. Sin evidencia periódica de que opera correctamente, es fe, no gestión.

### Dónde y cómo guardar evidencias

**Lo mínimo que necesitas:**

| Elemento | Requisito |
|---|---|
| Repositorio centralizado | No en el equipo de nadie — en un lugar con acceso controlado y backup |
| Nomenclatura consistente | `YYYY-MM-DD_tipo_descripcion_version.ext` facilita la búsqueda en auditorías |
| Retención definida | ¿Cuánto tiempo guardas cada tipo de evidencia? Define eso antes de que te pregunten |
| Control de acceso | No todo el mundo necesita ver todo — confidencialidad del activo aplica también a su evidencia |
| Integridad verificable | Para evidencias críticas, considera hash o repositorio con log de cambios |

### El checklist antes de cerrar un artefacto

Antes de marcar cualquier artefacto como "completo" o "aprobado":

- [ ] ¿Tiene versión y fecha?
- [ ] ¿Tiene dueño asignado (autor + aprobador)?
- [ ] ¿Está clasificado según sensibilidad de su contenido?
- [ ] ¿Existe evidencia de que fue revisado por las partes correctas?
- [ ] ¿Está guardado en un repositorio con backup, no solo en el equipo de alguien?
- [ ] ¿Hay fecha de próxima revisión?
- [ ] ¿Si mañana me voy de la empresa, alguien puede encontrar este documento y entenderlo?

> Esa última pregunta es la más honesta.  
> Si la respuesta es no, el artefacto no está realmente terminado.

---

## ❌ Anti-patrones frecuentes en la creación de artefactos

| Lo que hacemos | Por qué es un problema |
|---|---|
| Crear el documento y no decirle a nadie | Sin difusión, no existe operacionalmente |
| Guardar en el equipo personal | Si el equipo falla o la persona se va, se pierde todo |
| Versión única sin historial | No se puede auditar la evolución ni detectar cambios no autorizados |
| Evidencias sin contexto | Tres meses después nadie sabe qué significan |
| Aprobaciones por verbal o chat informal | No quedan registradas y no son defendibles |
| Documentos que nadie revisa periódicamente | Se desactualizan y empiezan a mentir sobre la realidad |
| Clasificar todo como "confidencial" por default | Impide el acceso a quien lo necesita y genera fricción innecesaria |

---

## 🔑 Lo que debes llevarte de este módulo

1. **Empieza en borrador, siempre.** El v0.1 sucio con preguntas abiertas es mejor punto de partida que la hoja en blanco perfecta.
2. **Sin validación formal, el artefacto no existe jurídica ni organizacionalmente.** La firma y la fecha son parte del documento, no el final del proceso.
3. **CID aplica a tus propios documentos.** Un registro de riesgos sin control de acceso, sin integridad y sin disponibilidad asegurada es un riesgo en sí mismo.
4. **Versiona todo.** La versión cuenta la historia del documento — y esa historia puede salvarte en una auditoría.
5. **La evidencia sin contexto no es evidencia.** Fecha, sistema, quién, qué, por qué. Sin eso, es una captura de pantalla que nadie puede interpretar.
6. **La pregunta final siempre es:** ¿si yo no estuviera mañana, alguien podría encontrar esto y entenderlo?

---

> *Estos seis módulos son una conversación, no un manual. Lo que funciona en tu contexto puede no funcionar en el mío. Lo que sí funciona siempre: documentar, validar, versionar y tener dueño.*

---

*Piensa como Atacante, Decide como Negocio — Charla de comunidad por Fernando Contreras / Shiru*
