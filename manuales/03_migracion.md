# Migración PC viejo → nuevo — 100€

**ID tarifa:** `migracion`
**Bloque:** B Mantenimiento · Software
**Tiempo realista:** 2.5h (rango 1.5-4)
**Cuando aplica:** Cliente compró PC nuevo (con Windows ya instalado), quiere todo lo del viejo: archivos personales, navegadores, configuraciones, apps básicas. **NO** incluye instalación Windows (eso es 80€ aparte). **NO** sirve si el PC viejo no arranca (eso es Pack Rescate o derivar).

---

## Antes de visita

- **Confirmar AMBOS PCs disponibles en visita simultáneamente** (origen y destino). Sin los 2 no hay migración.
- **Confirmar PC nuevo arranca a Windows** ya configurado (cuenta Microsoft hecha, escritorio funcional). Si llega virgen sin configurar → primero hay que configurarlo (15-30 min extra incluido).
- **Confirmar credenciales Windows AMBOS PCs** (login del cliente).
- **Estimar volumen archivos**: preguntar "¿cuántos GB de fotos/vídeos/documentos tienes?". Determina método de transferencia.

**Llevar:**
- USB MASTER (D:) + BACKUP (I:).
- **Cable de red corto** (RJ45, 1-2m) — más rápido que WiFi para volúmenes grandes.
- Disco Seagate 4TB intermedio si el método cable directo no encaja por topología del cliente.
- Adaptador USB-Ethernet si el portátil no tiene RJ45.

---

## Al llegar (10 min)

1. Saludar, ubicar AMBOS PCs en la misma mesa o cerca.
2. **`Scripts\0_LLEGADA\llegada.bat`** en cada uno (uno tras otro) → 2 checklists firmadas.
3. Decisión topología transferencia:
   - **Cable directo** (preferible): conectar PCs entre sí con cable RJ45. Configurar IPs estáticas en la misma subred (`192.168.50.10` ↔ `192.168.50.20`). Activar compartir archivos. ~110 MB/s sostenido.
   - **WiFi compartido**: ambos PCs en mismo router. Más lento (~30-50 MB/s típico). Opción si cable no es viable.
   - **Disco intermedio**: Seagate 4TB → copia desde viejo, conectar a nuevo, copia al destino. Más lento (lee + escribe 2 veces) pero a prueba de bombas si la red da problemas.

---

## Durante

### Software fase 1 — En PC viejo (45-90 min)

1. **`Scripts\12_MIGRACION\migracion.bat`** (idea #29 fases a + b1 + b2):
   - **Fase a**: detectar carpetas usuario (Documents, Desktop, Pictures, Videos, Downloads, Music) + carpetas custom típicas (`D:\`, `E:\<algo>`).
   - **Fase b1**: capturar configs Windows reusables (similar a #34 pero adaptado al caso migración):
     - Marcadores Edge / Chrome / Firefox / Brave.
     - Apps barra tareas (lista, no los .exe).
     - Fondo escritorio.
     - Carpetas favoritas Quick Access.
     - Lista WiFi conocidas (con passwords si Plan A funciona).
     - Lista impresoras.
   - **Fase b2**: copia masiva archivos personales al destino elegido (cable / Seagate / WiFi). Robocopy `/MIR` con log detallado.
2. **Detectar apps instaladas** en PC viejo (`Get-ItemProperty HKLM:\Software\Microsoft\Windows\CurrentVersion\Uninstall\*`). Genera lista para mostrar al cliente: "estas apps detecté, las que quieras las reinstalo en el nuevo".

### Software fase 2 — En PC nuevo (45-60 min)

3. **`Scripts\12_MIGRACION\migracion.bat`** modo restauración (fases c + d):
   - **Fase c**: leer manifiesto y devolver configs (marcadores, fondo, WiFi, impresoras conectadas, apps barra que existan en winget).
   - **Fase d**: copiar archivos personales del destino intermedio → carpetas usuario PC nuevo.
4. **Reinstalación apps elegidas por cliente** vía winget (Steam, Discord, navegadores adicionales, Office si tiene clave, etc.). NO login en sus cuentas, solo instalar.
5. **Drivers**: PC nuevo viene con drivers OEM. Solo añadir GPU última versión vía winget (Nvidia.GeForceExperience o AMD.RadeonSoftware).
6. Sincronizar Edge / Chrome con cuenta Microsoft / Google del cliente → marcadores y passwords vienen solos. Solo si el cliente confirma que quiere y mete su contraseña él (NO TÚ).

### Físico (técnico)

- **Mínimo**. Quizá mover algún PC en la mesa para conectar el cable.
- Si el cliente quiere que el PC viejo se vaya (deshecho responsable), se le explica que **no incluye recogida** — eso es servicio aparte si lo aceptamos.

---

## Al cerrar (15 min)

1. Sentar cliente delante del PC NUEVO:
   - Abrir Edge → "tus marcadores están".
   - Abrir Documentos → "tus archivos están".
   - WiFi conectada sola.
   - Fondo suyo.
2. Mostrar lista de **lo que NO se migra** (cuentas Steam con juegos, Adobe con licencia, claves de programas pagados → tienen que iniciar sesión ellos).
3. Recordar al cliente: el PC viejo todavía tiene sus datos. Si quiere venderlo o regalarlo, antes hay que formatearlo (servicio aparte, Formateo seco 70€).
4. **`Scripts\14_ENTREGA\entrega.bat`** → 3 entregables.
5. **Cobrar 100€** + recargo zona.
6. Trigger **"hemos terminado"** en Claude.

---

## Errores frecuentes / casos raros

_Pendiente actualizar tras 5 visitas reales._

---

## Tiempo total estimado

- **Mínimo**: 1.5h (poco volumen <50GB, cable directo, ambos PCs SSD, sin apps complicadas).
- **Realista**: 2.5h.
- **Jodido**: 4h+ (>500GB de archivos, HDD origen lento, sin red entre PCs (toca disco intermedio), 20+ apps a reinstalar).

---

## Reglas críticas

- ⚠️ **NO HACES login** en cuentas del cliente (Google, Microsoft, Steam, Adobe). Si requiere, **el cliente pone su contraseña**, no tú. Privacidad + responsabilidad legal.
- ⚠️ **PC viejo se queda con sus datos**. Si el cliente lo va a vender/regalar, recordar que necesita formateo. NO se lo formateas en esta visita salvo que lo pague aparte.
- ⚠️ **Verificar copia antes de declarar fin**. Abrir 2-3 archivos aleatorios en el PC nuevo (sin mirar contenido, solo confirmar que se abren).
