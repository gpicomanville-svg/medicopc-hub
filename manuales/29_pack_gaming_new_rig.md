# Pack Gaming New Rig (140€)

> Tiempo realista: **4-6h** (taller)
> Bloque tarifa: **F — Gaming**
> Modalidad: taller por defecto (manipulación fina) · domicilio +25€

---

## Qué es y qué NO es

**SÍ es:** servicio para clientes que **acaban de comprar / montar un PC nuevo gaming** y quieren llevárselo "listo para jugar" sin pelearse 1 día con drivers, BIOS, configuración Windows óptima, montaje físico, clonado SO desde otro PC, test estabilidad. Pack 140€ MO incluye:
1. **Montaje físico** del PC (si llega en piezas) o **revisión** del PC montado.
2. **Configuración BIOS** (XMP/EXPO RAM, Resizable BAR, fan curves, virtualización si toca).
3. **Instalación Windows** limpia + drivers fabricante.
4. **Clonado de SSD viejo** al nuevo (si trae) → conserva sistema y datos.
5. **Tests estabilidad** (Prime95 CPU + FurMark GPU + MemTest86 RAM).
6. **Steam + Epic + GOG + launchers** instalados con cuentas cliente.
7. **Software base gaming** (Discord, MSI Afterburner, HWiNFO, RivaTuner OSD).

**NO es:**
- ❌ **Pack Gaming Tune-Up 150€**: ese es para PCs gaming **YA EN USO** que quieren bajar temperaturas + undervolt + repaso. Aplica a PC viejo, no a uno nuevo.
- ❌ **Solo configuración**: si cliente solo quiere "instálame Steam y drivers" → eso es **Config Gaming 80€**, no requiere montaje ni tests profundos.
- ❌ **Win 11 OEM 80€**: ese es solo Windows. Pack Gaming New Rig **incluye Windows + montaje + tuning + clonado + tests**.

**Cuándo aplica:**
- Cliente compró PC piezas en PCComponentes / Coolmod / Versus para montar.
- Cliente compró PC pre-montado (Coolmod / Vsgamers / VANT) y quiere optimización primer día.
- Cliente migra de PC viejo a PC nuevo gaming, quiere conservar datos sin perder horas (alternativa: **Migración 100€** sin gaming, pero no incluye undervolt ni tuning).

---

## Antes (preparación)

### Confirmar por WhatsApp
- [ ] **Listado de componentes**: CPU, GPU, RAM, placa, fuente, chasis, disipador, almacenamiento.
- [ ] **¿Pieza por piezas o pre-montado?** Si pre-montado, ¿quién lo montó (tienda o cliente)?
- [ ] **¿Trae Windows OEM ya con clave o lo compra el cliente?** Pieza aparte 30-40€.
- [ ] **¿Hay PC viejo del que clonar disco?** Si SÍ → necesitamos su SSD/HDD viejo + adaptador.
- [ ] **Resolución monitor**: 1080p / 1440p / 4K. Determina configuración drivers.
- [ ] **Cuentas Steam / Epic / GOG / Battle.net / Riot / Ubisoft Connect** que tiene.

### Material en taller
- [ ] **USB Arsenal MASTER** + USB Ventoy con W11_25H2_ES.iso.
- [ ] **Pasta térmica** Arctic MX-6 + pads térmicos surtidos (por si necesitan reemplazo en GPU).
- [ ] **Destornilladores precision + Phillips PH1/PH2**.
- [ ] **Bridas + tijeras** para cable management.
- [ ] **Adaptador USB-NVMe + USB-SATA** (clonar desde disco viejo).
- [ ] **Pulsera antiestática**.
- [ ] **MemTest86 USB** + **Prime95** + **FurMark** + **Heaven Benchmark** + **HWiNFO64** en USB.

---

## Al recibir el equipo

- [ ] Foto piezas / PC montado.
- [ ] Inventario rápido de cajas componentes (cliente se las queda con garantías).
- [ ] Resguardo firmado.

---

## Durante — Físico paso a paso

### Paso 1 — Montaje (si llega en piezas)

⚠️ Si llega pre-montado por tienda → saltar al paso 2. Solo verificar montaje correcto (ver paso 1.10).

1. **Placa base sobre caja madre o foam antiestático**, fuera del chasis.
2. **CPU**:
   - Levantar palanca socket.
   - Insertar CPU alineando triángulo de la esquina.
   - Bajar palanca con suavidad.
   - **NO forzar** si hace resistencia — pin doblado, abortar.
3. **RAM**:
   - Slots A2 + B2 (segundo y cuarto desde la CPU normalmente, ver manual placa) si son 2 módulos.
   - Empujar firme hasta que las pestañas hagan clic.
4. **NVMe SSD M.2**:
   - Quitar disipador M.2 si lo tiene la placa.
   - Insertar SSD en ángulo 30°, bajar y atornillar.
   - Reponer disipador M.2 con thermal pad.
5. **Disipador CPU**:
   - Pasta térmica (grano de arroz, NO esparcir).
   - Backplate si requiere (cooler tipo Hyper 212 / Noctua).
   - Atornillar en patrón cruz.
   - Conectar cable ventilador a CPU_FAN.
6. **Insertar placa montada en chasis**.
7. **Fuente alimentación** en su sitio (tornillos traseros).
8. **GPU** en slot PCIe x16 (más cercano a la CPU).
9. **Cableado**:
   - 24-pin ATX a placa.
   - 8-pin EPS a CPU.
   - PCIe a GPU (8-pin / 6+2 / 12VHPWR según GPU).
   - SATA a discos.
   - Conectores frontales del chasis (Power, Reset, LED, USB, Audio) — ver manual placa.
10. **Verificar**:
    - Todo conectado.
    - Sin cables tocando ventiladores.
    - Cable management decente con bridas.

### Paso 2 — Primer arranque + BIOS

1. Pantalla + teclado + ratón.
2. Cable corriente + interruptor PSU ON.
3. Power frontal.
4. Llegar a BIOS (Del / F2):
   - **Verificar detección componentes**: CPU, RAM cantidad, GPU, NVMe.
   - **XMP / EXPO ON**: para que la RAM corra a su velocidad nominal (no 4800 MHz default sino 6000+ MHz comprados).
   - **Resizable BAR ON**: mejora rendimiento GPU moderna.
   - **Secure Boot ON**: requerido Win 11.
   - **TPM 2.0 ON**: requerido Win 11.
   - **Fan curves**: ajustar curva ventiladores (silencioso por defecto, agresivo bajo carga).
   - **Boot priority**: USB primero para instalar Windows.
5. Save & Exit.

### Paso 3 — MemTest86 (RAM nueva, OBLIGATORIO)

1. Boot USB MemTest86.
2. **2 pasadas mínimo** (~1-2h con 32GB DDR5 en kit modesto).
3. Resultado:
   - **0 errores** → RAM OK, continuar.
   - **>0 errores** → RAM defectuosa, devolver al fabricante. Pausar trabajo.

### Paso 4 — Instalación Windows 11

Como en `13_win11_oem.md`:
1. Boot USB Win 11.
2. Instalación limpia en NVMe.
3. Configuración OOBE (Shift+F10 → `oobe\bypassnro` si quiere cuenta local).
4. Privacidad en cero.

### Paso 5 — Activar Windows

1. Si licencia OEM en BIOS → automático.
2. Si licencia digital cuenta MS → login.
3. Si clave física → meter en Configuración → Activación.

### Paso 6 — Windows Update + Drivers

1. Windows Update completo (30-60 min, varios reinicios).
2. Drivers fabricante PLACA BASE web oficial:
   - Chipset (Intel ME / AMD).
   - Audio Realtek.
   - LAN.
   - WiFi/BT.
3. Driver GPU **DDU clean install**:
   - Descargar driver GPU oficial (NVIDIA / AMD / Intel Arc).
   - **Display Driver Uninstaller (DDU)** en safe mode (Configuración → Recuperación → Inicio avanzado → Modo seguro).
   - Limpiar drivers gráficos viejos.
   - Reiniciar.
   - Instalar driver GPU oficial limpio.

### Paso 7 — Tests estabilidad CPU

1. **Prime95** Small FFTs **30 min**:
   - Vigilar temperatura CPU en HWiNFO64.
   - **<85°C en sostenido** → bien.
   - **>95°C** → problema disipador (mal montado, pasta mal, fan curve mala). Revisar.
2. Si pasa 30 min sin BSOD ni throttling → CPU estable.

### Paso 8 — Tests estabilidad GPU

1. **FurMark 1080p 10 min** (estresa GPU al máximo, simula peor caso).
2. Vigilar temperatura GPU:
   - **<85°C aire** → bien.
   - **>90°C** → fan curve agresiva o servicing GPU recomendable.
3. **Heaven Benchmark 10 min** (más realista juego).
4. Si pasa sin artifacts ni cuelgue → GPU estable.

### Paso 9 — Clonado disco viejo (si aplica)

⚠️ **Solo si cliente trae SSD/HDD viejo y quiere conservar datos.**

1. Conectar SSD/HDD viejo al PC nuevo (USB adaptador o SATA interno temporal).
2. Software clonado: **Macrium Reflect Free** (descontinuado pero v8 funciona) o **Clonezilla** (vía USB Ventoy).
3. Clonar disco a disco con redimensión (si el SSD nuevo es más grande que el viejo, expandir partición Windows).
4. Verificar arranque desde disco nuevo.
5. Activación Windows: si era OEM en BIOS del PC viejo y este es PC nuevo → la clave **NO sirve** (vinculada a placa antigua). Cliente debe usar la clave OEM de la placa nueva o comprar Windows aparte.

### Paso 10 — Software base gaming

#### Imprescindibles
- [ ] **Steam** + login cliente (él teclea password).
- [ ] **Epic Games** + login.
- [ ] **GOG Galaxy** si tiene cuenta.
- [ ] **Battle.net** si juega Blizzard.
- [ ] **Riot Client** si juega LoL / Valorant.
- [ ] **Ubisoft Connect** si tiene Ubi.
- [ ] **EA App** si juega FIFA / BF.

#### Optimización gaming
- [ ] **MSI Afterburner** + **RivaTuner Statistics Server** (overlay FPS, control fan).
- [ ] **HWiNFO64** (sensores temperatura).
- [ ] **Discord** (comunicación gaming).
- [ ] **GeForce Experience** o **AMD Adrenalin** (drivers + grabación + filtros). Solo si cliente quiere — opcionales por bloatware.

#### NO instalar (a menos que cliente pida)
- ❌ Razer Synapse / Corsair iCUE pesados.
- ❌ RGB software (10 programas distintos para 10 luces).
- ❌ Bloatware ASUS Armoury Crate, MSI Center si no usa.

### Paso 11 — Configuración Windows óptima gaming

1. **Plan energía**: Alto rendimiento o Equilibrado AMD Ryzen.
2. **Game Mode** ON: Configuración → Juegos → Game Mode → ON.
3. **Hardware-accelerated GPU scheduling**: Configuración → Pantalla → Configuración pantalla → Gráficos → Configuración predeterminada → Cambiar configuración predeterminada de gráficos → Programación de GPU acelerada → ON.
4. **Mouse acceleration OFF**: Panel control → Mouse → Opciones puntero → desmarcar "Mejorar precisión del puntero".
5. **Game Bar / Xbox Game Bar**: dejar por defecto, no quitar (cliente puede usar grabación).
6. **Animaciones reducidas** opcional: Configuración → Accesibilidad → Efectos visuales → Animaciones OFF (algunos FPS ganan).
7. **Resolución y refresco monitor**: configurar a la resolución nativa + Hz máxima (144 / 165 / 240).

### Paso 12 — Test final con benchmark real

1. **3DMark Time Spy** (Steam, gratis demo) o **Cinebench R23** (Maxon, NO disponible portable, descartado oficialmente).
2. Anotar puntuación → comparar con tablas online media para esa CPU + GPU.
3. Si está dentro del rango esperado → sistema OK.
4. Si está -20% por debajo → buscar bottleneck (driver mal, throttling térmico, RAM no XMP, etc.).

---

## Al cerrar

- [ ] Mostrar al cliente:
  - Sistema arrancando rápido.
  - Steam con sus juegos descargables (no descargar yo, él decide).
  - HWiNFO mostrando temperaturas en idle.
  - Benchmark resultado.
- [ ] Cobrar **140€** (+ Windows OEM si lo vendí, 30-40€) Bizum o efectivo.
- [ ] Lanzar `entrega.bat` → factura `MPC-2026-XXXX` con desglose.
- [ ] Frase cierre: **"PC montado, testeado y configurado. Garantía 30 días en mano de obra. Si algo se cuelga, falla, BSOD raro, vuelvo gratis dentro del mes. Garantía piezas según fabricante (CPU 3 años Intel/AMD, RAM lifetime Corsair/G.Skill, GPU 2-3 años, SSD 5 años NVMe top, fuente 5-7 años Corsair/Seasonic)."**

---

## Errores frecuentes

_Pendiente actualizar tras 5 montajes reales._

Anticipados:
- **Pin CPU doblado** al insertar (LGA Intel) o **patilla rota** (PGA AMD viejos): pieza muerta. Cliente devuelve a tienda en garantía. NO intentar "enderezar" sin experiencia microsoldadura.
- **RAM no llega a velocidad XMP**: BIOS antigua, actualizar BIOS. O placa no soporta esa velocidad (kit 6400MHz en placa solo hasta 6000MHz).
- **GPU no detectada**: cable PCIe alimentación mal conectado, o slot mal encajado, o drivers mal instalados.
- **Test Prime95 BSOD a los 5 min**: voltajes RAM mal, XMP demasiado agresivo, undervolt CPU mal aplicado. Reiniciar BIOS por defecto y rehacer.
- **Test FurMark BSOD/cuelgue**: GPU defectuosa o fuente insuficiente. Comprobar.
- **Cliente no sabe la clave del OEM viejo** y quiere clonado de PC viejo a nuevo: Windows del PC viejo no se activa en nuevo (OEM atada a hardware antiguo). Avisar antes, comprar licencia nueva 30-40€.
- **Pre-montaje tienda mal hecho**: ventiladores invertidos, RAM en slots A1+A2 (mal), pasta térmica excesiva. Avisar al cliente, corregir cobrando los pasos del montaje (no rehacer pack entero).

---

## Tiempo total

- Montaje desde piezas + tests + Windows + tuning: **5-6h**.
- Pre-montado tienda + tests + Windows + tuning: **3-4h** (saltar montaje físico).
- Si requiere clonado disco viejo: **+1-2h**.

---

## Reglas críticas

🔴 **MemTest86 OBLIGATORIO** en montaje desde piezas. RAM defectuosa = BSODs aleatorios futuros, peor que descubrirlo en garantía.
🔴 **Prime95 + FurMark obligatorios** antes de entregar. Sin tests no garantías estabilidad.
🔴 **Pasta térmica grano de arroz**, NO esparcir, NO Liquid Metal sin barniz.
🔴 **Pulsera antiestática** al manipular CPU / RAM / GPU.
🔴 **CPU patilla / pin doblado** = NO continuar, devolver a tienda.
🔴 **XMP/EXPO ON** en BIOS, sino la RAM va a velocidad bajísima por defecto.
🔴 **Resizable BAR ON** en GPUs modernas = más rendimiento gratis.
🔴 **Cable 12VHPWR completamente metido** en RTX 4090/5090. Riesgo incendio si flojo.
🔴 **Cliente teclea passwords cuentas Steam / Epic / Discord**. Yo NO veo pass.
🔴 **NO instalar bloatware fabricante** (ASUS Armoury Crate, MSI Center). Pesado y rara vez útil.
🔴 **NO software pirata** (juegos crackeados, mods piratas). NUNCA.
🔴 **Foto montaje** antes de cerrar chasis. Si algo se rompe en transporte → tu prueba.
