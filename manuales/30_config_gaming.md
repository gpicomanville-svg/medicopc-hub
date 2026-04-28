# Configuración Gaming (80€)

> Tiempo realista: **2-3h**
> Bloque tarifa: **F — Gaming**
> Modalidad: domicilio o taller (sin recargo).

---

## Qué es y qué NO es

**SÍ es:** servicio para clientes que **YA tienen PC gaming funcionando** (Windows instalado, drivers básicos) pero quieren optimización completa: drivers limpios fabricante (NVIDIA / AMD), launchers gaming con cuentas, undervolt CPU/GPU básico, configuración Windows óptima para juegos, fan curves, monitorización temperaturas, eliminar bloatware. **80€** MO, sin piezas (no monta nada físico, no incluye servicing GPU).

**NO es:**
- ❌ **Pack Gaming Tune-Up 150€**: incluye limpieza profunda + servicing GPU desmontaje + cambio pasta + pads térmicos + benchmarks comparativos antes/después. Bloque B+F combinado.
- ❌ **Pack Gaming New Rig 140€**: para PCs nuevos recién montados, incluye montaje físico, instalación Windows, MemTest86. Aplica a hardware nuevo.
- ❌ **Limpieza Completa + GPU 120€**: limpieza física profunda. Si cliente quiere baja temperaturas además de tuning → sumar Limpieza+GPU 120€ + Config Gaming 80€ = 200€.
- ❌ **Reparación gaming**: "no me arranca un juego" → asistencia remota 30€ (mucho más simple).

**Cuándo aplica:**
- Cliente acabó de comprar GPU nueva, quiere drivers limpios + optimización.
- Cliente cambió monitor a 144Hz y no sabe configurar.
- Cliente con PC gaming bloatware fabricante (Lenovo Legion, ASUS ROG, MSI) que va peor que limpio.
- Cliente quiere undervolt para bajar temperaturas / consumo eléctrico sin perder rendimiento.
- Cliente quiere "que el PC me vaya como en YouTube" (frase típica): optimización general.

---

## Antes (preparación)

### Confirmar por WhatsApp
- [ ] **Especificaciones PC**: CPU, GPU, RAM, monitor (resolución + Hz), almacenamiento.
- [ ] **¿Qué juegos juega principalmente?** Determina prioridades:
  - **eSports competitivos** (CS2, Valorant, LoL, OW2): prioridad latencia + FPS altos > calidad gráfica.
  - **AAA** (Cyberpunk, RDR2, Elden Ring): calidad gráfica + estabilidad > FPS extremo.
  - **VR**: latencia frame extremo, drivers actualizados.
  - **Casual / indie**: configuración estándar.
- [ ] **¿Síntomas concretos?** FPS bajos, drops, crashes, temperaturas altas.
- [ ] **¿Cuentas Steam / Epic / Battle.net / Riot que tiene?**

### Material en mochila / taller
- [ ] **USB Arsenal MASTER** con instaladores (DDU, MSI Afterburner, HWiNFO, RivaTuner, FurMark, Heaven, Prime95).
- [ ] **Cable Ethernet** (descargar drivers más rápido).

---

## Al llegar

- [ ] Foto del PC, foto del Administrador de tareas → Rendimiento (ver CPU/GPU/RAM actuales).
- [ ] **Diagnóstico inicial 10 min**:
  - Lanzar `MEDICOPC.exe` → diagnóstico llegada.
  - Abrir HWiNFO64 → ver temperaturas idle CPU/GPU.
  - Lanzar 1 juego del cliente 5 min → ver FPS + temperaturas en juego.
  - Apuntar **estado inicial** (FPS / temps) en notepad para comparar al final.
- [ ] Confirmar verbalmente lo que se va a hacer.

---

## Durante — Software paso a paso

### Paso 1 — Limpieza ligera previa (no es Limpieza Completa, solo lo justo)

1. **AdwCleaner** + **Malwarebytes Free portable** escaneo rápido (15 min).
2. **Autoruns**: desactivar bloatware fabricante en arranque (Razer Synapse innecesario, ASUS GPU Tweak si no usa, MSI Mystic Light si no usa, LIM, Norton/McAfee preinstalado).
3. **Programas instalados**: desinstalar bloatware obvio.

### Paso 2 — DDU clean install drivers GPU

1. **Descargar driver GPU oficial** desde NVIDIA / AMD / Intel Arc (web oficial, NO GeForce Experience).
2. Configuración → Recuperación → Inicio avanzado → Reiniciar → Solucionar problemas → Opciones avanzadas → Configuración inicio → Reiniciar → **Modo seguro con red**.
3. Ejecutar **Display Driver Uninstaller (DDU)**:
   - Marcar "Limpiar y reiniciar" después.
   - Click "Clean and restart".
4. PC reinicia normal.
5. Instalar driver GPU oficial limpio.
6. Reiniciar.

### Paso 3 — Drivers chipset y placa actualizados

1. Web fabricante placa (ASUS / MSI / Gigabyte / ASRock) → **modelo exacto** → drivers Win 11.
2. Instalar:
   - **Chipset** (Intel ME / AMD Chipset).
   - **Audio Realtek** si suena mal.
   - **LAN Realtek / Intel** si problemas red.
   - **WiFi/BT** si lo usa.
3. Reiniciar.

### Paso 4 — Configuración Windows óptima gaming

#### Plan energía
1. Panel control → Opciones energía → **Alto rendimiento** (Intel) o **Ryzen Balanced** / **Ryzen High Performance** (AMD).

#### Game Mode + GPU scheduling + VRR
1. Configuración → Juegos → Game Mode → **ON**.
2. Configuración → Pantalla → Configuración pantalla avanzada → Gráficos → Cambiar configuración predeterminada de gráficos → **Programación de GPU acelerada por hardware → ON** + reiniciar.
3. Si monitor FreeSync/G-Sync: Configuración → Pantalla → ON.

#### Mouse acceleration OFF (eSports)
1. Panel control → Mouse → Opciones puntero → **desmarcar "Mejorar precisión del puntero"**.

#### DPI scaling 100%
1. Configuración → Pantalla → Escala → **100%**.

#### Resolución + refresco monitor
1. Configuración → Pantalla → resolución nativa.
2. Configuración → Pantalla → Configuración pantalla avanzada → Frecuencia actualización → **máximo soportado** (60 / 144 / 165 / 240 Hz).

#### Animaciones (opcional ganancia FPS)
1. Configuración → Accesibilidad → Efectos visuales → **Animaciones OFF**.

### Paso 5 — Launchers gaming

#### Steam
1. Descargar de steampowered.com.
2. Login cliente (él teclea password).
3. Configuración Steam → Descargas → Región más cercana (Madrid).
4. Configuración → In-Game → Overlay Steam ON.

#### Epic Games
1. Descargar epicgames.com.
2. Login cliente.

#### Otros (según cuentas cliente)
- Battle.net (Blizzard).
- Riot Client (LoL / Valorant).
- Ubisoft Connect.
- EA App.
- GOG Galaxy.

### Paso 6 — Software monitorización gaming

1. **MSI Afterburner** + **RivaTuner Statistics Server** instalados.
   - Configurar overlay OSD: FPS + temps CPU/GPU + uso CPU/GPU + uso RAM + frametime.
   - Tecla atajo (F12 por defecto) para mostrar/ocultar.
2. **HWiNFO64** instalado, sensores principales.
3. Test: abrir 1 juego cliente, comprobar overlay aparece y muestra datos.

### Paso 7 — Undervolt CPU (Intel / AMD)

⚠️ **Advertencia previa**: undervolt mal hecho = BSODs. Hay que ir con calma + tests.

#### Intel (Tdb cualquier i5/i7/i9 12+ gen)
1. **Intel XTU** (Extreme Tuning Utility) descarga oficial Intel.
2. Pestaña **Core Voltage Offset**:
   - Bajar de 0 mV → **-50 mV** primer test.
3. Aplicar.
4. **Prime95 Small FFTs 30 min**:
   - Vigilar temperaturas (deben bajar 5-10°C).
   - Sin BSOD → -50 mV estable.
5. Si estable → bajar a **-75 mV**, repetir test.
6. Si estable → **-100 mV** (suele ser el sweet spot).
7. Si BSOD en cualquier punto → subir +25 mV y rehacer test.
8. Apuntar el valor en notepad al cliente: "tu CPU corre a -100 mV undervolt".

#### AMD Ryzen 5000+ (PBO Curve Optimizer)
1. **Ryzen Master** o BIOS:
   - Curve Optimizer All Cores **-15** primer test (cada paso es ~3.3 mV).
2. **Prime95** test 30 min.
3. Sin errores → **-20**, repetir.
4. **-25 / -30 / -35** según calidad CPU.
5. Si BSOD → subir +5 y rehacer.
6. Apuntar valor.

⚠️ **NO undervolt agresivo en PCs portátiles gaming** (térmica más limitada, cualquier inestabilidad joroba al cliente sin saber por qué).

### Paso 8 — Undervolt GPU (NVIDIA)

#### Con MSI Afterburner
1. **MSI Afterburner** → Ctrl+F (Curve Editor).
2. Buscar voltaje habitual (ej. 1100 mV) en juego (verlo con HWiNFO mientras juega 5 min).
3. En la curva: punto a 1100 mV bajar 50 MHz, mantener punto a 950 mV en frecuencia base + 30-50 MHz.
4. Aplicar y guardar perfil.
5. Test: **Heaven Benchmark 10 min** + **FurMark 5 min**.
6. Sin artifacts/cuelgue → undervolt estable.
7. Si artifacts → curva más conservadora.

#### AMD GPU (Radeon Software)
1. AMD Adrenalin → Performance → Tuning.
2. Custom tuning → bajar voltaje GPU 30-50 mV.
3. Test similar.

### Paso 9 — Fan curves

#### Ventiladores chasis (BIOS)
1. Reiniciar a BIOS.
2. Hardware monitor / Fan Control:
   - **Idle**: ventiladores 30-40% (silencioso).
   - **Carga media** (60°C CPU): 50-70%.
   - **Carga alta** (80°C+): 100%.
3. Save.

#### Ventiladores GPU
1. MSI Afterburner → Fan curve editor.
2. Curva personalizada: silencioso idle, agresivo bajo carga.

### Paso 10 — Test final comparativo

1. Abrir 1 juego del cliente.
2. Anotar:
   - **FPS medio** (con overlay RivaTuner).
   - **Temperatura CPU** en juego.
   - **Temperatura GPU** en juego.
   - **Uso CPU / GPU** porcentaje.
3. Comparar con el "antes" del paso de diagnóstico inicial.
4. **Mejora esperada**:
   - FPS: +5-15% sobre estado bloatware/drivers viejos.
   - Temperaturas: -5-10°C undervolt.
   - Estabilidad: sin crashes en 1h juego.

---

## Al cerrar

- [ ] Mostrar al cliente comparativa antes/después (FPS + temps).
- [ ] Mostrar overlay RivaTuner activo en su juego.
- [ ] Explicarle: "tienes undervolt aplicado de -100mV CPU y -50MHz @ 1100mV GPU. Apuntado en este post-it. Si algún día reinstalas Windows o cambias hardware, vuelves a aplicarlo."
- [ ] Recordar:
  - **MSI Afterburner** debe arrancar con Windows para mantener undervolt GPU.
  - **Intel XTU** profile aplicado al arranque automáticamente.
  - **Curva ventiladores BIOS** queda fija.
- [ ] Cobrar **80€** Bizum / efectivo.
- [ ] Lanzar `entrega.bat` → factura `MPC-2026-XXXX`.
- [ ] Frase cierre: **"PC tuneado. Garantía 30 días en mano de obra. Si dentro del mes hay BSOD, crashes, FPS raros → vuelvo gratis a revisar undervolt y drivers. Si quieres bajar más temperaturas físicamente con limpieza+GPU, son 120€ aparte (servicing pasta y pads)."**

---

## Errores frecuentes

_Pendiente actualizar tras 5 sesiones reales._

Anticipados:
- **BSOD post-undervolt al día siguiente** (cliente lo nota cuando vuelvo a casa): undervolt demasiado agresivo en estado raro (despertar de suspensión, juego específico). Volver y subir +10 mV CPU o conservar curva GPU.
- **Cliente nota FPS iguales pero temperaturas más bajas**: undervolt funcionó pero no había bottleneck CPU/GPU sino drivers/Windows. Mejora indirecta. Explicar que la temperatura baja prolonga vida del hardware.
- **Driver GPU con DDU revierte a versión Windows automática**: desactivar Windows Update drivers de GPU: gpedit.msc → Configuración equipo → Plantillas administrativas → Componentes Windows → Windows Update → "No incluir controladores con Windows Update" → Habilitada.
- **GPU no soporta undervolt** (algunas RTX 30 portátil bloqueadas, GPUs OEM Dell sin Curve editable): explicar limitación cliente, omitir paso GPU.
- **Cliente con monitor FreeSync premium pero NVIDIA GPU**: G-Sync compatible está limitado a algunos monitores. Activar en NVIDIA Control Panel → Display → Set up G-Sync → Enable G-Sync compatible.
- **Cliente quiere overclock**: NO incluido en este pack. Es Pack Gaming Tune-Up 150€ o servicio aparte (riesgo + responsabilidad mayor).

---

## Tiempo total

- Sin undervolt: **1.5h**.
- Con undervolt CPU + GPU + tests: **2.5-3h**.

---

## Reglas críticas

🔴 **DDU SIEMPRE en safe mode** para drivers GPU. Sin DDU = drivers viejos siguen ahí, conflictos.
🔴 **Undervolt CON tests Prime95 + FurMark obligatorios**. Sin tests = BSODs futuros del cliente.
🔴 **NO undervolt en portátil sin VRM monitorización clara**. Térmica limitada portátil = inestabilidad.
🔴 **CLIENTE TECLEA passwords Steam / Epic / Discord / etc.** Yo nunca veo passwords.
🔴 **Apuntar valores undervolt en post-it / WhatsApp** al cliente. Si reinstala Windows luego, los recupera.
🔴 **MSI Afterburner debe arrancar con Windows** para mantener perfil GPU.
🔴 **Comparativa antes/después** obligatoria. Sin medición → cliente no ve la mejora → cuestionará 80€.
🔴 **NO software pirata** (juegos crackeados, mods piratas, repacks Russos).
🔴 **NO instalar bloatware fabricante** (ASUS Armoury Crate, MSI Center, Razer Synapse) si cliente no usa periféricos de esa marca.
🔴 **Bloatware fabricante portátil gaming** (Lenovo Vantage, MSI Center): conservar SOLO si cliente lo usa para fan curves o BIOS update. Si no → fuera.
🔴 **Si surge inestabilidad imposible de resolver** → revertir a stock, no cobrar la parte undervolt. Reputación.
