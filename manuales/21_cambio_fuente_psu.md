# Cambio fuente alimentación PC sobremesa (MO desde 45€ + pieza · consultar potencia)

> Tiempo realista: **45-90 min** (taller o domicilio según caso)
> Bloque tarifa: **C — Hardware Mano de Obra** (servicio NUEVO en v3.2)
> Modalidad: domicilio sin recargo

---

## Qué es y qué NO es

**SÍ es:** sustitución de la fuente de alimentación (PSU) en PC sobremesa por avería (no enciende), por insuficiencia de potencia (cliente añade GPU nueva más exigente), o por necesidad de upgrade (fuente vieja sin certificación).

**NO es:**
- ❌ **Cargador / fuente de portátil**: eso es **Cargador portátil genérico 40€** (G_piezas).
- ❌ **SAI / UPS**: no se cambia, se vende como periférico aparte.
- ❌ **Fuente para PC industrial / servidor**: derivar.

**Por qué "consultar potencia":** la pieza varía mucho:
- **500W** (Corsair CV / be quiet! System Power): **65€** — PCs ofimática + GPU básica.
- **650W** (Corsair CX): **85€** — PCs gaming RTX 4060/4070.
- **750W** (Corsair RM): **110€** — PCs gaming high-end RTX 4080.
- **850W+** (Corsair HX, Seasonic Focus): **130-180€** — workstations + GPUs top.

**Cálculo potencia recomendada:**
- CPU TDP + GPU TBP + 100W margen = potencia mínima.
- Ej: i5-13400 (65W) + RTX 4070 (200W) + 100W = **365W** → recomendar 650W (margen, eficiencia, futuro upgrade).

---

## Antes (preparación material)

### Confirmar por WhatsApp
- [ ] **Marca placa base + CPU + GPU actual del cliente** (datos para calcular potencia).
- [ ] **Síntoma exacto:**
  - PC no enciende → diagnóstico previo confirmado fuente muerta.
  - PC se apaga jugando → fuente insuficiente (típico tras añadir GPU nueva).
  - PC enciende pero apaga aleatorio → fuente con condensadores envejecidos.
- [ ] **Foto interior PC** abierto (ver espacio caja, tipo conectores, configuración cables).
- [ ] **Cliente quiere upgrade** (GPU nueva próximamente)? → recomendar margen +200W.

### Cotización
- [ ] Calcular potencia recomendada.
- [ ] Pieza específica + MO 45€ = total.
- [ ] Plazo: si pieza en stock típico (CV/CX 500-650W) entrega rápida; si custom, 2-4 días.

### Material taller/visita
- [ ] **Kit destornilladores** Phillips PH1 + PH2.
- [ ] **Pulsera ESD**.
- [ ] **Linterna** (cajas mal iluminadas).
- [ ] **Bridas plástico pequeñas** (recogida cables al final).
- [ ] **Multímetro** (test fuente vieja con clip si hay duda diagnóstico previo).

---

## Al llegar / al recibir equipo

- [ ] Foto exterior PC.
- [ ] Resguardo firmado.
- [ ] **Test fuente actual con clip** (si dudas):
  - Desconectar fuente del placa.
  - Puente con clip metálico **cable verde** del conector ATX 24-pin a **cualquier cable negro**.
  - Encender fuente.
  - Si ventiladores fuente arrancan → fuente OK eléctricamente.
  - Si NO arrancan → fuente muerta confirmada.

---

## Durante — Físico paso a paso

### Paso 1 — Apagar y desconectar todo
1. Apagar PC, esperar 2 min (descargar condensadores).
2. **Switch trasero de la fuente a OFF** (símbolo 0).
3. **Desenchufar cable corriente**.
4. Desenchufar cualquier cable USB / monitor / red del PC.

### Paso 2 — Acceso

1. Quitar **tapa lateral** del PC (1-2 tornillos traseros).
2. **Foto del estado actual** (críticamente importante: cómo van conectados los cables, por dónde pasan).

### Paso 3 — Desconectar cables fuente vieja

Lista de cables a desconectar (orden recomendado):
1. **ATX 24 pin** al placa base (conector grande).
2. **EPS 4+4 pin** al placa (alimentación CPU, esquina superior placa).
3. **PCIe 6+2 pin** a la GPU (cable múltiple a la tarjeta gráfica).
4. **SATA** a discos duros / SSD SATA (cables planos).
5. **Molex** a ventiladores antiguos (conector blanco 4 pin) — si hay.
6. **CPU fan** se queda al placa (no es de la fuente).

⚠️ Algunos PCs llevan **cable management** detrás del placa: anotar / fotografiar cómo van los cables antes de tirar.

### Paso 4 — Sacar fuente vieja

1. **4 tornillos** parte trasera del PC fijan la fuente al chasis.
2. Quitarlos.
3. **Sacar fuente** desde dentro de la caja (suele salir por dentro, no por fuera).

### Paso 5 — Instalar fuente nueva

1. **Comprobar potencia y certificación** etiqueta de la fuente nueva (por si pieza equivocada en caja).
2. **Insertar fuente nueva** en el hueco, ventilador hacia abajo (filtro polvo en el suelo del chasis) o hacia arriba según diseño caja:
   - Caja moderna con compartimento separado fuente (basement) → ventilador HACIA ABAJO (toma aire por debajo).
   - Caja vieja sin compartimento → ventilador HACIA ARRIBA (toma aire del interior).
3. **Atornillar** los 4 tornillos traseros.

### Paso 6 — Conectar cables nueva

Si la fuente es **modular** o **semi-modular**:
1. **Conectar primero los cables a la fuente** que vas a usar:
   - ATX 24 pin (siempre).
   - EPS 4+4 pin (siempre).
   - PCIe 6+2 (si hay GPU dedicada).
   - SATA (cuántos discos).
2. **NO conectar Molex** si no hace falta (estética).

Conectar al hardware:
1. **ATX 24 pin** al placa base.
2. **EPS 4+4 pin** al socket CPU del placa.
3. **PCIe** a GPU (verificar que clip cierra).
4. **SATA** a discos.

### Paso 7 — Cable management

1. **Pasar cables por la parte trasera** de la bandeja del placa (si la caja tiene management).
2. **Bridas** en grupos pequeños.
3. Asegurarse de que **ningún cable toca ventiladores** o disipador.
4. **Foto del estado final** (comparar con foto inicial).

### Paso 8 — Cierre y test

1. **Tapa lateral, tornillos**.
2. **Switch fuente a ON**.
3. Conectar cable corriente, monitor, teclado.
4. **Pulsar power**.
5. PC enciende → POST → BIOS o Windows.

---

## Test post-instalación

1. **Llegar a Windows**.
2. **HWiNFO** → pestaña sensors:
   - Voltajes 12V / 5V / 3.3V dentro de tolerancia (±5%).
   - Temperatura sistema OK.
3. **Stress test** 10 min:
   - **Prime95 small FFTs** (CPU 100%) + **FurMark** (GPU 100%) simultáneo.
   - Comprobar que NO se reinicia / apaga.
   - Voltajes estables bajo carga.
4. **Apagar/encender 3 veces** confirmar arranque limpio cada vez.

---

## Al cerrar (entrega)

- [ ] **Demo arranque** delante cliente.
- [ ] **Mostrar HWiNFO** voltajes estables.
- [ ] Cobrar **MO 45€+ + pieza X€** Bizum/efectivo.
- [ ] `entrega.bat` → factura desglosada.
- [ ] **Fuente vieja**: preguntar si la quiere para reciclar o me la quedo (ocasionalmente sirve diagnóstico).
- [ ] Hook cierre: *"Garantía 30 días en mano de obra. Pieza con garantía fabricante (Corsair CX 5 años, RM 10 años)."*
- [ ] **Recordar al cliente:**
  - Si nota apagados o cuelgues raros volver pronto (dentro garantía).
  - Si en futuro cambia GPU por una más potente, valorar si la fuente actual aguanta (yo le miro gratis).

---

## Errores frecuentes

_Pendiente actualizar tras 5 visitas reales._

Casos anticipados:
- **Cable EPS olvidado**: PC enciende ventiladores pero no postea. Causa #1 de "PC no arranca tras cambio fuente".
- **PCIe mal conectado** a GPU: GPU no recibe potencia, monitor sin señal aunque PC enciende.
- **Modular: cable PCIe enchufado a slot CPU de la fuente**: ⚠️ destruye GPU. NO mezclar cables entre fuentes (cada fabricante tiene pinout distinto AUNQUE el conector parezca igual).
- **Switch trasero olvidado en OFF**: cliente piensa que la fuente está rota. Risa, comprobar antes de gritar.
- **Fuente nueva con menos potencia que la vieja**: si cliente añade GPU futura, no aguanta. Calcular bien antes.

---

## Tiempo total

- **45 min** caso simple (fuente no modular, configuración básica).
- **60-90 min** caso modular o con cable management complejo.

---

## Reglas críticas

🔴 **NUNCA mezclar cables modulares** entre fuentes de marcas distintas. Pinout NO es universal aunque el conector sea igual. Cable Corsair en fuente Seasonic = humo.
🔴 **Switch fuente a OFF y desenchufar 2 min** antes de tocar nada interno.
🔴 **Cable EPS 4+4 al placa SIEMPRE.** El cliente recordará que su PC no arrancó si lo olvidas.
🔴 **Calcular potencia con margen futuro.** Si cliente puede añadir GPU mejor en 1-2 años, recomendar +150W.
🔴 **Pulsera ESD recomendable.** Especialmente en invierno con mucha estática.
🔴 **Test stress 10 min antes de entregar** confirma que no es un retorno garantía.
🔴 **Fuentes baratas sin marca (Tacens viejas, NOX baratas, marca blanca) NUNCA.** Riesgo real de morir y llevar consigo la placa.
🔴 **Foto antes/después** estado interno PC. Cubre si aparecen daños "sospechosos".
