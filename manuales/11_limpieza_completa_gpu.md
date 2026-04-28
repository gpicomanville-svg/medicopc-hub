# Limpieza Completa + Servicing GPU (120€)

> Tiempo realista: **3-4h**
> Bloque tarifa: **B — Mantenimiento Software**
> Modalidad: **taller por defecto** · domicilio +25€

---

## Qué es y qué NO es

**SÍ es:** Limpieza Completa estándar (80€) **PLUS** desmontaje completo de la GPU dedicada del PC, repasar pasta térmica del chipset gráfico, cambiar pads térmicos del VRAM/VRM si están secos, limpiar ventiladores GPU. Ideal para PCs gaming con 3+ años cuyas temperaturas GPU han subido de 65-70°C → 80-90°C en juego.

**NO es:**
- ❌ **PCs sin GPU dedicada** (iGPU integrada Intel/AMD): aplicar Limpieza Completa 80€ sin servicing GPU.
- ❌ **Reballing GPU** (rebolear chip BGA): derivar a partner microsoldadura.
- ❌ **Reparación GPU rota** (artefactos en pantalla, no enciende): NO se repara, hay que cambiar.
- ❌ **Pack Gaming Tune-Up 150€** que incluye undervolt + benchmarks + config Steam (servicio más completo).

**Cuándo recomendar este servicio vs Pack Gaming Tune-Up:**
- Si cliente solo quiere bajar temperaturas GPU → **120€ Limpieza+GPU** suficiente.
- Si cliente quiere bajar temps **+** tunear ventiladores **+** undervolt **+** benchmarks → **150€ Pack Gaming Tune-Up**.

---

## Antes (preparación)

### Confirmar por WhatsApp
- [ ] **Modelo GPU** (foto del Administrador de tareas → Rendimiento → GPU). Necesario para saber cómo se desmonta y qué tipo de pads térmicos lleva.
- [ ] **Síntoma**: ¿salta el ventilador a tope siempre? ¿Throttling en juegos? ¿Temperaturas registradas con MSI Afterburner / HWiNFO?
- [ ] **Edad GPU**: <2 años no merece, sigue de fábrica. >3 años sí.
- [ ] **¿Tiene garantía vigente del fabricante?** Si sí → ⚠️ desmontar la rompe. Avisar al cliente. Si insiste → resguardo firmado con cláusula explícita.

### Material en mochila / taller
- [ ] **Pasta térmica Arctic MX-6 o Kryonaut** (NO MX-4 vieja, NO Liquid Metal en GPU).
- [ ] **Pads térmicos Thermalright** o equivalentes en grosores variados (0.5mm, 1mm, 1.5mm, 2mm).
- [ ] **Alcohol isopropílico 99%** + paño microfibra + bastoncillos.
- [ ] **Goma de borrar limpia** (para limpiar contactos PCIe si toca).
- [ ] **Destornilladores precision** Phillips PH00, PH0, PH1, Torx T6, T7, T8 (varía por modelo GPU).
- [ ] **Linterna**.
- [ ] **Bandeja imantada** para tornillos.
- [ ] **Cepillo antiestático** o brocha pelo natural.
- [ ] **Bote aire comprimido** o **aspirador de mano antiestático** (Datavac estilo).
- [ ] **Cinta adhesiva removible** o pegatinas para marcar tornillos por zona (las GPUs tienen tornillos de tamaños distintos en sitios distintos).
- [ ] **HWiNFO** y **FurMark** o **Heaven** en USB Arsenal para test térmico antes/después.

---

## Al llegar (recogida domicilio) o al recibir el equipo (taller)

- [ ] Foto general del PC y de la GPU dedicada visible por la ventana lateral si aplica.
- [ ] **Test térmico inicial** en el equipo del cliente (en domicilio si recoges, en taller si trae): lanzar Heaven Benchmark 10 min → apuntar temperatura GPU máxima en HWiNFO. Esto será la "antes".
- [ ] Resguardo firmado con cláusula GPU (nº serie GPU + estado + qué se va a hacer).
- [ ] Llevar a taller si se acordó.

---

## Durante — Limpieza Completa estándar (parte 1)

Misma metodología que el manual 01 Limpieza Completa, resumido aquí:

### Software (90 min)
1. RKill → AdwCleaner → Malwarebytes (escaneo completo).
2. Limpieza Windows nativa (cleanmgr, Storage Sense, programas).
3. Autoruns (limpiar arranque).
4. BleachBit (caché, papelera, logs).
5. Drivers actualizados (DDU si hay sospecha drivers gráficos rotos).

### Físico interior (60 min)
1. Tapa lateral del sobremesa (o tapa inferior portátil).
2. Aspirado interior con aspirador antiestático **NUNCA** uno doméstico.
3. Aire comprimido por filtros y rejillas.
4. **Quitar disipador CPU**, limpiar pasta vieja, aplicar pasta nueva (grano arroz centro), recolocar disipador.
5. Limpiar ventiladores chasis con bastoncillo.
6. **NO tocar fuente** (componentes activos peligrosos).

### Físico exterior (30 min)
1. Pantalla, teclado, ratón, carcasa exterior con microfibra.

---

## Durante — Servicing GPU (parte 2, lo nuevo)

### Paso 1 — Desmontar GPU del PC

1. PC apagado, desenchufado, descargado (apretar power 5 segundos).
2. Quitar tornillo de fijación de la GPU al chasis (parte trasera, donde están los puertos HDMI/DP).
3. Desconectar cable PCIe de alimentación de la GPU (8 pines o 6+2 según modelo).
4. Empujar la pestaña del slot PCIe x16 hacia abajo y tirar la GPU **suavemente** hacia arriba.
5. Llevar la GPU a la mesa de trabajo, sobre superficie antiestática (alfombrilla goma, NO directo sobre madera/metal).

### Paso 2 — Foto de la GPU intacta

Foto detallada de:
- Tornillos del backplate (marcando cada uno).
- Cableado del ventilador GPU (3-4 pines).
- Pads térmicos visibles por las ranuras (color, posición).

Esto sirve por si algo se pierde / hay que recolocar.

### Paso 3 — Quitar el shroud (carcasa de plástico con ventiladores)

1. Identificar los tornillos del shroud por la parte delantera y por la parte trasera (backplate).
2. Quitarlos uno a uno, marcando posición en bandeja imantada (4 mm vs 6 mm vs 8 mm, NO mezclar).
3. **Desconectar cable ventiladores** del PCB (cuidado, conector pequeño y frágil).
4. Levantar el shroud + ventiladores. Apartar.

### Paso 4 — Quitar el backplate (chapa metálica trasera)

1. Tornillos visibles por la parte trasera del PCB.
2. Levantar backplate. **Atención**: a veces hay pads térmicos pegados al backplate que conectan VRAM trasera. Si están secos / despegados → cambiar.

### Paso 5 — Quitar el disipador del chip GPU

1. Localizar los tornillos del disipador alrededor del chip GPU (suelen ser 4, en formato cruz, con muelles).
2. Aflojar **siempre en patrón cruz** (1, 3, 2, 4) para no torcer la presión.
3. Levantar el disipador **suavemente**. Si hace resistencia es porque la pasta está pegada → mover ligeramente lateral, NUNCA tirar fuerte.
4. Una vez fuera → ver el chip GPU expuesto + chips VRAM alrededor + componentes VRM.

### Paso 6 — Limpiar pasta vieja del chip GPU

1. Microfibra + alcohol isopropílico 99%.
2. Limpiar el chip GPU dejándolo brillante.
3. Limpiar la base del disipador (parte cobre o vapor chamber) dejándola brillante.
4. **Inspeccionar**: si la pasta original era líquida (Liquid Metal en algunas RTX 3000 Founders) → ⚠️ NO la cambies sin saber lo que haces. Riesgo de cortocircuito. Volver a montar y avisar al cliente.

### Paso 7 — Inspeccionar y cambiar pads térmicos

#### Pads del VRAM (alrededor del chip GPU)
1. Mirar cada pad: color, grosor, condición.
2. **Si están blandos, oleosos, descoloridos** → cambiar.
3. **Si están secos, agrietados** → cambiar obligatorio.
4. **Si están en buena condición** → reusar.

#### Cómo cambiar
1. Despegar pad viejo cuidadosamente (no rasgar PCB).
2. Limpiar resto con alcohol.
3. Medir grosor original con calibre o regla milimétrica.
4. Cortar pad nuevo del mismo grosor con cúter, igual tamaño que el viejo.
5. Pegar pad nuevo en la posición exacta del viejo. Quitar plástico protector ambos lados.

#### Pads VRM y otros componentes
1. Si los hay (algunas tarjetas tienen VRM separados) → mismo proceso.
2. Si solo hay 1-2 pads → reemplazar suelto.

### Paso 8 — Aplicar pasta nueva al chip GPU

1. Pasta MX-6 o Kryonaut: punto del tamaño de **un grano de arroz** en el centro del chip.
2. Para chips grandes (RTX 4080+, RX 7900) → cantidad un poco mayor pero NO esparcir.
3. Algunos técnicos prefieren método "X" o "spread" (esparcir con tarjeta), pero el método "punto centro" funciona bien en chips cuadrados/rectangulares estándar.
4. **NUNCA Liquid Metal** en GPU sin experiencia (necesita barniz aislante alrededor, riesgo cortocircuito muy alto).

### Paso 9 — Limpiar ventiladores GPU

1. Aire comprimido + cepillo blando.
2. **Importante**: bloquear las aspas con un dedo mientras soplas (si las dejas girar libres se puede dañar el rodamiento).
3. Inspeccionar rodamientos: si oyes ruido al girar manualmente → ventilador agotado, recomendar cambio (pieza ~15-25€ + MO).

### Paso 10 — Remontar GPU

Orden inverso:
1. Disipador sobre el chip GPU. Atornillar en patrón cruz, **apretado pero NO a tope**.
2. Reconectar cable ventiladores al PCB.
3. Backplate con tornillos correctos.
4. Shroud + ventiladores.
5. Tornillos del shroud.

### Paso 11 — Reinstalar GPU en el PC

1. Insertar en slot PCIe x16 hasta que la pestaña haga clic.
2. Tornillo trasero al chasis.
3. Cable PCIe alimentación 8 pines / 6+2.
4. Comprobar que ningún cable interfiere con los ventiladores.

---

## Durante — Verificación post-servicing

### Paso 1 — Arrancar y comprobar que GPU se detecta

1. Cerrar PC, encender.
2. Llegar a Windows. Abrir **Administrador de dispositivos → Adaptadores de pantalla**.
3. Comprobar que la GPU aparece sin signo de admiración amarillo.
4. Si no se detecta o hay error → apagar, comprobar conexión PCIe + alimentación.

### Paso 2 — Test térmico DESPUÉS

1. **HWiNFO64** → sensores → encontrar GPU → Temperatura.
2. **Heaven Benchmark 10 min** o **FurMark 10 min** (estresa más).
3. Apuntar temperatura GPU máxima.
4. Comparar con la "antes" del paso del cliente.
5. **Mejora esperada**: 5-15°C menos a plena carga. Si no mejora o empeora → algo se ha hecho mal, revisar pasta y pads.

### Paso 3 — Comprobar ventiladores

1. En el bench, escuchar los ventiladores GPU. Si hacen ruido raro nuevo → desmontar y revisar.
2. Comprobar curva ventiladores en MSI Afterburner si está instalado.

---

## Al cerrar

- [ ] Imprimir o guardar **comparativa antes/después** (HWiNFO log, captura): "antes 87°C, ahora 73°C".
- [ ] Enseñárselo al cliente. Esto es lo que justifica los 120€ vs 80€.
- [ ] Devolver el PC al cliente o configurar entrega.
- [ ] Cobrar **120€** Bizum o efectivo.
- [ ] Lanzar `entrega.bat` → factura `MPC-2026-XXXX` con concepto "Limpieza Completa + Servicing GPU".
- [ ] Frase cierre: **"GPU repasada y termalmente sana. Garantía 30 días en mano de obra. Si las temperaturas vuelven a subir o el ventilador hace ruido raro en este mes, vuelvo gratis."**

---

## Errores frecuentes

_Pendiente actualizar tras 5 visitas reales._

Anticipados:
- **GPU con Liquid Metal de fábrica** (RTX 3080 Ti / 3090 Founders, algunas portátiles MSI): NO la toques sin experiencia. Volver a montar sin tocar pasta. Cobrar solo Limpieza Completa 80€.
- **Pads térmicos en GPU moderna (RTX 4070+ / RX 7000)**: muchas vienen con pads finos de calidad mediocre. Reemplazo con Thermalright Odyssey gana 5-10°C en VRAM.
- **Tornillos del disipador agarrotados**: si no aflojan con destornillador correcto → **NO forzar**. Llamar al cliente, devolver con disculpa, no romper.
- **Cliente nervioso** porque "se le rompe la garantía": preguntar siempre antes. Si tiene <2 años → mejor NO hacer servicing, devolver al fabricante.
- **GPU portátil**: ⚠️ desmontar GPU portátil es un nivel extra de complicación (heatpipes compartidos con CPU, pads no estándar). En portátiles → Pack Gaming completo o Limpieza Completa, no servicing GPU separado.

---

## Tiempo total

- Limpieza Completa parte 1: **2-2.5h**.
- Servicing GPU parte 2: **1-1.5h**.
- Total: **3-4h**.

---

## Reglas críticas

🔴 **NO desmontar GPU con garantía vigente del fabricante** sin avisar al cliente y firma de aceptación. Rompe garantía.
🔴 **NO Liquid Metal** en GPU sin experiencia. Riesgo cortocircuito altísimo.
🔴 **Apretar tornillos disipador en patrón cruz** y con presión moderada. Apretar a tope torciendo PCB = GPU rota.
🔴 **Foto antes y durante el desmontaje** obligatoria. Protección si algo no encaja al recolocar.
🔴 **Marcar tornillos por zona** en bandeja imantada. Mezclar tornillos largos donde van cortos = perforar PCB.
🔴 **Test térmico antes y después** obligatorio. Sin medición la mejora no se demuestra.
🔴 **Si tornillos no aflojan** → NO forzar, devolver con disculpa. Mejor perder 0€ que romper GPU del cliente.
🔴 **Limpiar contactos PCIe con goma de borrar limpia** si se ven oxidados. NO con limpiacontactos químico (deja residuo).
🔴 **NO recomendar este servicio en GPU <2 años**. Sale más caro que el beneficio térmico.
