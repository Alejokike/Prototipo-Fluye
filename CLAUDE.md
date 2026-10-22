# CLAUDE.md · Prototipo de Fluye · Rama Producto

Instrucciones para Claude Code en esta carpeta. Léelas completas antes de tocar cualquier archivo.
Última revisión: 16-oct-2026. Si algo de aquí contradice a Notion, **Notion manda**: avisa de la diferencia y no la resuelvas por tu cuenta.

---

## 1. Qué es esto

- Es el prototipo navegable de **Fluye Initial Product (P1 · Venezuela · Seller-led)**. Esta es la rama de Producto, publicada como artefacto en claude.ai.
- Es **desechable y de referencia**. Sus decisiones se llevan a la especificación (FDS/TDS). **Su código nunca se porta a Angular**: lo que se extrae es el aprendizaje.
- Sirve para cuatro cosas (guía del prototipo, §2):
  1. **Mostrar que el loop cierra:** un pago observado cambia los hechos que el vendedor ve en la siguiente venta con el mismo cliente. Esto es lo que diferencia a Fluye de un simple flujo de venta y cobro.
  2. Hacer entender la propuesta de valor en pocos minutos: control sobre la propia política, visibilidad de cada cliente, venta a plazo respaldada por hechos y cobro sin fricción.
  3. Cerrar decisiones viendo, no debatiendo.
  4. Ser la referencia visual de lo que se construye en octubre.
- Nivel de riesgo C: no toca producción ni datos reales.

## 2. La visión que el prototipo tiene que reflejar

**Narrativa maestra:** *Fluye desbloquea el crédito B2B convirtiendo la actividad comercial real en registros de grado bancario; myservy es la infraestructura debajo.*

Fluye es la plataforma del **Ecosistema de Crédito Comercial** para mercados B2B: estructura cómo las empresas se relacionan, comercian y construyen confianza crediticia entre sí, para que un banco pueda financiar transacciones concretas con confianza.

**Lo que Fluye NO es.** Nada en la UI puede sugerir lo contrario:
- No presta ni es prestamista: el capital siempre lo pone un aliado.
- No garantiza ni es garante.
- No recibe ni custodia el dinero de las ventas: el pago del cliente llega a la cuenta del vendedor.
- No es un riel de pagos ni un BNPL.
- No emite las facturas del vendedor: solo registra el número de factura y de control.
- No es un buró de crédito: no hay score global ni cuenta del cliente.

**Principios del CEO (decisiones de octubre 2026):**
- **Score:** lo calcula el engine de myservy con reglas fijas (mismos datos, mismo resultado). La AI explica, lee documentos y sugiere. **El vendedor decide.**
- **Configuración por país:** lo que depende del país, de los aliados o de los contratos lo configura **Fluye Operations**. El vendedor solo activa o desactiva.
- **Un solo producto que se adapta por mercado.** Lo que cambia por país vive en un paquete de mercado: moneda, idiomas, calendario, impuestos, medios de pago, verificación, fees y aliados. El mercado es de la cuenta y el idioma es de cada usuario. Hoy existe el paquete de Venezuela; Qatar llega después del descubrimiento.
- **Distinción en cada pantalla:** cada superficie separa **hechos, interpretación, recomendación y decisión humana**.

**Cómo cobra Fluye** (sin mínimo por factura ni por cuenta):
- La base se devenga al activar la venta y se cobra con cada pago recibido, sobre lo efectivamente pagado.
- Lo no pagado, anulado o retenido no paga base.
- **Dos modos por cliente** del vendedor (decidido el 15-oct):
  - *Con evaluación de crédito* (tarifa base). Incluye cuotas, condiciones a plazo, límites, score, cobertura y adelanto.
  - *Solo cobranza* (50 % de descuento). Registra ventas de pago único, las cobra y guarda el historial, para que el score exista desde el primer día cuando se active la evaluación.
- En el MVP, el cobro de los fees es **manual**: factura mensual y pago por transferencia (6-oct). El débito domiciliado llega después del lanzamiento.

## 3. Alcance del MVP de octubre

**Fuente del alcance:** la Matriz de alcance P1 y la propiedad «Alcance octubre» de cada ficha. Lo que está **Fuera** puede verse como referencia, pero no se construye ni se pule.

**Decisiones vigentes:**
- **Roles:** tres (Propietario, Administrador y Operador) y puede haber varios Propietarios (DC-013, 15-oct). La página de decisiones de octubre todavía habla de cuatro roles; manda la decisión del 15-oct.
- **Pagos:** medios con aviso y registro manual, sin riel. El cliente marca «Ya pagué» y el vendedor aprueba o devuelve. Se permiten pagos parciales; no hay sobrepago ni saldo a favor.
- **Factura:** opcional en cualquier venta (venta mínima: solo monto y plazo).
- **Plan de pago:** solo pago único y cuotas fijas.
- **Enlace seguro:** vence a los 14 días y se puede regenerar. Se envía por correo en español e inglés.
- **Monedas:** USD y VES con tasa manual. La moneda base queda fija con la primera venta. **Las monedas distintas nunca se suman.**
- **Avisos:** solo por correo, con cadencia posterior al vencimiento, y pausa de ventas por mora. El logo del vendedor sí entra en los correos (15-oct).
- **No entran:** exportar (Q-04) ni el cobro automático (Q-05).

**Fuera de octubre.** Hoy el bloque MASTER de `app.js` lo oculta o lo bloquea:
- Riel y medios automáticos, tarjeta o PayPal, cobro automático, conciliación bancaria.
- Retenciones de IVA e ISLR.
- Importaciones, historial, Cartera de ventas, Estado de cuenta, exportaciones, búsqueda global y centro de notificaciones.
- API, webhooks y MCP.
- Cotización y aceptación del cliente, invitaciones y cuenta del cliente.
- Valuaciones, inicial más cuotas, pago contra recepción y cobro mensual.
- Mensajes de texto, aviso previo al vencimiento y recordatorios fijos por cuota.
- Todo el lado de compras (Buyer-led): proveedores, cotizaciones, compras, pagos y cartera de compras.

**Por decidir:** las excepciones de Operations (SC-019).

## 4. Reglas de trabajo

1. **La especificación manda.** Las reglas salen de las fichas de Notion (SC, UC, BR, DC). Si una pantalla necesita una regla que no existe, no la inventes: márcala en el código con `// SUPUESTO: …` y anótala en `DECISIONS.md`.
2. **No resuelvas diferencias en silencio.** Si la especificación y el prototipo no coinciden, se registra y se decide fuera del código.
3. **Registro de decisiones.** Mantén `DECISIONS.md` en esta carpeta durante la sesión, con las columnas: Decisión | Variante elegida | Por qué | Tipo (Decisión / Supuesto abierto). Producto lo lleva luego a Notion.
4. **Trazabilidad.** Cada cambio cita su pantalla (SC-xxx) y, si aplica, su UC o CF. Si cambia lo que muestra una pantalla, actualiza su ficha de referencia en el objeto de referencias de `app.js` (busca `'SC-0`).
5. **Lenguaje de la vertical:**
   - En la UI se dice *cliente*, aunque la especificación diga *buyer*.
   - En la UI se dice *saldo*, aunque la especificación diga *exposición*.
   - Se usa el vocabulario de las Bases y del glosario.
   - No se usan nombres de personas en textos ni datos.
6. **Sin datos reales** ni datos sensibles. Los datos de ejemplo son de Venezuela, con clientes en USD y en VES. Debe haber al menos un cliente nuevo y uno recurrente, para que se vea el cierre del loop.
7. **Modo demo:** una vista limpia para presentar al cliente, sin panel de decisiones ni marcas de supuesto. No lo rompas.
8. **No publiques.** La publicación al artefacto la hace Claude en Cowork, que primero revisa si algún co-autor publicó entretanto.

## 5. Design System (myservy DS 1.2.0 · tema fluye-light)

- **Colores:** usa **solo los roles de color** definidos en `:root` (`--primary`, `--on-surface`, `--surface-container-*`, `--success`, etc.). **Nunca escribas un hex en una pantalla.**
- **Texto y cifras:** la tipografía es Geist. Los montos van con `.amt` (Geist Mono, cifras tabulares) y el iconismo es Material Symbols Outlined.
- **Botones:**
  - Esquinas de 12 px y etiqueta de 13 px.
  - md (32 px) por defecto.
  - sm (28 px) dentro de filas, tarjetas, encabezados de panel, tablas, barras de filtros y avisos.
  - lg (40 px) solo para el botón principal de pago del cliente.
  - **Una sola acción llena por pantalla**: dentro de filas y tarjetas, la acción principal es tonal (`.btn-tn`).
- **Dirección del texto:** usa propiedades lógicas (`inset-inline-*`, `margin-inline-*`) para no romper RTL.
- **Movimiento:** respeta `prefers-reduced-motion`.
- **Plugin `ms-front`:** si tiene disponible la skill `ms-design-system`, úsala antes de crear o cambiar estilos.

### Decisiones de diseño vigentes (19-oct-2026)
- **Sin tarjetas dentro de tarjetas.** Dentro de un panel, los indicadores van planos.
- **Ayuda mínima.** Solo se deja un subtítulo, pista o tooltip si dice algo que la pantalla no dice. No se añaden textos redundantes.
- **Móvil sin barra inferior.** La navegación es el menú lateral; no hay botón principal flotante.
- **Controles del DS.** Los `<select>` y los `input[type=file]` dentro de `.fld` se reemplazan solos por los componentes `ui-select` y `ui-file` (scripts al final de `index.html`). Escribe el control nativo y deja que el script lo mejore. Sus textos propios se eligen según `document.documentElement.lang`.
- **Datos de ejemplo del equipo:** solo Carolina Mejías es Propietaria.
- **Referencias:** el objeto `REF` y el mapa `G` (en `mapHtml`) siguen la base «Screens — Fluye Initial Product» de Notion. Si cambia una ficha (ID, nombre, alcance, madurez), actualiza ambos.

## 6. Cómo está construido el código

Son dos archivos y deben seguir siendo dos: no añadas frameworks, bundlers, dependencias ni backend.

- **`index.html`:** casi todo es CSS, organizado en **capas que se pisan**:
  - Orden: base → «Acabado de última generación» → «DS 1.2.0» → «MASTER».
  - La última regla gana. Varias clases se definen más de una vez (`.hero-c` ×4, `.mxr` ×3, `.panel` ×3).
  - Al final solo hay `<div id="app">`, `#toast` y `<script src="app.js">`.
- **`app.js`:** una sola función autoejecutable en `'use strict'`. Las secciones están marcadas con `/* ---------- … ---------- */`:

  | Sección | Qué contiene |
  |---|---|
  | utilidades | fechas, formatos, idiomas (`LANGS`), día de hoy simulado (`TODAY` = 29-sep-2026) |
  | datos de ejemplo | clientes, ventas, pagos, mercados (`MARKETS`) |
  | selectores y reglas | cálculos de saldo, límites, mora y score |
  | piezas de UI | componentes HTML reutilizables (`info()`, `head()`, chips, etc.) |
  | pantallas | una función `vXxx()` por pantalla (`vHome`, `vBuyers`, `vSale`, `vSaleForm`, `vReview`, `vPay`, `vCobranza`, `vPolicy`…) |
  | capas del prototipo | panel de decisiones, modo demo, diálogos |
  | router y render | `route()`, que lee el hash (`#/sales/VTA-0006`) y pinta con `innerHTML` |
  | SC-043 | `vJoin()` justo después de `vRecover()`; ruta `#/join/<id de usuario invitado>`; acciones `join*` |
  | `I18N` | diccionario de traducciones (una línea de unos 273 KB) |
  | **MASTER** | al final: recorta todo al MVP de octubre |

- **Estado:** el estado global vive en `S`. Cada interacción modifica `S` y vuelve a llamar a `route()`.

**Dónde va cada cambio:**

| Qué cambia | Dónde va |
|---|---|
| Una pantalla | su `vXxx()` |
| Datos de ejemplo | la sección de datos |
| Una regla de negocio | la sección de selectores y reglas |
| Algo entra o sale del MVP | el bloque MASTER |
| Un estilo | la regla que gana para esa clase, o una regla nueva **al final** del CSS con un comentario |
| Traducciones | `I18N` en `app.js`; la capa del prototipo (`.proto`, `.drawer`, `.ref`, supuestos) no se traduce a propósito |

## 7. Lo que rompe el prototipo sin avisar

1. **Las traducciones van por coincidencia de texto.** La pantalla se pinta en español y `applyI18n` busca cada texto en `I18N.en`. Si cambias o añades un texto en español, **añade o actualiza su par en `I18N`**: `["texto en español","English text"]`, con `{a1}`, `{s1}`… para las partes variables. Si no, la vista en inglés queda a medias sin ningún error. La vista del cliente (`#/pay`, `#/msg`) usa el idioma del cliente.
2. **MASTER reemplaza funciones.** `xMenu`, `resCard`, `mTips`, `cartOk`, `navData`, `route`, `debPanel`, `billBanner` y `billPending` se redefinen al final, y `mvpData()` modifica los datos. Si editas la versión original, no verás el cambio. Si quitas algo de `MVP_BLOCK` o de la regla CSS de MASTER, vuelve a aparecer funcionalidad que está fuera del MVP. Eso es un cambio de alcance y necesita decisión.
3. **CSS en capas:** antes de editar una regla, busca todas las definiciones de esa clase.
4. **Paréntesis en CSS:** un `)` de más invalida la declaración en silencio (pasó en 6 reglas, corregidas el 16-oct). Comprueba el balance con el script del paso 2 de la verificación.
5. **Configuración guardada en el navegador:** la clave `fluye.cfg` (con versión `v:1`) guarda marca, mercado y preferencias. Si cambias la forma de esos datos, sube la versión en `cfgSave` y `cfgLoad`. Otras claves: `fluye.lang` y `fluye.today`.
6. **Líneas gigantes:** `I18N` y los logos en base64 (`LOGO_*`) ocupan líneas de decenas o cientos de KB. **No las reescribas completas** ni las abras para reformatear. Para tocarlas, haz un reemplazo exacto de la parte que cambia.
7. **Nada de llamadas de red:** no añadas `fetch` ni scripts externos. La única dependencia externa son las fuentes de Google.
8. **Cambios puntuales:** no reformatees, no reordenes y no hagas «limpiezas» masivas. Esos diffs no se pueden revisar ni fusionar con lo que publiquen otros.

## 8. Verificación antes de devolver los archivos

Ejecuta esto y reporta el resultado:

```bash
# 1. Sintaxis del JS
node --check app.js

# 2. Paréntesis desbalanceados en el CSS (no debe imprimir nada)
python3 -c "import re;s=open('index.html',encoding='utf-8').read();c=re.sub(r'/\*.*?\*/','',s[s.find('<style>'):s.rfind('</style>')],flags=re.S);[print(d.strip()[:100]) for d in re.findall(r'[^{};]+(?=[;}])',c) if d.count('(')!=d.count(')')]"

# 3. Textos nuevos sin traducir: lista cada texto en español que añadiste y confirma que existe en I18N
```

Luego abre `index.html` en el navegador y comprueba:

- **Rutas:** recorre como mínimo `#/entry`, `#/home`, `#/buyers`, `#/buyers/b1`, `#/buyers/new`, `#/sales`, `#/sales/new`, `#/sales/VTA-0006`, `#/cobranza`, `#/pay/VTA-0006`, `#/msg/VTA-0006`, `#/config` y cada `#/config/*`.
- **Consola:** sin errores.
- **Idiomas:** en español y en inglés.
- **Anchos:** a 390 px (móvil) y a 1280 px.
- **Modo demo:** se ve limpio.
- **Lo que está fuera:** sigue oculto (`#/cartera`, `#/notifications` y las rutas de compras redirigen a `#/home`).

Termina con un resumen de lo que cambió: pantallas (SC), textos nuevos y su traducción, y supuestos nuevos.

## 9. Fuentes en Notion

- Fluye definitions (narrativa maestra): https://app.notion.com/p/3a0d1d9a83c9801797f9ec018045a805
- Decisiones de producto de octubre 2026 (CEO): https://app.notion.com/p/3f1d1d9a83c9816b9007e1798a0cbd9e
- Prototype — Fluye Initial Product (guía, alcance, escenas): https://app.notion.com/p/3ead1d9a83c981a1a9b8f467b6401247
- Matriz de alcance — P1 (octubre 2026): https://app.notion.com/p/1584735466e14709b4c64115c3405544
- FDS-01 Overview: https://app.notion.com/p/0e932a67600f4060b824fc03ae04bab5
- Contexto de myservy para asistentes de IA: https://app.notion.com/p/3f1d1d9a83c9818cba55f620e51d3be4
