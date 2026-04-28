# Cambio batería portátil (desde 80€ MO + pieza)

> Tiempo realista: **45-90 min** + desplazamiento (mejor en taller)
> Bloque tarifa: **C — Hardware Mano de Obra**
> Modalidad: taller por defecto · domicilio +25€

---

## Qué es y qué NO es

**SÍ es:** sustitución física de la batería interna de un portátil. Mano de obra **desde 80€** según modelo (varía por dificultad de despiece). Pieza aparte (rango 50-150€ según modelo).

**NO es:**
- ❌ **Calibración batería sin cambio**: si la batería todavía aguanta pero el porcentaje miente → es ajuste software, no es servicio. Lo hago gratis si ya estoy en otro servicio.
- ❌ **Reparación celdas batería original**: NO se hace, peligro real (incendio, daño placa).
- ❌ **Cambio cargador**: eso es venta de cargador (rango G de tarifa, ~40€).

**Cliente típico:**
- Portátil 2-4 años con batería que apenas dura 30 min.
- Batería hinchada (peligrosa, urgente).
- Portátil que solo funciona conectado.

⚠️ **Batería HINCHADA = urgencia.** No es estética, es **riesgo de incendio**. Cobrar urgencia +30% si es petición de hoy mismo.

---

## Antes (preparación material)

### Confirmar por WhatsApp
- [ ] **Marca + modelo + año exacto** del portátil. Sin esto NO se puede pedir batería compatible.
- [ ] **Foto del estado actual de la batería**: si está hinchada se ve por la base del portátil deformada o el touchpad levantado.
- [ ] **Foto BatteryReport** del cliente: pedirle ejecutar `powercfg /batteryreport` y mandar el HTML resultante. Te dice capacidad de diseño vs capacidad real.
- [ ] **¿Pieza la trae el cliente o me encargo yo?**
  - Si la trae el cliente: comprobar que es **modelo correcto** y **marca decente** (Tepulseil, Akku-Net, baterías originales). Evitar AliExpress baratas.
  - Si me encargo yo: **48-72h entrega** + coste pieza al cliente. Suelo pedir a Amazon vendido por marca conocida.

### Material en mochila
- [ ] **Kit destornilladores precision** (Phillips PH00/PH0/PH1 + Torx T5/T6 + Pentalobe T5 según marca).
- [ ] **Púas de plástico / spudger** (clave para no rayar carcasa).
- [ ] **Bandeja imantada** + foto de cada paso del despiece (recordar orden tornillos).
- [ ] **Guantes nitrilo** si la batería está hinchada (manchas, principalmente seguridad si la celda revienta).
- [ ] **Bolsa antiestática + bolsa ignífuga** para batería vieja (si está hinchada → bolsa ignífuga obligatoria, NO transporte directo).

---

## Al llegar

### Paso 1 — Inspección visual

- [ ] **Estado batería actual**: foto al móvil ANTES de tocar nada.
- [ ] Si la base del portátil está **deformada** (panza visible) o el **touchpad levantado** → batería hinchada. Confirmar al cliente, valorar urgencia.
- [ ] **Marcas de daño** existentes en el portátil: golpes, arañazos, falta de tornillos, tapa torcida. Foto y anotar (cubrir culo).

### Paso 2 — Resguardo firmado

- [ ] Resguardo papel: descripción + serie + estado físico inicial + servicio a hacer + precio total acordado + fecha entrega.
- [ ] Cliente firma. Foto del resguardo.

### Paso 3 — BatteryReport actual

1. Abrir consola admin en el portátil del cliente:
   ```
   powercfg /batteryreport /output "C:\bateria_antes.html"
   ```
2. Abrir HTML resultante. Apuntar:
   - **Design Capacity**: capacidad de diseño (mWh).
   - **Full Charge Capacity**: capacidad real actual (mWh).
   - **% Wear**: degradación. >40% = batería muy gastada.
3. Captura para enseñar al cliente comparativa post-cambio.

---

## Durante — Despiece

### Paso 1 — Apagar y prepararse

1. Apagar portátil completamente (no suspender).
2. Desenchufar cargador.
3. Dejar pasar **5-10 min** para que se descarguen condensadores.
4. Mesa despejada, paño suave debajo del portátil para no rayar tapa al voltearlo.
5. Si la batería está hinchada → guantes + bolsa ignífuga preparada.

### Paso 2 — Quitar tornillos tapa inferior

1. Localizar **TODOS los tornillos** de la tapa inferior:
   - Algunos están **debajo de patas de goma** que hay que despegar (típico HP / Lenovo).
   - Algunos son **cortos**, otros **largos**. ANOTAR posición de cada uno (foto + bandeja imantada con casillas).
2. Quitar tornillos uno a uno.
3. **NO forzar la tapa** todavía.

### Paso 3 — Abrir tapa

1. **Púa de plástico** insertada por una esquina (no esquinas con bisagra).
2. Recorrer todo el perímetro despegando los **clips de plástico internos**. Suena "clic" cada vez que se libera uno.
3. Levantar tapa con cuidado.
4. **Si la tapa no sale** → puede haber tornillo escondido (debajo de pegatina, debajo de tapa de RAM, etc.). NO forzar, buscar.

### Paso 4 — Localizar y desconectar batería

1. Identificar la **batería** (rectángulo grande, 60-90% del interior).
2. **Identificar el conector batería** (cable blanco/marrón con clip pequeño que va a la placa base).
3. **DESCONECTAR PRIMERO el conector batería** antes de desatornillarla. Esto **corta toda corriente** al portátil:
   - Algunos clips se sueltan tirando hacia arriba.
   - Otros tienen pestaña que hay que palanquear.
   - **NO tirar del cable**, siempre del conector.
4. Anotar la **orientación del conector** (foto).

### Paso 5 — Desatornillar y sacar batería vieja

1. Tornillos de fijación batería (suelen ser 4-8).
2. Sacar batería **horizontalmente**, no curvar.
3. Si está hinchada y no sale → NO forzar más, valorar caso. A veces hay que quitar más componentes alrededor.
4. **Bolsa ignífuga / antiestática** para la batería vieja inmediatamente.

---

## Durante — Instalación batería nueva

### Paso 6 — Comprobar pieza nueva

1. Caja precintada, modelo coincide con la cotizada.
2. **Verificar voltaje y mAh** en la etiqueta (debe coincidir con la original o ser muy parecida).
3. Visualmente: sin abolladuras, conector limpio.

### Paso 7 — Instalar

1. Colocar batería en su sitio respetando orientación original.
2. Atornillar (tornillos de la batería, **no a tope**, firme).
3. **Conectar conector** al final, una vez batería ya atornillada.

### Paso 8 — Cerrar tapa

1. Recolocar tapa inferior, alinear bien antes de presionar.
2. **Presionar el perímetro** para encajar los clips de plástico (suena "clic" cada vez que entra uno).
3. Atornillar tapa con TODOS los tornillos en sus posiciones originales (cortos vs largos, importante).
4. Recolocar patas de goma si las despegaste (suelen pegarse de nuevo, si pierden adhesivo → punto pequeño de pegamento UHU).

---

## Durante — Software de validación

### Paso 9 — Primer arranque

1. Conectar cargador.
2. Encender portátil.
3. Si arranca normalmente → ✅
4. Si NO arranca:
   - Comprobar conector batería bien metido.
   - Comprobar tornillos no estén forzados sobre la placa.
   - Comprobar tapa cerrada del todo.

### Paso 10 — Calibración batería nueva

1. **Cargar al 100%** completamente con portátil encendido (1-3h).
2. **Desconectar cargador**, dejar usar el portátil hasta que se apague solo (descarga total).
3. **Volver a cargar al 100%** sin tocar.

Esto re-inicializa la lectura del controlador de carga. Si no se hace, el porcentaje puede mostrar errores los primeros días.

### Paso 11 — BatteryReport post-cambio

1. Consola admin:
   ```
   powercfg /batteryreport /output "C:\bateria_despues.html"
   ```
2. Comparar con el "antes":
   - **Full Charge Capacity** debería ser ≥ 95% del Design Capacity (en batería nueva).
   - **Wear**: <5%.
3. Si la nueva muestra wear alto inmediato (>10%) → pieza defectuosa, devolver y pedir otra.

### Paso 12 — Configuración Windows recomendada

1. Win + I → Sistema → Energía y batería.
2. Activar **Recomendaciones de energía**: equilibrado.
3. **Smart Charging** (en portátiles modernos Lenovo / HP / Dell): activar para limitar carga al 80% en uso enchufado, alargar vida batería.
4. **Modo ahorro batería**: configurar a 20% para que se active solo.

---

## Al cerrar

- [ ] Foto del portátil cerrado.
- [ ] Demostrar al cliente:
  - BatteryReport antes vs después (capacidad real subida significativamente).
  - Portátil enciende, descargando vs cargando se actualiza.
  - Tiempo estimado restante con uso normal.
- [ ] **Recordar al cliente** la calibración (3 ciclos completos al principio).
- [ ] **Batería vieja**:
  - Si hinchada / dañada → **transporte en bolsa ignífuga** y entrega a punto limpio o tienda con reciclaje pilas.
  - Si sana pero gastada → punto limpio / contenedor pilas.
  - **NUNCA tirar a basura normal** ni dejar al cliente que la tire.
- [ ] Cobrar **MO 80-150€** + pieza según presupuesto cerrado.
- [ ] Lanzar `entrega.bat` → factura `MPC-2026-XXXX`.
- [ ] Frase cierre: **"Garantía 30 días en mano de obra. La batería en sí tiene 1 año garantía del fabricante (depende marca). Si en este mes el portátil tiene problemas relacionados con la batería, vuelvo gratis."**

---

## Errores frecuentes

_Pendiente actualizar tras 5 visitas reales._

Anticipados:
- **Modelo incorrecto de batería**: portátiles tienen variantes con conectores distintos (mismo modelo año diferente puede llevar batería distinta). Verificar P/N (part number) en la etiqueta de la batería original antes de pedir.
- **Batería compatible barata** que dura 6 meses: avisar al cliente antes de comprar piezas baratas. Marcas decentes: Tepulseil, Akku-Net, batería original fabricante.
- **Tornillos perdidos en clientes**: bandeja imantada y/o vasito siempre. Si pierdes uno → tornillo M2 o M2.5 según modelo, los tengo de repuesto en mochila.
- **Cliente que dice "antes me duraba 8h"** y la nueva dura 4h: el portátil moderno consume más por software. La batería puede estar OK pero el sistema usa más recursos. BatteryReport es prueba objetiva.
- **Batería hinchada que no sale fácil**: NO forzar. Si está pegada al teclado/touchpad por la presión → valorar si hay daño colateral, presupuesto extra.
- **Portátiles ultradelgados (Lenovo Yoga, Asus Zenbook)** con baterías cosidas a la carcasa: despiece complejo. Cobrar MO 130-150€ por la dificultad.

---

## Tiempo total

- Portátil estándar (Lenovo ThinkPad, HP ProBook, Acer básico): **45-60 min**.
- Portátil ultradelgado (Yoga, XPS, Zenbook): **75-90 min**.
- Calibración: 3-6h después (no cuenta como tiempo del técnico, el cliente lo hace solo).
- BatteryReport: 5 min antes y 5 min después.

---

## Reglas críticas

🔴 **DESCONECTAR conector batería ANTES de desatornillar.** Riesgo cortocircuito.
🔴 **Foto de cada paso del despiece.** Por si pierdes alguna pieza o cable.
🔴 **Batería vieja en bolsa ignífuga** si está hinchada. Riesgo incendio durante transporte.
🔴 **NUNCA reutilizar batería hinchada** "por si aguanta un poco más". Riesgo real al cliente.
🔴 **Verificar pieza nueva** antes de instalar (modelo, voltaje, mAh).
🔴 **NO apretar tornillos batería a tope.** Firme suficiente.
🔴 **BatteryReport antes y después.** Documentación objetiva.
🔴 **NO tocar la batería vieja con manos sin protección si está hinchada.** Si la celda revienta libera electrolito corrosivo.
🔴 **Calibración 3 ciclos al cliente.** Indicar por WhatsApp al final.
🔴 **NO instalar batería falsificada / muy barata sin avisar.** Cliente decide informado, sino pierde garantía y dura 6 meses.
🔴 **Reciclaje obligatorio** de la batería vieja en punto limpio. NO basura.
