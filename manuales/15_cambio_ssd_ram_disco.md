# Cambio SSD / RAM / disco (30€ MO)

> Tiempo realista: **30-90 min** según equipo (sobremesa rápido, portátil moderno largo)
> Bloque tarifa: **C — Hardware Mano de Obra**
> Modalidad: domicilio o taller (sin recargo por defecto). Servicios largos (clonado posterior incluido) → mejor taller.

---

## Qué es y qué NO es

**SÍ es:** instalación física de un SSD nuevo (NVMe M.2 o SATA 2.5"), de un módulo de RAM, o de un disco duro adicional. Pieza la trae el cliente o se la vendo aparte (bloque G de tarifa).

**NO es:**
- ❌ **Clonado del sistema viejo al SSD nuevo**: eso es **Clonado OS → SSD 50€** aparte. Si el cliente lo quiere, sumar.
- ❌ **Instalación de Windows desde cero en el SSD nuevo**: eso es **Win 11 OEM 80€** aparte.
- ❌ **Migración completa PC viejo → PC nuevo**: eso es **Migración 100€** aparte.
- ❌ **Soldadura de RAM** (portátiles ultradelgados con RAM soldada): no se toca. Derivar.
- ❌ **Reballing chipset / GPU**: derivar a partner microsoldadura.

**Combinaciones frecuentes a cotizar:**
- Cliente trae SSD NVMe + quiere clonar Win → **30€ MO + 50€ clonado = 80€** (le sale igual que un Formateo+Backup pero conserva todo).
- Cliente trae SSD + quiere Win nuevo → **30€ MO + 80€ Win 11 OEM = 110€**.
- Cliente quiere SSD + RAM en el mismo viaje → **30€ MO total** (es la misma intervención, no doble).

---

## Antes (preparación material)

### Confirmar por WhatsApp antes de salir
- [ ] **Marca y modelo exacto del PC** (sobremesa o portátil).
- [ ] **Tipo de pieza:**
  - SSD: NVMe M.2 (PCIe Gen3 o Gen4) o SATA 2.5".
  - RAM: DDR3, DDR4, DDR5. Velocidad MHz. Cantidad GB.
- [ ] **¿La pieza la trae el cliente o me la pide a mí?**
- [ ] **¿Quiere que se le clone el sistema?** (Si SSD nuevo es para reemplazar el actual.)
- [ ] Si es portátil moderno (post-2020, Asus / Lenovo / HP delgados) → **mirar despiece en YouTube** antes de salir. Algunos exigen quitar 15+ tornillos y palanca de plástico.

### Material en mochila
- [ ] **Kit destornilladores precision** (Phillips PH00 / PH0 / PH1 + Torx T5 / T6 + Pentalobe T5 para algunos portátiles).
- [ ] **Pulsera antiestática** (poco la uso pero por si entra cliente nervioso, da imagen profesional).
- [ ] **Púas de plástico / spudger** (para abrir portátiles sin marcar).
- [ ] **Bandeja imantada** para no perder tornillos.
- [ ] **Pasta térmica** Arctic MX-6 (por si toco disipador NVMe sin querer).
- [ ] **Linterna** USB-C (para ver dentro sobremesas mal iluminados).
- [ ] **USB Arsenal MASTER** con CrystalDiskInfo (Tools\) para verificar SSD nuevo post-instalación.
- [ ] **USB Ventoy rojo** con `gparted.iso` por si hay que crear/redimensionar particiones.

### Verificar pieza antes de instalar (si la traigo yo)
- [ ] Caja precintada.
- [ ] Modelo coincide con lo cotizado (Kingston NV2 1TB ≠ NV1 1TB).
- [ ] Si es RAM → comprobar **velocidad MHz** y **CL latencia** en la etiqueta del módulo.

---

## Al llegar

- [ ] Saludar, foto del equipo cerrado (cara estética, por si después aparece un arañazo y quiere reclamar).
- [ ] Pedir al cliente que cierre todas sus cosas y guarde lo que esté abierto.
- [ ] Apagar PC completamente (no suspensión).
- [ ] Desenchufar **alimentación** y **cualquier cable USB**.
- [ ] Si es portátil: **desactivar batería desde la BIOS** o **desconectar conector batería** una vez abierto (no dar corriente al placa con batería conectada).
- [ ] Mesa despejada, papel/funda debajo del PC para no rayar.

---

## Durante — Físico paso a paso

### Caso 1 — SSD NVMe M.2 (sobremesa)

#### Paso 1 — Acceder
1. Quitar tapa lateral (suele ser 2 tornillos traseros).
2. Localizar **slot M.2** en la placa base. Suelen estar etiquetados `M2_1`, `M2_2`. Hay sobremesas con disipador (placa MSI / ASUS / Gigabyte gama media-alta) → quitar tornillo del disipador y retirarlo.

#### Paso 2 — Instalar
1. Quitar el tornillo pequeño del **standoff M.2** (el que sujeta el SSD).
2. Insertar el SSD **inclinado 30°** en el slot. Empujar hasta que entre del todo.
3. Apretar el SSD hacia abajo y poner el tornillo en su sitio. **NO apretar mucho** — riesgo romper el SSD.
4. Si había disipador: quitar plástico del thermal pad si es nuevo. Recolocar disipador, atornillar.

#### Paso 3 — Cerrar
1. Tapa lateral, tornillos.
2. Reconectar alimentación.

#### Paso 4 — Verificar
1. Encender PC. Entrar a **BIOS** (Del / F2).
2. Ir a **Storage / Boot** → comprobar que aparece el SSD nuevo con su modelo y capacidad.
3. Si NO aparece:
   - Comprobar que está bien insertado (a veces queda inclinado).
   - Comprobar slot. M2_2 a veces comparte línea con SATA y deshabilita SATA. Mirar manual de la placa.
   - Probar otro slot M.2 si la placa tiene 2.

### Caso 2 — SSD SATA 2.5" (sobremesa o portátil)

#### Paso 1 — Acceder y conectar (sobremesa)
1. Tapa lateral.
2. Localizar **bahía 2.5"** en la cárcasa (suele estar al lado del HDD, abajo).
3. Atornillar SSD a la bahía con 4 tornillos.
4. Cable **SATA datos** a un puerto SATA libre de la placa.
5. Cable **SATA alimentación** desde la fuente (cable plano negro/amarillo/rojo con conector 15 pines).

#### Paso 1 alt — Portátil
1. Quitar tornillos tapa inferior.
2. Localizar **bahía 2.5"** o **caddy de disco** (a veces hay que quitar la batería para acceder).
3. Si tiene caddy → sacar caddy, atornillar SSD al caddy, recolocar.
4. Si tiene conector directo SATA → enchufar SSD al conector, atornillar.

#### Paso 2 — Verificar
1. Encender, BIOS, comprobar que aparece.
2. Si arranca y entra a Windows → **abrir Administración de discos** (Win + X → Administración de discos):
   - Aparece "Disco no inicializado" → click derecho → **Inicializar** → **GPT** (no MBR).
   - Click derecho en espacio sin asignar → **Nuevo volumen simple** → siguiente, siguiente, NTFS, etiqueta "Datos" o lo que quiera el cliente.
   - Letra automática (E:, F:).

### Caso 3 — RAM DDR4 / DDR5 (sobremesa)

#### Paso 1 — Acceder
1. Tapa lateral.
2. Localizar **slots DIMM** (suelen ser 2 o 4, al lado de la CPU).

#### Paso 2 — Instalar
1. **Importante:** comprobar configuración de canales. Si la placa tiene 4 slots y el cliente trae 2 módulos → **A2 + B2** (segundo y cuarto contando desde la CPU) para dual-channel. Mirar manual de la placa si dudas.
2. Si solo añadiendo módulo nuevo: respetar configuración de canales existente.
3. Abrir las pestañas a ambos lados del slot.
4. Alinear muesca del módulo con el slot. Empujar **firmemente con dos dedos por los extremos** hasta que las pestañas se cierren solas con un clic.
5. Comprobar visualmente que el módulo está al mismo nivel a izquierda y derecha.

#### Paso 3 — Verificar
1. Cerrar tapa, encender.
2. Si **NO arranca** (POST falla, beeps o pantalla negra):
   - Comprobar que el módulo está bien metido (un fallo del 80% de las veces).
   - Quitar el módulo nuevo, arrancar con los antiguos para confirmar que el problema es el nuevo.
   - Si el módulo nuevo es incompatible (velocidad / CL fuera de QVL) → la placa puede no postear. Cliente devuelve el módulo, pedirle uno compatible.
3. Si arranca: en Windows abrir **Administrador de tareas → Rendimiento → Memoria** y comprobar que la cantidad coincide.
4. Si la placa soporta XMP / EXPO y la RAM es de alta velocidad → entrar a BIOS, activar **XMP Profile 1** (DDR4) o **EXPO Profile 1** (DDR5 AMD). Guardar y reiniciar. Verificar otra vez en Windows que la velocidad MHz coincide con la prometida.

### Caso 4 — RAM DDR4 / DDR5 (portátil)

#### Paso 1 — Acceder
1. Tornillos tapa inferior (atención a tornillos largos vs cortos, anotarlos en posiciones diferentes de la bandeja imantada).
2. **Localizar slots SODIMM** (más pequeños que DIMM sobremesa). A veces hay 1 slot accesible y 1 oculto debajo del teclado. Si solo hay 1 o están soldados → STOP, este portátil no admite ampliación.

#### Paso 2 — Instalar
1. Sacar módulo viejo (si hay que sustituir): abrir las pestañas laterales con cuidado, el módulo se eleva 30°, sacar.
2. Insertar nuevo módulo a 30°, empujar hacia abajo hasta que las pestañas hagan clic.

#### Paso 3 — Verificar (igual que sobremesa)

### Caso 5 — HDD 3.5" (sobremesa, segundo disco)

#### Paso 1 — Atornillar
1. Bahía 3.5" cárcasa, atornillar HDD con 4 tornillos largos.
2. Cable SATA datos + SATA alimentación.

#### Paso 2 — Verificar
1. BIOS → comprobar detección.
2. Windows → Administración de discos → Inicializar GPT → Nuevo volumen NTFS.

---

## Durante — Software de comprobación post-instalación

### CrystalDiskInfo (SSD / HDD)

1. Pendrive USB Arsenal MASTER → carpeta `Tools\CrystalDiskInfo\`.
2. Doble click `DiskInfo64.exe`.
3. Comprobar que el disco nuevo aparece arriba.
4. **Estado**: debe salir **"Bueno" en azul**. Si sale "Precaución" en amarillo o "Malo" en rojo → ⚠️ disco defectuoso de fábrica, devolver al cliente.
5. **Horas de uso** debe ser **0** o muy pocas (1-5 max si es de demo). Si tiene 1000+ horas → es usado vendido como nuevo, alertar al cliente.
6. **Total Host Writes**: debe ser bajo. SSD con 5TB+ escritos siendo "nuevo" es engaño.
7. Captura de pantalla y guardar en sesión cliente.

### CPU-Z (RAM)

1. `Tools\CPU-Z\cpuz_x64.exe`.
2. Pestaña **Memory**: comprobar que cantidad y tipo coinciden (16GB DDR4, etc.).
3. Pestaña **SPD**: seleccionar slot 1 → ver módulo nuevo. Ver MHz, latencia CL, fabricante, fecha producción.
4. Si el cliente activó XMP → comprobar que **DRAM Frequency** coincide (ej. 1600 MHz x 2 = 3200 MT/s para DDR4-3200).

---

## Al cerrar

- [ ] Cerrar el PC físicamente, comprobar todos los tornillos puestos.
- [ ] Foto del equipo cerrado igual que al llegar (cara estética).
- [ ] Si era SSD nuevo y se incluía clonado o instalación Windows → ese servicio se hace ahora **aparte cobrado**.
- [ ] Si era SSD vacío sin clonado → cliente queda con disco nuevo accesible en Windows como "E:" para que él guarde lo que quiera.
- [ ] Si era ampliación RAM → enseñar Administrador de tareas con la cantidad nueva.
- [ ] Cobrar **30€ Bizum o efectivo** (más servicios extra si los hubo).
- [ ] Lanzar `entrega.bat` → factura `MPC-2026-XXXX`.
- [ ] Frase cierre: **"Garantía 30 días en mano de obra. Si dentro de 30 días el SSD/RAM falla por algún problema de instalación, vuelvo gratis. Si falla la pieza por defecto de fábrica, gestionas garantía con el fabricante."**

---

## Errores frecuentes

_Pendiente actualizar tras 5 visitas reales._

Casos anticipados ya identificados:
- **Cliente compra SSD M.2 SATA pensando que es NVMe**: SSDs M.2 vienen en 2 sabores (NVMe PCIe vs SATA, mismo formato físico). Si la placa solo tiene slot M.2 NVMe (sin soporte M.2 SATA) → no funciona. Comprobar manual de la placa antes.
- **Portátil con RAM soldada** (ultradelgados Lenovo Yoga, Asus Zenbook delgados): no se puede ampliar. Avisar antes de salir.
- **DDR4 vs DDR5 visualmente parecen iguales** pero las muescas están en posiciones distintas → no entran físicamente en placa equivocada. Si forzas, rompes módulo y placa.
- **NVMe nuevo no detectado**: 60% de las veces es el slot M2_2 deshabilitado por compartir línea con SATA. Cambiar al M2_1 o leer manual.
- **Sobremesa con cable SATA suelto sin querer al cerrar tapa**: comprobar siempre que los discos viejos siguen detectándose tras cambiar la tapa.

---

## Tiempo total

- SSD NVMe sobremesa: **20-30 min** + verificación.
- SSD SATA sobremesa: **30-40 min**.
- SSD portátil: **30-60 min** (depende modelo).
- RAM sobremesa: **15-25 min**.
- RAM portátil: **30-60 min** (depende modelo).
- HDD 3.5" sobremesa: **20-30 min**.

---

## Reglas críticas

🔴 **Verificar pieza antes de instalar**. Caja precintada, modelo correcto. Una vez puesta es difícil devolver.
🔴 **Apagar y desenchufar siempre**. PC encendido al manipular RAM = se rompe placa o módulo.
🔴 **Desconectar batería en portátiles** (físicamente o por BIOS) antes de tocar nada eléctrico.
🔴 **NO forzar nada**. Si no entra, no es por falta de fuerza, es por orientación equivocada.
🔴 **NO apretar tornillos M.2 a tope**. Riesgo de partir el SSD.
🔴 **NO mezclar módulos RAM de marcas/velocidades distintas** sin avisar al cliente. Funciona pero a la velocidad del más lento, y a veces causa inestabilidad.
🔴 **CrystalDiskInfo obligatorio post-instalación SSD**. Si sale ámbar o rojo, devolver pieza.
🔴 **Foto antes/después** si abro caja del PC. Protección mutua si aparece daño estético.
🔴 **Si cliente tenía datos en disco antiguo y va a tirarlo** → recomendar borrado seguro (gparted con shred desde USB Ventoy) ANTES de devolverle el disco. NO dejar disco con datos personales en la calle.
