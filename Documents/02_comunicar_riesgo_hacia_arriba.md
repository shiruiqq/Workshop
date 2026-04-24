# 02 — Comunicar el Riesgo Hacia Arriba

> **Workshop: Gestión de Riesgos en el Mundo Real**  
> Módulo 2 de N — *Hablar en idioma gerente*

---

## 🎯 Objetivo de este módulo

Que el equipo técnico entienda **cómo traducir un riesgo técnico en un mensaje que el negocio pueda escuchar, entender y decidir.**

No se trata de simplificar.  
Se trata de hablar el idioma correcto, con la persona correcta, en el momento correcto.

---

## 😤 El problema real

Casi nadie nos enseña esto.  
Se aprende con experiencia. Con errores. Con oportunidades que a veces llegan de golpe:

> *"Tienes 10 minutos con el Gerente General. ¿Qué le dices?"*

Y ahí es donde caemos en los dos patrones más comunes:

---

### ❌ Patrón 1 — "Todo está malo y necesitamos plata"

El técnico llega con una lista de problemas, vulnerabilidades críticas, sistemas desactualizados y una solicitud de presupuesto.

**El resultado:**  
La gerencia escucha costos, no valor.  
Escucha problemas, no soluciones.  
Y en el mejor caso, aprueba lo mínimo para "apagar el incendio".

---

### ❌ Patrón 2 — Solo hablamos cuando algo sale mal

Cuando todo funciona, no decimos nada.  
Cuando hay un incidente, aparecemos con el sombrero en la mano.

**El resultado:**  
La percepción de TI/Seguridad es reactiva.  
Siempre llegamos a pedir, nunca a mostrar valor.  
Y la gerencia empieza a vernos como un costo fijo, no como una capacidad estratégica.

---

## 🧠 Lo que la gerencia realmente piensa

Seamos honestos sobre cómo nos ven:

> *"Son los de las computadoras y los servidores."*  
> *"Mientras tengamos internet, todo bien."*  
> *"¿Eso no lo hace solo la inteligencia artificial ahora?"*

No es mala fe. Es que **el mundo C-Level vive en dos dimensiones:**

| Dimensión | Lo que les importa |
|---|---|
| **Financiera** | ¿Cuánto cuesta? ¿Cuánto ahorramos? ¿Cuál es el ROI? |
| **Operacional** | ¿La máquina sigue funcionando? ¿Podemos vender hoy? |

Si tu mensaje no cabe en alguna de esas dos dimensiones, **no llega.**

---

## ✅ Lo que rara vez hacemos: mostrar los wins

Antes de hablar de riesgos, hay algo que casi nunca comunicamos:

**Lo que hemos hecho bien.**

- El ataque que se bloqueó sin que nadie se enterara
- El proveedor que rechazamos porque no cumplía los controles
- La migración que salió limpia porque hicimos el trabajo previo
- El ahorro por no haber tenido un incidente este año
- El proyecto que se entregó a tiempo con seguridad incluida

> **Esto no es vanidad. Es contexto.**  
> Si solo llegas a pedir, eres un costo.  
> Si llegas mostrando valor primero, eres una inversión.

---

## 🔑 El cambio de mentalidad

| Lo que decimos | Lo que deberían escuchar |
|---|---|
| "Tenemos una vulnerabilidad crítica CVSSv3 9.8" | "Si esto se explota, paramos operaciones 48 horas" |
| "Necesitamos un WAF" | "Con esto protegemos los ingresos del canal digital" |
| "El sistema X está desactualizado" | "Ese sistema procesa el 40% de nuestras ventas y está expuesto" |
| "Detectamos un intento de acceso no autorizado" | "Alguien intentó entrar. Lo bloqueamos. Acá está lo que hicimos y lo que necesitamos para que no vuelva a pasar" |

**La fórmula base:**

```
[Qué pasó o puede pasar]
+ [Qué impacta en el negocio]
+ [Qué hicimos o proponemos]
+ [Qué necesitamos decidir]
```

---

## 🏗️ Cómo cambia el mensaje según tu posición jerárquica

Tu rol define **qué puedes decir, a quién, y con qué nivel de detalle.**

---

### 🔧 Analista / Especialista técnico

**Tu audiencia directa:** Jefe de área, coordinador, líder técnico.  
**Tu lenguaje:** Técnico pero contextualizado.  
**Tu objetivo:** Escalar con evidencia y con una recomendación clara.

Lo que necesitas dominar:
- El checklist del Módulo 01 (evidencia + severidad + activo + responsable)
- Una recomendación inicial, aunque sea preliminar
- Saber cuándo parar y dejar que tu jefe lleve el mensaje más arriba

> ⚠️ **Error frecuente:** Ir directo a la gerencia saltando a tu jefe.  
> Aunque tengas razón, rompe la cadena y genera desconfianza.

---

### 👔 Jefe de Área / Coordinador de Seguridad

**Tu audiencia directa:** Gerente de TI, CTO, CISO.  
**Tu lenguaje:** Técnico + impacto operacional.  
**Tu objetivo:** Traducir el hallazgo técnico en una decisión de gestión.

Lo que necesitas dominar:
- Conectar el riesgo técnico con el impacto en operación o finanzas
- Presentar opciones, no solo el problema
- Tener claro quién tiene que decidir y darte el presupuesto o la autorización

> ⚠️ **Error frecuente:** Presentar el problema sin opciones.  
> La gerencia no sabe qué hacer con "hay un problema crítico".  
> Necesitan escuchar "tenemos tres opciones, recomendamos esta, y cuesta X".

---

### 🧭 CISO / Gerente de Seguridad / CTO

**Tu audiencia directa:** Gerente General, Directorio, Comité de Riesgos.  
**Tu lenguaje:** Negocio, finanzas, estrategia.  
**Tu objetivo:** Enmarcar la seguridad como capacidad organizacional, no como gasto técnico.

Lo que necesitas dominar:
- Hablar en términos de riesgo empresarial, no técnico
- Mostrar tendencias, no eventos aislados
- Conectar inversión en seguridad con continuidad operacional y cumplimiento regulatorio
- Saber cuándo decir "esto necesita una decisión de directorio"

> ⚠️ **Error frecuente:** Llevar al directorio el mismo nivel de detalle que llevas a tu equipo.  
> Un director no necesita saber que el CVSSv3 es 9.8.  
> Necesita saber que "si no actuamos antes del viernes, tenemos exposición regulatoria y posibles multas".

---

## 📊 Estructura de un mensaje de escalamiento efectivo

Independiente de tu nivel jerárquico, la estructura es similar. Lo que cambia es el nivel de detalle.

```
1. SITUACIÓN (qué está pasando)
   → Una oración. Sin tecnicismos innecesarios.

2. IMPACTO (qué significa para el negocio)
   → Operación, dinero, reputación o regulación.

3. LO QUE HICIMOS (acciones tomadas)
   → Muestra que no llegaste con las manos vacías.

4. OPCIONES (qué podemos hacer)
   → Mínimo dos opciones. Con costo y consecuencia de cada una.

5. RECOMENDACIÓN (qué propones tú)
   → Una sola. Clara. Con justificación.

6. DECISIÓN REQUERIDA (qué necesitas de ellos)
   → Sé explícito: ¿aprobación de presupuesto? ¿autorización para actuar? ¿aceptación del riesgo?
```

---

## 💬 Ejemplo real: el mismo riesgo, tres mensajes distintos

**Contexto:** Se detectó acceso no autorizado a un servidor de archivos compartido con datos de clientes.

---

**Mensaje del Analista → a su Jefe:**

> "Detecté acceso anómalo al fileserver de clientes desde una IP interna no reconocida. Tengo los logs, aislé el equipo de origen y generé el ticket. Necesito que valides si escalamos a incidente formal o esperamos el análisis completo."

---

**Mensaje del Jefe → al CISO:**

> "Tuvimos un acceso no autorizado al servidor de archivos de clientes. El equipo lo contuvo en menos de una hora. El impacto potencial incluye datos personales de clientes, lo que activa nuestra política de notificación. Necesito tu autorización para activar el proceso de respuesta a incidentes y evaluar si hay obligación regulatoria de notificar."

---

**Mensaje del CISO → al Gerente General:**

> "Esta mañana tuvimos un intento de acceso no autorizado a información de clientes. El equipo lo detectó y contuvo rápido. En este momento estamos evaluando si hay obligación de notificar a la autoridad regulatoria. Te aviso antes de que llegue cualquier consulta externa. Necesito 30 minutos contigo esta semana para revisar si el nivel de inversión en detección temprana es suficiente dado el crecimiento de este tipo de amenazas."

---

> **El riesgo es el mismo. El mensaje es completamente distinto.**

---

## 📈 Cómo construir el historial de wins

No esperes el próximo incidente para aparecer.  
Construye un registro simple de valor entregado:

| Período | Acción | Impacto en negocio |
|---|---|---|
| Q1 | Bloqueamos campaña de phishing dirigida | 0 credenciales comprometidas |
| Q1 | Rechazamos integración de proveedor sin controles | Evitamos exposición de datos de clientes |
| Q2 | Migración cloud sin incidentes de seguridad | Proyecto entregado en plazo |
| Q2 | Reducción de superficie de ataque en red perimetral | Reducción de 40% en alertas de seguridad |

> Este registro es tu argumento cuando pides presupuesto.  
> No es vanidad. Es evidencia de gestión.

---

## ❌ Anti-patrones frecuentes al comunicar hacia arriba

| Lo que hacemos | Por qué es un problema |
|---|---|
| Hablar en siglas y términos técnicos | La gerencia desconecta y delega sin entender |
| Solo aparecer cuando hay problemas | Se construye una imagen reactiva y de costo |
| Pedir presupuesto sin mostrar valor previo | El contexto falta y la respuesta es "no hay" |
| Llevar el problema sin opciones | Obliga a la gerencia a improvisar una solución técnica |
| Saltarse la cadena jerárquica | Genera desconfianza aunque el mensaje sea correcto |
| No documentar la decisión tomada | Si algo falla, no hay trazabilidad de quién aprobó qué |

---

## 🔑 Lo que debes llevarte de este módulo

1. **La gerencia vive en dos mundos:** finanzas y operación. Tu mensaje tiene que entrar por ahí.
2. **Tu posición jerárquica define el nivel de detalle**, no el fondo del mensaje.
3. **Mostrar wins no es opcional.** Es el contexto que hace que te escuchen cuando pides.
4. **Llega siempre con opciones y una recomendación.** No solo con el problema.
5. **Documenta la decisión.** Siempre. Aunque sea un correo de confirmación.

---

> *Siguiente módulo → Decidir bajo presión: trade-offs reales y quién asume el riesgo*

---

*Workshop: Gestión de Riesgos en el Mundo Real — Módulo 02*
