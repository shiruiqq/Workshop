# 03 — El Riesgo en el Tiempo

> **Workshop: Gestión de Riesgos en el Mundo Real**  
> Módulo 3 de N — *Los riesgos no son eventos. Son procesos.*

---

## 🎯 Objetivo de este módulo

Romper una ilusión muy común en la gestión de riesgos:

> *"Identificamos el riesgo. Lo evaluamos. Listo."*

El riesgo no es un evento puntual que se resuelve y desaparece.  
Es una condición que **vive, cambia, envejece y cobra cuando menos lo esperas.**

Y a veces, el golpe no llega el día que tomaste la mala decisión.  
Llega meses después.

---

## 📖 La historia del servidor que "siempre funcionó bien"

Esta historia es real. Ocurre en muchas organizaciones. Con distintos activos, pero el mismo patrón.

---

### El escenario

Un servidor con una sola función:  
**Enviar y recibir documentos tributarios. SMTP/POP. Nada más.**

Viejo. Estable. Olvidado.

Y con una regla de firewall que nadie había cuestionado en años:

```
ANY → ANY | ALL PORTS | PERMIT
```

Acceso total hacia y desde internet. Sin restricción. Sin monitoreo.  
El servidor hacía su trabajo. Nadie lo tocaba. Nadie lo revisaba.

> *"Siempre ha funcionado así."*

Esa frase. Esa frase exacta.

---

### La intervención

Llega el equipo de ciberseguridad.  
Revisa. Documenta. Genera evidencia.  
Plantea escenarios de lo que podría ocurrir con esa exposición.

La respuesta del negocio, simplificada:

> *"Sí, entendemos. Pero no lo toquemos ahora, está funcionando."*

Riesgo identificado. Riesgo **no documentado como aceptado.**  
Nadie firmó nada. Nadie asumió formalmente el riesgo.  
Solo... se dejó estar.

---

### El trade-off mal resuelto

En algún momento se decide actuar.  
Se restringe la regla. Se cierra la exposición.

Y el servidor deja de funcionar.

La mensajería tributaria falla.  
La operación se detiene.  
La presión es inmediata.

**Decisión bajo presión:**

> *"Vuelvan al estado original. Necesitamos que funcione."*

Y así, sin análisis, sin plan alternativo, sin documentar la decisión:  
**se reabre el ANY TO ANY.**

El riesgo vuelve. Más legitimado que antes.  
Porque ahora tiene un antecedente:  
*"La última vez que lo tocamos, se cayó todo."*

---

### La consecuencia diferida

Pasan los meses.

El servidor sigue ahí. La regla sigue abierta.  
Nadie vuelve a revisarlo. El tema quedó "cerrado".

Y entonces ocurre el ransomware.

No esa semana. No ese mes.  
**Meses después.**

---

> ¿Fue culpa del servidor?  
> ¿Fue culpa de la regla?  
> ¿Fue culpa de quien no quiso tocarlo?  
> ¿Fue culpa de quien lo tocó mal?

**Todas las anteriores. Y ninguna por separado.**

---

## 🔗 Los tres nodos de la historia

Esta historia no tiene un momento donde falló todo.  
Tiene tres nodos encadenados. Si falla uno, el siguiente se vuelve inevitable.

---

### Nodo 1 — El riesgo aceptado sin documentar

| Qué pasó | Por qué importa |
|---|---|
| El riesgo se identificó | El equipo técnico hizo su trabajo |
| Se presentó con evidencia | También |
| No se documentó la decisión de no actuar | Acá está el problema |
| Nadie asumió el riesgo formalmente | El riesgo quedó flotando, sin dueño |

**La trampa:**  
Cuando no hay un documento que diga *"conocemos este riesgo y decidimos aceptarlo por estas razones"*, el riesgo existe pero nadie es responsable de él.

Y cuando algo falla, la pregunta es:

> *"¿Por qué nadie hizo nada?"*

Y la respuesta técnica es:

> *"Sí hicimos. Lo reportamos. Nadie decidió."*

Y la respuesta del negocio es:

> *"Nadie nos dijo que era tan grave."*

**Ambos tienen razón. Y eso es exactamente el problema.**

---

### Nodo 2 — El trade-off mal resuelto

| Qué pasó | Por qué importa |
|---|---|
| Se intentó corregir el riesgo | Bien |
| No había un plan de contingencia | Mal |
| El servicio falló al implementar el cambio | Consecuencia predecible no prevista |
| Se revirtió bajo presión sin análisis | La decisión se tomó en el peor momento posible |
| No se documentó la reversión | El riesgo volvió legitimado |

**La trampa:**  
Un trade-off es una decisión entre dos males.  
Pero un trade-off bajo presión, sin opciones preparadas, casi siempre elige el mal equivocado.

Parchear puede botar producción → cierto.  
No parchear mantiene la exposición → también cierto.

**Pero ninguna de esas dos opciones debería tomarse en el momento de la crisis.**  
Deberían estar analizadas antes.

> *"Si tocamos esto y falla, ¿qué hacemos?"*  
> Esa pregunta debió hacerse antes de tocar.

---

### Nodo 3 — El tiempo como variable activa

| Qué pasó | Por qué importa |
|---|---|
| El riesgo volvió al estado original | El problema se "cerró" sin resolverse |
| Nadie revisó el estado del riesgo después | El riesgo se volvió invisible nuevamente |
| Meses después ocurrió el ransomware | El tiempo entre causa y efecto desvinculó la responsabilidad |
| Nadie conectó el incidente con la decisión anterior | El aprendizaje no ocurrió |

**La trampa:**  
Cuando el tiempo entre la causa y el efecto es largo, la conexión se pierde.  
El ransomware no llegó el día siguiente. Llegó meses después.  
Y eso hace que nadie relacione el incidente con la regla ANY TO ANY.

Pero la cadena estaba ahí.  
**El tiempo no elimina el riesgo. Solo retrasa el cobro.**

---

## ⏳ El riesgo como proceso, no como evento

La mayoría de los frameworks de riesgo tratan el riesgo como algo que:

1. Se identifica
2. Se evalúa
3. Se trata
4. Se cierra

**La realidad es diferente:**

```
IDENTIFICACIÓN
      │
      ▼
EVALUACIÓN
      │
      ▼
DECISIÓN (tratar / aceptar / transferir / evitar)
      │
      ▼
IMPLEMENTACIÓN
      │
      ▼
REVISIÓN ← ← ← ← ← ← ← ← ← ← ← ←
      │                              │
      ▼                              │
¿El contexto cambió?                 │
  ├── Sí → re-evaluar ──────────────┘
  └── No → mantener y volver a revisar
```

> **El riesgo no se cierra. Se gestiona.**

---

## 🔄 Los riesgos cambian con el tiempo

Un riesgo evaluado hoy puede ser completamente distinto en 6 meses.

| Variable que cambia | Cómo afecta al riesgo |
|---|---|
| **El entorno de amenazas** | Una vulnerabilidad sin exploit público puede tener uno mañana |
| **El activo** | Un sistema "de baja criticidad" puede volverse crítico si cambia su uso |
| **El negocio** | La empresa crece, cambia de rubro, adquiere otra empresa |
| **La regulación** | Lo que era opcional puede volverse obligatorio |
| **Los controles** | Un control que mitigaba el riesgo puede dejar de funcionar |
| **El tiempo sin incidente** | Genera falsa sensación de seguridad |

> **"Siempre ha funcionado así"**  
> es la señal de que nadie ha revisado el riesgo en mucho tiempo.

---

## 📋 Gestión del riesgo en el tiempo: lo mínimo necesario

### 1. Fecha de vencimiento del riesgo aceptado

Cuando se acepta un riesgo, debe tener una fecha de revisión.  
No es opcional. Es parte de la decisión.

```
Riesgo: Servidor SMTP con regla ANY TO ANY
Decisión: Aceptar temporalmente mientras se evalúa solución alternativa
Responsable: [nombre]
Fecha de revisión: [fecha concreta, no "próximo trimestre"]
```

---

### 2. Registro de cambios de contexto

Si algo cambia en el entorno, el riesgo debe re-evaluarse.

| Trigger de re-evaluación | Ejemplo |
|---|---|
| Nuevo exploit público para el sistema afectado | CVE publicado con PoC disponible |
| Cambio en el uso del activo | El servidor "de bodega" ahora procesa datos de clientes |
| Incidente en la industria | Otra empresa del mismo rubro fue atacada por el mismo vector |
| Cambio regulatorio | Nueva norma que obliga a proteger ese tipo de dato |
| Cambio en el negocio | Fusión, adquisición, nuevo producto |

---

### 3. Documentar la reversión como decisión

Cuando un control se revierte (como en la historia del SMTP), eso es una decisión de riesgo.  
Y debe tratarse como tal.

```
Evento: Se revirtió el bloqueo de puertos en servidor SMTP
Motivo: Falla en servicio tributario durante implementación
Decisión tomada por: [nombre y cargo]
Estado del riesgo: Reabierto
Plan de cierre: [fecha y responsable]
```

> Si no se documenta, el riesgo reabierto se convierte en riesgo invisible.  
> Y los riesgos invisibles son los que generan ransomware.

---

## 🏭 Por qué esto es especialmente crítico en OT/Industrial

En entornos IT, un sistema desactualizado es un problema serio.  
En entornos OT, un sistema desactualizado puede ser **imposible de actualizar.**

| Característica OT | Implicancia en gestión de riesgos |
|---|---|
| Sistemas legacy sin soporte | El riesgo técnico es permanente y no tiene solución directa |
| Ciclos de mantenimiento largos | La ventana para intervenir es estrecha y planificada con meses de anticipación |
| Impacto físico potencial | Un error no es solo downtime, puede ser seguridad física de personas |
| "No se toca lo que funciona" | La cultura de no intervención es estructural, no por descuido |
| Proveedores que no permiten cambios | El control del activo no es total |

**En OT, la gestión del riesgo en el tiempo no es opcional.**  
Es la única forma de gestionar riesgos que no puedes resolver con un parche.

> La pregunta no es "¿cuándo lo arreglamos?"  
> Es "¿cómo convivimos con este riesgo de forma controlada, y qué nos avisa si la situación cambia?"

---

## ⚖️ Trade-offs: lo que nadie te dice

Un trade-off no es elegir entre lo bueno y lo malo.  
Es elegir entre dos males, con información incompleta, bajo presión.

**Lo que debes tener antes de un trade-off:**

| Pregunta | Por qué importa |
|---|---|
| ¿Qué pasa si actuamos? | El escenario de intervención con sus riesgos |
| ¿Qué pasa si no actuamos? | El escenario de no intervención con sus riesgos |
| ¿Qué pasa si actuamos y falla? | El plan de contingencia |
| ¿Quién decide? | La persona que asume el riesgo debe ser quien decide |
| ¿Quién documenta? | Siempre alguien distinto a quien decide |

> **El trade-off más peligroso es el que se toma en el momento de la crisis.**  
> Porque en ese momento no hay análisis. Solo presión.

---

## 🔑 Lo que debes llevarte de este módulo

1. **"Siempre ha funcionado así" es una señal de riesgo, no de seguridad.**
2. **Un riesgo aceptado sin documentar es un riesgo sin dueño.** Y los riesgos sin dueño explotan solos.
3. **El tiempo entre causa y efecto no elimina la relación.** El ransomware de hoy puede ser la decisión de hace seis meses.
4. **Los trade-offs deben prepararse antes de la crisis**, no durante.
5. **Todo riesgo aceptado necesita fecha de revisión.** Sin esa fecha, no es una decisión. Es un olvido.
6. **En OT, gestionar el riesgo en el tiempo no es una opción.** Es el único modelo posible.

---

> *Siguiente módulo → Decidir bajo presión: el framework simple para tomar decisiones cuando no hay tiempo*

---

*Workshop: Gestión de Riesgos en el Mundo Real — Módulo 03*
