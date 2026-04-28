# Cambio teclado portátil (desde 70€ MO + pieza · consultar modelo)

> Tiempo realista: **1-3h** (taller)
> Bloque tarifa: **C — Hardware Mano de Obra**
> Modalidad: **taller siempre** (variabilidad alta entre modelos)

---

## Qué es y qué NO es

**SÍ es:** sustitución completa del teclado interno de un portátil (teclas no responden, líquido derramado, teclas pegadas/rotas, retroiluminación rota, layout cambiado).

**NO es:**
- ❌ Teclados externos USB/inalámbricos → cliente compra y conecta solo, no es servicio.
- ❌ Mac portátiles con teclado mariposa o butterfly → derivar (procedimiento muy específico, riesgo alto).
- ❌ Teclados mecánicos custom para gaming sobremesa → no aplicable.

**Por qué "consultar modelo":** los teclados portátiles van **soldados al chasis o al palmrest** en muchos modelos modernos. Procedimiento varía drásticamente:
- **Modelos fácil** (HP / Lenovo IdeaPad antiguos): teclado clipsado, 15 min.
- **Modelos medios** (ASUS Vivobook, Acer Aspire): teclado atornillado al palmrest desde el reverso, 1h desmontaje.
- **Modelos difícil** (Dell XPS, ASUS ZenBook, MacBook): teclado remachado al palmrest → cambiar palmrest entero (200-400€ pieza).

**Pieza típica:**
- Teclado genérico ASUS / HP / Lenovo gama media: **50-80€** (G_piezas).
- Teclado retroiluminado RGB: **80-150€**.
- Palmrest+teclado completo (modelos remachados): **200-400€** ⚠️ avisar al cliente y reconsiderar.

**Total ejemplo:** ASUS Vivobook 15.6" estándar = 70€ MO + 60€ pieza = **130€**.

---

## Antes (preparación material)

### Confirmar por WhatsApp ANTES de aceptar
- [ ] **Marca, modelo y serial** del portátil.
- [ ] **Foto teclado** estado actual.
- [ ] **Síntomas exactos:**
  - Teclas no responden (físicas o softwarera).
  - Líquido derramado (cuándo, qué, hace cuánto).
  - Teclas pegadas o rotas.
  - Retroiluminación.
- [ ] **Probar teclado USB externo** ANTES de presupuestar:
  - Si externo escribe normal → teclado interno físico.
  - Si externo TAMBIÉN falla → puede ser controlador/driver (servicio software, no cambio).

### Investigación pieza ANTES de cotizar
- [ ] Buscar en **iFixit / YouTube despiece "[modelo] keyboard replacement"** para ver:
  - Si es clipsado (10 min) o remachado (palmrest entero).
  - Tornillos accesibles desde abajo o desde arriba.
  - Tiempo realista del cambio.
- [ ] Si es **remachado** → avisar al cliente del coste real (palmrest 200€+) antes de aceptar. Muchas veces no compensa vs portátil nuevo.
- [ ] Cotizar pieza específica + MO 70€.

### Material taller
- [ ] **Kit destornilladores precision** PH00/PH0 + Pentalobe T5.
- [ ] **Púas plástico**.
- [ ] **Bandeja imantada** tornillos (cantidad alta).
- [ ] **Pulsera ESD**.
- [ ] **Lupa LED** (conectores ZIF teclado son MUY pequeños y delicados).
- [ ] **Pinzas finas** antiestáticas.

---

## Al recibir equipo (taller)

- [ ] Foto frontal con teclado actual + estado físico.
- [ ] Resguardo firmado.
- [ ] **Test inicial software**: USB externo escribir → confirmar que software OK, problema físico.

---

## Durante — Físico paso a paso

### Caso A — Teclado clipsado desde arriba (modelos fáciles)

#### Paso 1 — Localizar clips
1. Apagar y desenchufar.
2. **Despegar batería** del placa.
3. Mirar el perímetro del teclado: clips visibles arriba y abajo.

#### Paso 2 — Desclipsar
1. Insertar púa en una esquina del teclado, hacer palanca suave hacia arriba.
2. Recorrer todo el perímetro liberando clips.
3. Teclado se eleva 1-2 cm.

#### Paso 3 — Desconectar
1. Bajo el teclado: cable plano (FFC) hacia el placa.
2. **Levantar pestaña conector ZIF** → tirar del cable suave.
3. Si lleva conector retroiluminación: igual.

#### Paso 4 — Conectar nuevo
1. Cable FFC nuevo → conector ZIF → cerrar pestaña.
2. Clipsar teclado nuevo de un extremo, ir presionando perímetro hasta que cierra todo.

### Caso B — Teclado atornillado desde abajo (medio)

#### Paso 1 — Acceder por la tapa inferior
1. Quitar **todos los tornillos tapa inferior** (anotar tamaños distintos en bandeja imantada).
2. **Despegar tapa con púa** desde una esquina.
3. Vista interior visible.

#### Paso 2 — Localizar tornillos teclado
1. Bajo el placa principal o el palmrest, hay **tornillos pequeños** que sujetan el teclado al chasis. Suele haber 8-15 tornillos.
2. Quitarlos uno a uno, anotar posiciones.

#### Paso 3 — Desconectar y sacar
1. Cable FFC del teclado al placa → ZIF abrir → tirar suave.
2. Levantar el teclado **desde arriba** (lado teclas) con cuidado.

#### Paso 4 — Montar nuevo
1. Insertar teclado nuevo desde arriba.
2. Tornillos posiciones originales.
3. Cable FFC al ZIF.
4. Tapa inferior, tornillos.

### Caso C — Teclado remachado al palmrest (difícil)

⚠️ **Si es este caso → recomendar al cliente que valore vs comprar portátil nuevo. Suele no compensar.**

#### Si aún así sigue:
1. Desmontaje completo del portátil (placa, batería, ventiladores fuera).
2. Palmrest + teclado nuevo entero como conjunto.
3. Reensamblar todo.
4. Tiempo: 2-3h.

---

## Test ANTES de cerrar

1. **Conectar batería y cargador**.
2. **Encender portátil**, llegar a Windows.
3. **Test todas las teclas**: usar **PassMark KeyboardTest** o web `keyboardtester.com`:
   - Pulsar todas las teclas una por una.
   - Verde = funciona. Roja = no detectada.
   - Si alguna roja → cable mal conectado o teclado defectuoso.
4. **Test combinaciones**: Shift, Ctrl, Alt, Fn + teclas multimedia.
5. **Test retroiluminación** si aplica: Fn + tecla iluminación, comprobar todos los niveles.

---

## Al cerrar (entrega)

- [ ] Foto cerrado.
- [ ] **Demo teclas delante cliente**: escribir frase corta.
- [ ] Cobrar **MO 70€ + pieza X€** Bizum/efectivo.
- [ ] `entrega.bat` → factura desglosada.
- [ ] Hook cierre: *"Garantía 30 días en mano de obra. La pieza tiene su garantía del fabricante."*

---

## Errores frecuentes

_Pendiente actualizar tras 5 visitas reales._

Casos anticipados:
- **Cable FFC roto al desconectar**: el ZIF es delicado. Si rompes cable, hay que pedir cable nuevo (10-20€) y esperar.
- **Teclado nuevo es de **otro layout** (US en lugar de ES)** — confirmar layout antes de pedir.
- **Algunos tornillos son distintos de tamaño** y se montan en posiciones específicas. Si los mezclas, agujeros pasan rosca o tornillos largos perforan.
- **Líquido derramado hace tiempo** ha podido corroer el placa. Cambio teclado puede no resolver si hay corrosión bajo placa. Avisar al cliente: "si tras el cambio sigue el síntoma, hay placa afectada y eso es derivar".

---

## Tiempo total

- **30-60 min** Caso A (teclado clipsado).
- **1-2h** Caso B (atornillado desde abajo).
- **2-3h** Caso C (palmrest entero, raro).

---

## Reglas críticas

🔴 **TALLER SIEMPRE.** Domicilio no aplica.
🔴 **Investigación pieza + procedimiento ANTES de cotizar.** Si es remachado y cuesta 250€ pieza, el cliente prefiere saberlo antes de aceptar.
🔴 **Probar teclado USB externo ANTES de presupuestar.** Si externo también falla, problema software.
🔴 **Bandeja imantada** y anotar tornillos por posición. Tornillos perdidos o cambiados = portátil mal cerrado.
🔴 **ZIF connectors van con mucho cuidado.** Levantar pestaña ANTES de tirar del cable.
🔴 **Test todas las teclas con software antes de cerrar.** Si una falla, abrir y revisar antes de entregar.
🔴 **Si descubres corrosión bajo el teclado** (líquido viejo) → llamar al cliente y advertir antes de seguir.
