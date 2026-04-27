# Formateo + Backup y restauración — 90€

**ID tarifa:** `pack_formateo_backup`
**Bloque:** B Mantenimiento · Software
**Tiempo realista:** 3h (rango 2-5)
**Cuando aplica:** Windows roto, malware persistente, BSOD recurrentes, performance irrecuperable. Cliente quiere "borrón y cuenta nueva" PERO conservando archivos personales y configuraciones (marcadores, WiFi, fondo, apps barra, iconos escritorio).

⚠️ **Requiere firma expresa del cliente** asumiendo que se borra el sistema. Aunque el script #34 captura, el backup es la red de seguridad — la firma protege legal.

---

## Antes de visita

- **Confirmar al teléfono**: ¿Windows arranca al menos hasta entrar al escritorio? Si NO arranca → necesitarás Ventoy y Clonezilla (incluido en plan).
- **Confirmar clave Windows**: cuenta MS vinculada (preferible) o clave OEM en BIOS. Si ninguna y el cliente compró el PC sin Windows → +Instalación Windows OEM 80€ aparte (con licencia que se compra).
- **Confirmar volumen archivos personales**: si dice "1-2 TB de fotos y vídeos" → llevar Seagate 4TB sí o sí, y avisar tiempo extra.

**Llevar:**
- USB MASTER (D:) + BACKUP (I:) maletín.
- USB rojo Ventoy (5 ISOs + MemTest86) por si Windows no arranca.
- Disco Seagate 4TB para backup intermedio.
- Adaptador SATA-USB y NVMe-USB por si hay que sacar disco.

---

## Al llegar (10-15 min)

1. Saludar, ubicar PC, foto inicial.
2. **`Scripts\0_LLEGADA\llegada.bat`** → checklist firmada (cubre la firma legal del formateo en el documento).
3. **Diagnóstico inicial**: ¿hasta dónde llega Windows? ¿pantalla bloqueo? ¿BSOD al boot? ¿modo seguro arranca?
4. Si Windows arranca → vamos a captura sin USB rescate.
5. Si NO arranca → siguiente sección "Caso Windows muerto".

---

## Durante

### Caso A: Windows arranca (camino normal)

#### Software fase 1 — Captura (45-60 min)

1. **`Scripts\13_RESTAURAR\guardar.bat`** desde USB MASTER → orquestador 10 pasos:
   - Marcadores Edge/Chrome/Firefox/Brave (.bak).
   - Passwords (Plan A si Edge/Chrome con cuenta MS sincronizada).
   - WiFi (perfiles con contraseña en claro vía `netsh wlan export`).
   - Impresoras (excluye Microsoft Print to PDF nativa).
   - Fondo escritorio (TranscodedWallpaper).
   - Apps barra tareas (8-10 .lnk típico).
   - Iconos escritorio (todos los `.lnk`).
   - Carpetas Quick Access / favoritas Explorer.
   - Clave OEM Windows (solo OA3xOriginalProductKey de BIOS, sin fallback Registry — incidente #34).
   - Metadata equipo (hostname, zona horaria).
2. Manifiesto JSON guardado al USB MASTER (`MEDICOPC_MASTER\MedicoPC_Restaurar\<sesion>\manifiesto.json`).
3. **Backup archivos personales** al disco Seagate 4TB:
   - `C:\Users\<cliente>\Documents`, `Desktop`, `Pictures`, `Videos`, `Downloads` (preguntar cliente).
   - Carpetas custom si el cliente indica (por ejemplo `D:\Mis Cosas\`).
   - Robocopy `/MIR /R:2 /W:5` para que copia sea fiable y no se quede en archivos bloqueados.

#### Software fase 2 — Reinstalación (45-90 min)

4. Reinicio con USB rojo Ventoy → seleccionar ISO Windows correspondiente:
   - **Windows 11 25H2** si TPM 2.0 + CPU compatible.
   - **Windows 10 22H2** si NO TPM o CPU vieja (avisar cliente: ESU pago opcional 2026+).
5. Borrar TODAS las particiones del disco origen → instalación limpia.
6. Cuenta local con nombre del cliente (NO obligar Microsoft Account si no quiere).
7. Activación: si OEM en BIOS → automática. Si cuenta MS → login y vincular. Si nada → cliente busca su clave email/web.

#### Software fase 3 — Restauración (45-60 min)

8. **`Scripts\13_RESTAURAR\restaurar.bat`** apuntando al manifiesto del USB:
   - Devuelve los 10 componentes capturados.
   - Activación Windows: 3 ramas (verde si ya activado / ámbar si sin OEM o no aplicable / verde con `slmgr /ipk` solo si OEM válida y no es clave KMS Setup blacklisted).
9. **Restaurar archivos personales** desde Seagate al PC del cliente. Robocopy con la misma estructura.
10. **Drivers críticos** vía winget:
    - `winget install Nvidia.GeForceExperience` o `AMD.RadeonSoftware`.
    - Chipset según fabricante placa.
    - Audio Realtek si placa lo requiere (winget o web fabricante).
11. **Pre-entrega**: AdwCleaner + Sysinternals Autoruns para dejar todo limpio.

### Caso B: Windows NO arranca

1. Arrancar **Clonezilla** desde USB rojo Ventoy.
2. **Clonar disco origen → imagen `.img` en Seagate 4TB** ANTES de tocar nada. Si más adelante el disco peta o falta algo, tienes la imagen.
3. Volver a arrancar Windows. Si entra → Caso A.
4. Si no entra ni con Modo Seguro → ir directo a fase 2 (reinstalación). Los archivos personales tendrás que sacarlos de la imagen Clonezilla después montándola.

### Físico (técnico)

- **Mínimo**. No requiere abrir PC normalmente.
- Si durante el formateo detectas SSD que tarda barbaridades en escribir o lecturas SMART feas → propón cambio (servicio aparte bloque C, instalación 30€ + pieza).

---

## Al cerrar (15-20 min)

1. Sentar cliente delante. Enseñar:
   - **Marcadores** en Edge → "están todos".
   - **WiFi** conectada sola.
   - **Fondo** suyo.
   - **Iconos escritorio** suyos.
   - Carpeta `Documentos` con sus archivos.
2. Mostrar lista de **apps que NO se restauran automático** (Office, Photoshop, juegos Steam, etc.) — el cliente las reinstala con su cuenta. Ofrecer instalar las top 3-5 vía winget si quiere (incluido en pack).
3. **`Scripts\14_ENTREGA\entrega.bat`** → 3 entregables.
4. **Cobrar 90€** + recargo zona si aplica.
5. Trigger **"hemos terminado"** en Claude.

---

## Errores frecuentes / casos raros

_Pendiente actualizar tras 5 visitas reales._

---

## Tiempo total estimado

- **Mínimo**: 2h (Windows arrancable, SSD, archivos cliente <100GB, drivers fáciles).
- **Realista**: 3h.
- **Jodido**: 4-5h (HDD lento, >500GB archivos, drivers raros que toca buscar a mano, activación con problemas).

---

## Reglas críticas

- ⚠️ **Firma expresa del cliente ANTES de borrar nada**. Sin firma, no hay formateo. La checklist de #36 LLEGADA cubre legalmente.
- ⚠️ **Backup VERIFICADO antes de borrar**. Robocopy /MIR debe terminar con 0 errores. Abrir aleatoriamente 2-3 archivos del Seagate para confirmar que copió bien (NO mirar contenido por privacidad, solo abrir para ver que se abre).
- ⚠️ **Disco origen ≠ disco backup**. Nunca formatear sin tener la copia en otro disco físico distinto.
