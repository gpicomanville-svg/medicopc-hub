# Pack Gaming Tune-Up — 160€

**ID tarifa:** `pack_gaming_tuneup`
**Bloque:** F Packs temáticos
**Tiempo realista:** 3h (rango 2-4)
**Cuando aplica:** PC gaming ya montado del cliente, tiene Windows funcionando y juega, pero quiere mejorar (más FPS, menos calor, menos ruido). Cliente con cierta cultura PC (sabe lo que es un benchmark). **NO** sirve para PC nuevo recién montado (eso es Gaming New Rig 140€). **NO** es solo drivers (eso es Config Gaming suelto 80€).

---

## Antes de visita

- **Confirmar GPU del cliente al teléfono**: NVIDIA / AMD / Intel ARC. Determina si undervolt aplica:
  - NVIDIA → undervolt vía MSI Afterburner con perfil `.mvc` ✓
  - AMD → undervolt vía Adrenalin Software (manual, sin CLI fiable) → script lo deja en ámbar `manual_requerido` con instrucción
  - Intel ARC → undervolt no aplica, sale gris
- **Confirmar Windows actualizado y arranca OK** (este servicio no es para arreglar Windows).
- **Confirmar acceso a la torre** (cliente avisa si está en mueble apretado).

**Llevar:**
- USB MASTER + BACKUP.
- **Profile1.mvc** ya creado en `Tools\MSIAfterburner\Profiles\` (curva conservadora -50mV, hecho una vez en sobremesa de pruebas). ⚠️ Si NO está creado todavía → undervolt sale gris, avisar cliente que esa parte irá manual o se pospone.
- Pasta térmica (Arctic MX-6 o KTC1 — para gaming preferible MX-6, mejor disipación).
- Pads térmicos (Thermalright varios grosores para VRAM/VRM).
- Kit destornilladores.
- Brocha + bote aire comprimido.

---

## Al llegar (10 min)

1. Saludar, ubicar PC, foto frontal y lateral.
2. **`Scripts\0_LLEGADA\llegada.bat`** → checklist firmada.
3. Pregunta clave: **"¿Qué juegos juegas más y qué FPS notas?"**. Te da:
   - Punto de referencia subjetivo (cliente ya tiene su sensación).
   - Test real al final con sus juegos para que vea diferencia.
4. Foto de la torre con tapa puesta.

---

## Durante

### Software fase 1 — Benchmark ANTES (15-20 min)

1. **`Scripts\15_GAMING\gaming.bat`** → menú → opción 1 **Tune-Up**.
2. Detector GPU automático lista hardware (NVIDIA RTX 5080 / AMD Radeon / iGPU descartado correctamente).
3. **Heaven Benchmark** (`Tools\Heaven\`) en preset Extreme 1080p o 1440p según monitor cliente, 3 minutos → captura FPS medio + score. Se guarda en JSON.
4. **Prime95** (`Tools\Prime95\prime95.exe`) modo Small FFTs, 5 min → carga máxima CPU, monitor de temps con HWiNFO en paralelo. Punto base CPU.

### Software fase 2 — Limpieza drivers GPU (15-20 min)

5. **DDU** (`Tools\DDU\DDU.exe`):
   - Modo silencioso configurado por script (`-cleanandexit -silent`).
   - DDU pide reinicio en **Modo Seguro**. Script avisa al técnico: "reinicia ahora en Modo Seguro y vuelve a lanzar `gaming.bat`, retomará donde quedó".
   - Técnico reinicia con shift+reiniciar → opciones avanzadas → modo seguro.
6. (Tras reinicio) Relanzar `gaming.bat` con la misma sesión → script detecta paso DDU completado → salta a instalación driver nuevo.
7. **Driver fabricante último vía winget**:
   - NVIDIA: `winget install Nvidia.GeForceExperience` (incluye driver actualizado).
   - AMD: `winget install AMD.RadeonSoftware`.
   - Intel ARC: `winget install Intel.IntelArcGraphicsDriver`.
8. Reinicio Windows normal.

### Software fase 3 — Tuning ventiladores (10 min)

9. **Fan Control** (`Tools\FanControl\FanControl.exe`):
   - Lanza la app.
   - Importar perfil `Tools\FanControl\plantillas\fan_curve_conservadora.json` (30°C silencio → 50°C medio → 70°C suave → 80°C tope).
   - Aplicar y arrancar Fan Control con Windows automáticamente (config del cliente, no del técnico).
   - Cliente puede ajustar después si quiere más silencio o más rendimiento.

### Software fase 4 — Undervolt (15-30 min, opcional con flag)

10. Solo si flag `-EnableUndervolt` + `Profile1.mvc` existe:
    - Snapshot stock primero (script guarda voltaje original por si hay que revertir).
    - Aplicar curva conservadora -50mV.
    - **Test estabilidad obligatorio** Prime95 + Heaven en bucle 15 min:
      - Si pasa sin crashear → guardar perfil. VERDE.
      - Si crashea o cuelga → REVERTIR automático a stock + ROJO en JSON manifest. Cliente queda como estaba.
11. Si AMD sin CLI → ámbar manual_requerido. Mostrar al cliente al final cómo abrir Adrenalin → tab Performance → Tuning → Custom → Apply Undervolt.

### Software fase 5 — Apps gaming (10-15 min)

12. Vía winget (NO login cliente, solo instalar):
    - `winget install Valve.Steam`
    - `winget install EpicGames.EpicGamesLauncher`
    - `winget install Discord.Discord`
    - `winget install Nvidia.GeForceExperience` (si NVIDIA, ya estará).
13. Cliente hará login él en sus cuentas después.

### Software fase 6 — Benchmark DESPUÉS (10-15 min)

14. Heaven mismo preset que ANTES + Prime95 mismas condiciones.
15. Comparar FPS / score / temps en JSON. Mejora típica:
    - **CPU temp**: 5-10°C menos (gracias a pasta + tuning fans).
    - **GPU FPS**: 3-12% más (drivers limpios + temps mejores → menos throttling).
    - Con undervolt encima: GPU temp -10°C, ruido -30%, FPS igual o ligeramente mejor.

### Físico (técnico, en paralelo a software fases 1-3)

1. **Apagar PC**, desconectar todo. Mesa de trabajo.
2. **Abrir caja** (gaming suele tener tornillos cómodos). Foto interior con polvo.
3. **Soplado y brocha**:
   - Filtros frontales/superiores/inferiores (sacar y golpear).
   - Aspas todos los ventiladores (sujetar).
   - Disipador CPU (importante en gaming, suelen tener bastante polvo).
   - Disipador GPU si accesible sin desmontar (no desmontar GPU salvo necesidad real, los ventiladores GPU son frágiles).
   - Fuente (rejillas, NO ABRIR).
4. **Disipador CPU fuera**:
   - Aflojar tornillos en cruz.
   - Limpiar pasta vieja IHS y disipador con isopropílico + bayeta microfibra.
5. **Pasta nueva Arctic MX-6** (gota arroz centro IHS).
6. **Pads térmicos**: si hay VRM o VRAM con pads secos/aplastados → cambiar. NO tocar pads que estén bien (perder un pad bueno por uno peor es bug).
7. **Reensamblar disipador**, apretar en cruz sin pasarse.
8. **Foto interior limpio**.
9. **Cerrar caja**, conectar todo.

---

## Al cerrar (15-20 min)

1. Sentar cliente delante. Enseñar:
   - **Heaven antes vs después**: número FPS y score lado a lado.
   - **Temps CPU antes vs después** (HWiNFO).
   - **Tu juego que más juegas**: cliente pone su juego, jugar 5 min con MSI Afterburner OSD activado mostrando FPS.
2. **Explicar Fan Control**:
   - "Esta app arranca con Windows sola, controla tus ventiladores. Si quieres más silencio, baja la curva en esta zona [señalar]. Si quieres más rendimiento al jugar, sube la zona alta".
3. **Si undervolt aplicado**: "Tu GPU ahora consume menos voltaje. Funciona igual o mejor. Si en algún juego tienes crashes (raro porque es perfil conservador), me llamas y revierto sin coste".
4. **`Scripts\14_ENTREGA\entrega.bat`** → 3 entregables.
5. **Cobrar 160€** + recargo zona.
6. Trigger **"hemos terminado"** en Claude.

---

## Errores frecuentes / casos raros

_Pendiente actualizar tras 5 visitas reales._

---

## Tiempo total estimado

- **Mínimo**: 2h (PC accesible, sin undervolt, drivers OK, polvo razonable).
- **Realista**: 3h.
- **Jodido**: 4h+ (caja gaming compleja con cable management apretado, undervolt con tests largos, GPU con disipador agarrado).

---

## Reglas críticas

- ⚠️ **NO buscar el límite del undervolt**. -50mV es bueno y conservador. Si encuentras que aguanta -100mV, NO lo aplicas — buscas estabilidad, no récord.
- ⚠️ **NO tocar overclock CPU/GPU**. Es responsabilidad legal si peta. Cliente puede pedirlo, le dices que es servicio aparte y bajo su firma.
- ⚠️ **NO BIOS settings**. Nada de modificar XMP, voltajes desde BIOS, perfiles ASUS/MSI/Gigabyte raros. Si algo BIOS, fuera de pack.
- ⚠️ **NO login cuentas cliente**. Steam, Epic, Discord las arranca él con su cuenta.
- ⚠️ Si el cliente tiene una **GPU vieja** (1060, 1070, etc.) y pide undervolt agresivo → conservador igual. Una GPU vieja peor toleraba undervolt que una nueva.
