# Recuperación N1 — 130€

**ID tarifa:** `recup_n1`
**Bloque:** D Recuperación de datos
**Tiempo realista:** 3-5h (rango 1.5-12)
**Cuando aplica:** Disco accesible (Windows lo ve aunque sea como "sin formatear" o disco RAW), SMART OK, **sin clicks ni ruidos raros**. Cliente dice "borré sin querer" / "Windows pide formatear" / "perdí archivos" / "se rompió Windows pero el disco gira".

⛔ **NO aplica si:** SMART rojo, sectores reasignados >100, disco hace clicks, calienta excesivamente, Windows ni siquiera lo detecta. **Esos casos son N2** (laboratorio partner, 350-800€). El script #23 hace triaje automático.

---

## Antes de visita

- **Confirmar al teléfono el síntoma**: ¿el disco se ve aunque no se acceda? ¿hace ruidos raros? ¿desde cuándo? ¿qué pasó (apagón, golpe, virus, borrado accidental)?
- **Avisar tasa éxito honesta**: "N1 ronda 70-85% de éxito según caso. Si SMART está mal, te derivo a laboratorio sin tocar (350-800€). Si está bien pero los archivos se han sobreescrito mucho, recupero menos. No te puedo prometer 100%."
- **Diagnóstico (25€) descontable**: si el cliente solo quiere saber si vale la pena gastar 130€, le haces Diagnóstico primero (con el triaje del script). Si decide tirar adelante, los 25€ se restan del N1 → cobras 105€.

**Llevar:**
- USB MASTER + BACKUP.
- Disco Seagate 4TB destino (espacio libre ≥1.5x el tamaño del disco origen).
- Adaptador SATA-USB y NVMe-USB (para sacar disco si necesario).
- USB rojo Ventoy (Clonezilla por si hace falta imagen forense antes de tocar).

---

## Al llegar (10 min)

1. Saludar, ubicar PC y disco.
2. **`Scripts\0_LLEGADA\llegada.bat`** → checklist firmada (importante: la firma cubre que tasa éxito no es 100%).
3. Inspección física inicial:
   - **Escuchar disco encendido** 10 segundos. Clicks rítmicos = stop, derivar N2.
   - **Tocar suavemente** (no funciona en SSD, sí en HDD): vibración normal vs vibración rara.
   - Olor a quemado o caliente extremo = stop, derivar N2.

---

## Durante

### Triaje (5-10 min)

1. **`Scripts\17_RECUPERACION\recuperacion.bat`** desde USB MASTER.
2. Detector discos automático lista todos los conectados con SMART status, marca, modelo, tipo (SSD/HDD), letras Windows.
3. Triaje en cascada del script: HealthStatus → Wear → ReadErrors → pregunta clicks al técnico → CDI Reallocated si nativo no resuelve.
4. **Resultado triaje**:
   - 🟢 `n1_viable` → continuar.
   - 🔴 `derivar_n2` → STOP. Comunicar cliente, devolver disco. Solo cobras si cliente acepta gestión derivación a partner laboratorio (entonces 130€ + 60€ gestión).

### Aviso TRIM si SSD origen

5. Si origen es SSD y el script lo detecta → muestra aviso al técnico: "TRIM puede haber borrado físicamente los datos si el borrado fue >24h. Tasa de éxito menor en SSD que HDD para borrados antiguos. ¿Continuar? S/N".
6. Comunicar al cliente esa limitación antes de seguir. Si decide parar → cobras solo Diagnóstico 25€.

### Selección destino

7. Script lista discos disponibles con espacio libre. Técnico elige destino.
8. **Validación bloqueante**: destino ≠ origen. Si intentas el mismo, script aborta. NO hay forma de saltarlo.
9. Validación espacio: destino libre ≥ 1.5x tamaño origen (margen para duplicados que filtra el clasificador después).

### Imagen forense (opcional, solo casos sospechosos)

10. Si el disco origen "tiene pinta delicada" (sectores reasignados <100 pero in crescendo, vibración rara, ya tuvo problemas antes), usar flag `-CrearImagenForense`. **PERO** ddrescue no está en `Tools\` — el helper sale ámbar siempre con instrucción "arranca Clonezilla del USB rojo y haz imagen ahí".
11. Flujo Clonezilla manual: arrancar USB Ventoy → Clonezilla → guardar imagen `.img` al Seagate 4TB → trabajar sobre imagen montada en lugar de disco real. Aporta ~30-60 min extra pero protege si el disco se muere mid-recovery.

### Recuperación (1-10h según volumen)

12. Si Windows pide formatear el disco (particiones perdidas) → **TestDisk primero** (`Tools\PhotoRec\testdisk_win.exe`):
    - Menú interactivo, técnico navega ~30s.
    - Analyse → Quick Search → si encuentra particiones, escribir tabla → reboot → recuperación a nivel partición (mejor que PhotoRec porque conserva nombres/estructura).
13. Si TestDisk no resuelve, o el caso es borrado lógico/corrupción FS → **PhotoRec** (`Tools\PhotoRec\photorec_win.exe`):
    - Menú interactivo, técnico configura: tipos de archivo a recuperar (todos por defecto), destino (Seagate 4TB), modo (Free para borrados / Whole para corrupción).
    - PhotoRec genera blob plano sin estructura: `recup_dir.1\f0000001.jpg`, `f0000002.pdf`, etc. Sin nombres originales.
    - Tiempo realista: SSD 500GB ~30 min · HDD 1TB ~3-5h · HDD 2TB ~6-10h.
14. **Mientras corre PhotoRec largo**: si el cliente está incómodo y son >2h, dejar AnyDesk activo para volver remoto + volver al día siguiente a por el disco. Coste recogida +25€ aplica si te lo llevas a taller.

### Clasificador post-PhotoRec

15. Cuando PhotoRec termina, script lanza `clasificador_post.ps1`:
    - Recorre `recup_dir.N\` completos.
    - Hash MD5 primer 1MB de cada archivo → dedup conservando 1 por hash (rápido vs hash completo, false positives nulos en imágenes/docs/videos).
    - Filtra basura por `lista_negra_basura.txt` (.tmp, .log, .lnk, archivos del sistema, fragmentos Windows).
    - Categoriza por extensión: `imagenes/`, `documentos/`, `videos/`, `audio/`, `otros/`.
    - Mueve a carpeta limpia `Datos_Cliente_Limpios\<categoria>\` en el Seagate 4TB del cliente.
    - Genera informe JSON con: total recuperados, tras dedup, tras filtro, por categoría, espacio total MB.

### Físico

- Si disco está en PC cliente y arranca → conexión externa con adaptador es lo más rápido.
- Si necesario sacar disco físicamente del PC cliente → kit destornilladores. Foto antes/después del estado físico (responsabilidad).

---

## Al cerrar (20-30 min)

1. Sentar cliente delante del Seagate 4TB conectado al PC del cliente (o portátil técnico):
   - Abrir carpeta `Datos_Cliente_Limpios\imagenes\` → ver número total + abrir 1-2 thumbnails (NO abrir muchos, privacidad).
   - Mostrar resumen: "X imágenes, Y documentos, Z vídeos recuperados, W GB en total".
2. **Briefing al cliente** (importante, evita malentendidos):
   - "Los nombres están reconstruidos. Tu `Curriculum.docx` ahora se llama `f0001234.docx`. Abre y renombra".
   - "PhotoRec recupera todo lo que encuentra, incluso archivos que tú habías borrado adrede hace tiempo. Si ves cosas que no esperabas, es normal".
   - "El clasificador ha quitado duplicados y basura del sistema. Si echas algo de menos muy específico, dímelo, podemos buscarlo".
3. **Copia los datos al destino que el cliente quiera** (su nuevo disco, otro USB suyo, carpeta concreta del PC).
4. **`Scripts\14_ENTREGA\entrega.bat`** → 3 entregables.
5. **Cobrar 130€** (descontar 25€ Diagnóstico previo si aplicó).
6. Trigger **"hemos terminado"** en Claude.

---

## PRIVACIDAD CLIENTE — REGLA INMUTABLE

⛔ **El script NUNCA abre archivos durante la recuperación**. Solo metadatos (extensión, tamaño, hash binario sin parsear). Aplica a ti también: **NO miras fotos del cliente NI documentos**. Cliente puede tener intimidades (fotos íntimas, escritos personales, documentos médicos). Solo verificas que el archivo se abre cuando enseñas resultados, sin mirar contenido. Si el cliente abre algo delante de ti, mira para otro lado.

---

## Errores frecuentes / casos raros

_Pendiente actualizar tras 5 visitas reales._

---

## Tiempo total estimado

- **Mínimo**: 1.5h (SSD pequeño, recuperación rápida, todo limpio, clasificador eficiente).
- **Realista**: 3-5h (HDD mediano, volumen medio, hay que esperar PhotoRec).
- **Jodido**: 8-12h (HDD grande, dejar con AnyDesk y volver al día siguiente, posible recogida +25€).

---

## Reglas críticas

- ⚠️ **NUNCA ESCRIBIR EN DISCO ORIGEN**. El script lo bloquea pero también ojo manual.
- ⚠️ **Destino ≠ origen** siempre. Bloqueo del script + atención técnico.
- ⚠️ **Privacidad absoluta**. No abres contenido. No comentas con nadie qué viste.
- ⚠️ **Triaje N1 vs N2 al inicio**. Si el script dice derivar, NO insistir. El cliente prefiere pagar partner antes que romper más el disco.
- ⚠️ **Si crees que el disco va a morir mid-recovery** → imagen forense con Clonezilla ANTES. 30-60 min extra pero salva la cara.
