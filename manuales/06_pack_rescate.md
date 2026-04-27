# Pack Rescate — 200€

**ID tarifa:** `pack_rescate`
**Bloque:** F Packs temáticos
**Tiempo realista:** 6h (rango 4-14)
**Cuando aplica:** TODO ROTO. Cliente desesperado: PC no arranca, archivos perdidos, malware grave, BSOD recurrentes, Windows corrupto. Pack que combina **Diagnóstico (25€) + Recuperación N1 (130€) + Formateo (70€) + Backup (90€)** = ahorro ~115€ vs servicios sueltos. Cubre el escenario "salva lo que puedas y déjamelo funcionando otra vez".

⚠️ **Escenario emocionalmente cargado**. Cliente puede haber perdido fotos familiares, tesis, archivos del trabajo. Honestidad brutal en expectativas y sin promesas que no puedas cumplir.

---

## Antes de visita

- **Llamada larga al teléfono** (10-15 min):
  - Síntoma exacto: "¿qué hace? ¿qué dejó de hacer? ¿desde cuándo? ¿pasó algo (apagón, golpe, descarga eléctrica, virus)?".
  - Volumen archivos críticos: "¿cuánto tienes que recuperar como prioridad? ¿fotos? ¿documentos?".
  - **Frase exacta a decir**: _"Voy a hacer todo lo posible. Voy a recuperar lo que se pueda del disco actual y a dejarte Windows funcionando otra vez. Si el disco está físicamente roto, te derivo a laboratorio aparte (350-800€). No te puedo prometer 100% de los archivos, pero sí me dejo la piel."_
  - Avisar plazos: **mínimo 4-6h en sitio**, puede partirse en 2 visitas si volumen grande.
- Si el cliente está demasiado nervioso al teléfono → más calma, recordar que la mayoría de N1 sale bien (70-85% éxito).

**Llevar TODO:**
- USB MASTER + BACKUP (D: e I:).
- USB rojo Ventoy (5 ISOs + MemTest86).
- Disco Seagate 4TB (vacío idealmente, mínimo 1.5TB libre).
- Adaptadores SATA-USB y NVMe-USB.
- Kit destornilladores completo.
- Pasta térmica + pads (limpieza incluida en pack si tiene polvo).
- Aire comprimido + brocha.
- ⚠️ **Tiempo previsto: 6h+. Si vas con prisa o tienes cita después, NO COJAS el Pack Rescate**. Dile al cliente "esta semana no puedo, te llamo el lunes".

---

## Al llegar (15-20 min)

1. Saludar con tono calmado. Cliente puede estar agobiado.
2. **`Scripts\0_LLEGADA\llegada.bat`** → checklist firmada (importantísima en este servicio: cubre que tasa éxito no es 100%, que se va a formatear el sistema, que puede haber datos no recuperables).
3. **Diagnóstico visual + escucha**:
   - **¿Clicks rítmicos** del HDD? Stop, derivar N2 antes de tocar nada.
   - **¿Olor a quemado**? Stop, posible problema placa o fuente, otro tipo de servicio.
   - **¿Calienta extremo?** Apagar 10 min, volver a evaluar.
4. Foto estado físico inicial + interior si sospechas problema físico.

---

## Durante — 4 fases ESTRICTAS, no saltar pasos

### FASE 1 — Diagnóstico (15-30 min)

#### Caso A: PC arranca al menos a algo
1. **`Scripts\11_DIAGNOSTICO_LLEGADA\guiado.bat`** → captura SMART, hardware, eventos sistema, drivers crashed.
2. Decisión:
   - SMART verde + sin clicks + Windows medio funciona → continuar fase 2.
   - SMART rojo o reallocated >100 → **STOP, derivar N2**. Cobras 25€ Diagnóstico solo. Comunicar cliente: "el disco está físicamente comprometido, no quiero romperlo más, te derivo al laboratorio".

#### Caso B: PC NO arranca
1. **USB rojo Ventoy** → **MemTest86** → 1 pasada completa (~30-60 min según RAM). Si falla → problema RAM, no formateo. Diagnóstico aparte.
2. Si MemTest pasa → **Clonezilla** del Ventoy → **clonar HDD/SSD a imagen `.img`** en Seagate 4TB **ANTES de tocar nada**. ⚠️ Crítico: si el disco peta durante recuperación, tienes la imagen para retomar.
3. Trabajar sobre la imagen montada en lugar del disco real (montaje read-only).

### FASE 2 — Recuperación N1 (1-5h según volumen)

1. **`Scripts\17_RECUPERACION\recuperacion.bat`** → triaje + selección destino + PhotoRec/TestDisk.
2. Si Caso B con imagen Clonezilla → script puede trabajar sobre el archivo `.img` montado.
3. PhotoRec recupera al Seagate 4TB intermediario en `Datos_Cliente_Limpios\`.
4. Clasificador post-PhotoRec: dedup + filtro basura + categorización.
5. **Verificar resultado** antes de seguir: abrir 2-3 archivos al azar (sin mirar contenido) para confirmar que se abren.
6. ⚠️ **NO seguir a fase 3 hasta tener la recuperación validada y copiada al Seagate**.

### FASE 3 — Formateo + Reinstalación Windows (1-2h)

1. Si Windows existía y arranca al menos al escritorio:
   - **`Scripts\13_RESTAURAR\guardar.bat`** → captura WiFi, marcadores, fondo, apps barra (lo que se pueda — pueden estar comprometidos por malware, da igual, mejor algo que nada).
2. **USB rojo Ventoy** → ISO **Windows 11 25H2** si TPM 2.0 + CPU compatible, o **Windows 10 22H2** si no.
3. Borrar TODAS las particiones del disco origen (incluida la de recuperación OEM rota).
4. Instalación limpia.
5. Cuenta local con nombre del cliente. NO obligar Microsoft Account si cliente prefiere local.
6. Activación: OEM BIOS automática / cuenta MS vinculada / clave aparte si tiene.

### FASE 4 — Restauración + entrega de datos (45-90 min)

1. **`Scripts\13_RESTAURAR\restaurar.bat`** apuntando al manifiesto del USB → devuelve marcadores, fondo, apps barra, iconos escritorio (lo recuperable). Activación Windows (3 ramas).
2. **Copiar `Datos_Cliente_Limpios\` del Seagate al PC del cliente**:
   - Ruta destino: `C:\Users\<cliente>\Documents\Recuperado_MedicoPC\<fecha>\`
   - Categorías separadas: `imagenes/`, `documentos/`, etc.
   - Robocopy /MIR con log para que el cliente pueda revisar después qué se copió.
3. **Drivers críticos** vía winget: chipset, GPU (Nvidia.GeForceExperience o AMD.RadeonSoftware), audio si hace falta.
4. **Pre-entrega**:
   - **Sysinternals Autoruns** → revisar startup limpio.
   - **AdwCleaner** → escaneo final por si quedó algo raro.
   - **Windows Update** → todas las actualizaciones críticas (puede ser otra hora más).

### Físico (limpieza incluida en pack)

- Si tiene polvo significativo → soplado + brocha.
- Si pasta térmica >2 años → cambio incluido (Arctic MX-6 o KTC1).
- Foto antes/después del interior.

---

## Al cerrar (30-45 min, briefing largo)

1. **Sentar al cliente delante**. Tomarse tiempo. Es un servicio caro y emocional.
2. **Mostrar Windows funcionando**:
   - WiFi conectada.
   - Marcadores donde estaban.
   - Fondo suyo.
3. **Mostrar carpeta `Recuperado_MedicoPC`**:
   - "Esto es lo que rescaté de tu disco antiguo. Aquí están las imágenes, aquí los documentos, aquí los vídeos".
   - Abrir 2-3 archivos delante (sin mirar contenido más de la cuenta).
   - "Los nombres están reconstruidos, la mayoría no son los originales. Tu `Tesis_Final.docx` ahora se llama `f0001234.docx`, ábrelos y renómbralos como te apetezca".
   - "PhotoRec recupera todo lo que encuentra, incluso archivos que tú habías borrado adrede hace años. Si ves cosas raras, normal. Bórralas si quieres".
4. **Lo que SE PERDIÓ honestamente**:
   - Configuración de programas instalados (los reinstalará él con sus cuentas).
   - Apps con licencias compradas (Office, Photoshop, juegos Steam) → tendrá que iniciar sesión él.
   - Si algunos archivos no aparecen → pudieron estar sobreescritos antes de la recuperación. Eso ya no se puede recuperar (mentir aquí destroza la confianza).
5. **`Scripts\14_ENTREGA\entrega.bat`** → 3 entregables. La factura sale con descripción "Pack Rescate" que ya cubre el desglose interno.
6. **Cobrar 200€**. Si N2 fue derivado (caso poco común dentro de Pack Rescate) → factura partner aparte + 60€ gestión sumados.
7. Trigger **"hemos terminado"** en Claude.

---

## Errores frecuentes / casos raros

_Pendiente actualizar tras 5 visitas reales._

---

## Tiempo total estimado

- **Mínimo**: 4h (caso suave: SSD recuperable, Windows reinstalable rápido, drivers fáciles).
- **Realista**: 6h (lo normal en Pack Rescate, caso medio).
- **Jodido**: 10-14h → **partir en 2 visitas** o **llevarse PC al taller** (+25€ recogida).

---

## Reglas críticas

- ⚠️ **NUNCA prometas recuperación 100%**. Frase exacta para evitar líos: _"voy a recuperar lo que se pueda, te dejo Windows funcionando, y si el disco está físicamente roto te derivo a laboratorio aparte"_.
- ⚠️ **Orden estricto fases**: Diagnóstico → N1 → Formateo → Restauración. **NO formatear sin tener la N1 validada y copiada al Seagate**. Saltarse el orden = potencialmente perder datos del cliente para siempre.
- ⚠️ **Imagen Clonezilla cuando el disco está delicado**. Si SMART tiene errores pero menores, o el disco hace ruidos raros pero arranca → imagen forense ANTES. Pierdes 30-60 min, ganas tranquilidad.
- ⚠️ **Privacidad cliente** (igual que Recuperación N1 sola): no abres archivos, no comentas qué hay, mira para otro lado si el cliente abre algo sensible delante de ti.
- ⚠️ **Tiempo realista al telefonear**: si dices 4h y son 8h, pierdes confianza. Mejor decir "4-8h dependiendo del caso, te aviso en cada paso".
- ⚠️ **Si el cliente está MUY desesperado** (lloriquea, suplica, ofrece más dinero) → mantén calma profesional. NO prometas. NO subas precio aunque te lo pida (200€ fijo del pack). Eres el técnico, no el psicólogo, pero la calma transmite.
