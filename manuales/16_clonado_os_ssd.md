# Clonado OS → SSD nuevo (50€)

> Tiempo realista: **1.5-2.5h** + desplazamiento (depende de tamaño disco)
> Bloque tarifa: **C — Hardware Mano de Obra**
> Modalidad: taller por defecto · domicilio +25€

---

## Qué es y qué NO es

**SÍ es:** clonar el sistema actual del cliente (Windows + programas + datos) a un **SSD nuevo**, conservando todo intacto. Después se cambia el disco origen por el SSD destino, el cliente arranca con su sistema idéntico pero más rápido.

**NO es:**
- ❌ **Cambio SSD/RAM/disco 30€**: instalación física pelada sin clonar. Si el cliente trae SSD para que se lo monte vacío y reinstale Windows aparte → 30€ + 80€ Win 11 OEM = 110€.
- ❌ **Instalación Windows 11 OEM 80€**: instalación limpia desde cero.
- ❌ **Migración 100€**: PC viejo entero → PC nuevo entero (más complejo, incluye programas y configuraciones detectables).

**Cuándo vender Clonado vs Instalación limpia:**
- Cliente **conserva todo**, solo quiere PC más rápido → **Clonado 50€** (+ pieza SSD = 110-145€ total típico).
- Cliente con **sistema sucio / lento por software** → **Formateo + Backup 80€** o **Win 11 OEM 80€** (instalación limpia es mejor).
- Cliente quiere clonado pero el sistema actual está corrupto / lleno de basura → avisar que clonar copia los problemas. Mejor instalación limpia.

**Combos típicos:**
- Cliente con HDD lento, quiere SSD: **30€ MO + 50€ Clonado + SSD pieza (60-95€)** = ~140-175€ total.
- Cliente con SSD pequeño lleno, quiere SSD más grande: mismo combo.

---

## Antes (preparación material)

### Confirmar por WhatsApp
- [ ] **Disco origen**: HDD o SSD. Tamaño usado actual (cliente mira en Mi PC → click derecho disco C → Propiedades).
- [ ] **SSD destino**: ¿lo trae el cliente o lo pido yo? Tamaño (debe ser ≥ tamaño usado actual). Marca.
- [ ] **Marca SSD destino** importa para elegir herramienta de clonado:
  - **Samsung** → Samsung Data Migration (oficial gratis).
  - **Crucial / WD / Kingston** → Acronis True Image OEM (gratis con marca).
  - **Otros** (Kingston NV2, marca rara) → Clonezilla del USB Ventoy.

### Material en mochila
- [ ] **USB Ventoy rojo** con `clonezilla.iso` (siempre).
- [ ] **USB MASTER** con Tools.
- [ ] **Adaptador USB → NVMe / SATA** (para conectar el SSD destino externamente durante clonado, evitar abrir y cerrar PC dos veces).
- [ ] **Destornilladores** + bandeja imantada (si toca instalar el SSD nuevo).

---

## Al llegar

- [ ] Foto del equipo cerrado.
- [ ] Comprobar **espacio usado** en disco origen: Mi PC → propiedades. Verificar que cabe en el SSD destino.
- [ ] Si el disco origen está al **>90% lleno** → recomendar limpieza previa (basura, temporales) antes de clonar. **Limpieza Básica 60€** opcional o lo hago de bonus si toma <15 min.
- [ ] Foto del estado del disco con el espacio actual.

---

## Durante — Método A: Herramienta del fabricante (preferido)

### Caso Samsung (Samsung Data Migration)

**Cuándo:** SSD destino es Samsung (870 EVO, 980, 990 Pro, etc.).

#### Paso 1 — Conectar SSD destino externamente

1. Conectar SSD nuevo al adaptador USB.
2. Enchufar al PC. Windows lo detecta como disco vacío.
3. Inicializar GPT desde Administración de discos si pide.

#### Paso 2 — Instalar Samsung Data Migration

1. Descargar última versión de [samsung.com/semiconductor/minisite/ssd/download/tools/](https://semiconductor.samsung.com/consumer-storage/support/tools/).
2. Instalar y abrir.
3. La aplicación detecta automáticamente el disco origen (Windows) y el SSD Samsung destino.

#### Paso 3 — Clonar

1. Click **Iniciar**.
2. Si el disco origen es **mayor que el SSD destino pero los datos caben** → la app reduce automáticamente la partición C: al tamaño de los datos.
3. Si los datos NO caben → reducir manualmente carpetas grandes antes de clonar (Descargas, Vídeos, Fotos basura).
4. Espera 30-90 min según tamaño.
5. Mensaje "Clonado completado".

### Caso Crucial / WD / Kingston (Acronis True Image OEM)

**Cuándo:** SSD destino es Crucial, WD Blue/Black, Kingston KC-series, etc.

1. Descargar la versión OEM gratuita vinculada a la marca:
   - **Crucial**: [crucial.com/clone](https://www.crucial.com/support/storage-acronis-true-image-for-crucial).
   - **WD**: Acronis True Image WD Edition desde web WD.
   - **Kingston**: Acronis True Image HD desde Kingston (ojo, algunos modelos no incluyen).
2. Instalar (la app verifica que tienes un SSD de la marca conectado, si no → no funciona).
3. Conectar SSD destino externamente.
4. Abrir Acronis → **Clonar disco** → seleccionar origen y destino → clonar.
5. Espera tiempo similar a Samsung.

### Caso genérico / SSD marca rara (Macrium Reflect Free deprecated, usar Clonezilla)

⚠️ **Macrium Reflect Free YA NO SE OFRECE** (descontinuado a partir de 2024). Si tenías la versión vieja sigue funcionando, pero NO se recomienda para nuevos clientes.

**Para genéricos → Método B (Clonezilla)**.

---

## Durante — Método B: Clonezilla (universal, más técnico)

**Cuándo:** SSDs sin herramienta del fabricante, o si Método A falla.

### Paso 1 — Conectar SSD destino externamente o instalado

- Externamente con adaptador USB es más fácil (no tienes que abrir el PC todavía).
- Si el PC tiene 2 slots M.2 y caben los dos SSD a la vez → instalar el destino directamente.

### Paso 2 — Arrancar Clonezilla

1. USB Ventoy rojo → seleccionar `clonezilla-live-XXX.iso` → Boot.
2. Seleccionar **Clonezilla live (default)**. Enter.
3. Idioma: **Español** o **English** (lo conoces mejor).
4. Configuración teclado: **Don't touch keymap**.
5. **Start Clonezilla**.

### Paso 3 — Modo de clonado

1. Seleccionar **device-device** (clonado disco a disco directo, NO image).
2. Modo: **Beginner**.
3. Operación: **disk_to_local_disk** (disco origen → disco destino).
4. **OJO con la siguiente pantalla**: Clonezilla pide elegir el disco ORIGEN (el que se va a clonar). Identificar bien:
   - Tamaño (origen suele ser el que tiene Windows).
   - Modelo SSD (visible en la lista).
   - Si dudas → cancelar y comprobar con `lsblk` en otra terminal.
5. Pantalla siguiente: disco DESTINO. Mismo cuidado.

⚠️ **Si te equivocas y eliges destino como origen** → SOBRESCRIBES el disco con Windows. **NO HAY VUELTA.** Triple comprobación antes de Enter.

### Paso 4 — Opciones avanzadas

1. **Skip checking source filesystem** (saltar comprobación previa, ahorra 10 min).
2. **Choose what to do at the end** → Choose later.
3. Confirmar: **"This program will overwrite all data on the target disk"** → escribir **`y`** + Enter.
4. Segunda confirmación: **`y`** + Enter.
5. Tercera confirmación: **clonar tabla de particiones también**: **`y`** + Enter.

### Paso 5 — Esperar

- 30-90 min según tamaño y velocidad.
- Pantalla muestra progreso por partición.
- Al acabar: opción **reiniciar / apagar** → seleccionar apagar.

### Paso 6 — Cambiar disco físicamente

1. Apagar PC, desenchufar.
2. Abrir tapa.
3. **Quitar disco origen** (HDD o SSD viejo).
4. **Instalar SSD destino** en la misma posición (slot M.2 o bahía SATA).
5. Cerrar tapa.

### Paso 7 — Arrancar y verificar

1. Encender PC.
2. **Si arranca normal** → ✅ clonado OK. Saltar a paso 8.
3. **Si NO arranca** (BIOS no encuentra sistema):
   - Entrar BIOS → comprobar orden de arranque, poner el SSD nuevo arriba.
   - Si sigue fallando → puede que el bootloader Windows necesite reparación. Arrancar con USB Ventoy → instalador Windows → Reparar el equipo → Solucionar problemas → Reparación de inicio.

### Paso 8 — Expandir partición C: (si SSD destino es mayor)

1. Ya en Windows: Win + X → Administración de discos.
2. Verás la partición C: con el tamaño antiguo + espacio sin asignar al final.
3. Click derecho en C: → **Extender volumen** → siguiente, siguiente. Toma todo el espacio.
4. Si la partición de Recovery está EN MEDIO bloqueando la extensión:
   - Mover Recovery con GParted (USB Ventoy → GParted) o programa similar.
   - Casos raros, ~20% de las veces.

---

## Al cerrar

- [ ] Cerrar PC, foto del equipo montado.
- [ ] Comprobar:
  - Windows arranca rápido (el cliente nota la diferencia HDD → SSD inmediatamente).
  - **Velocidad arranque**: cronometrar antes (en HDD si era HDD origen) y después (SSD). Mostrar al cliente.
  - **Activación Windows**: sigue activado (el clonado mantiene la licencia digital).
  - Programas, archivos, escritorio: TODO igual.
- [ ] **CrystalDiskInfo** sobre el SSD nuevo: estado azul, horas de uso 0-5.
- [ ] Cobrar **50€** + pieza si la traje yo.
- [ ] Lanzar `entrega.bat` → factura `MPC-2026-XXXX`.
- [ ] **Disco origen viejo**:
  - Si el cliente lo quiere conservar → entregárselo (cliente sabe que tiene sus datos viejos ahí, decisión suya).
  - Si quiere borrarlo → comentar opción de borrado seguro con GParted/shred (gratis si toma <10 min, sino +20€ servicio).
- [ ] Frase cierre: **"Garantía 30 días en la mano de obra. Si Windows da problemas relacionados con el clonado, vuelvo gratis. La pieza SSD tiene su garantía propia (3-5 años el fabricante)."**

---

## Errores frecuentes

_Pendiente actualizar tras 5 visitas reales._

Anticipados:
- **SSD destino más pequeño que origen** + datos no caben: cliente tiene que liberar espacio antes. Si rechaza → no se puede clonar.
- **Disco origen con sectores defectuosos**: clonado falla a media. Comprobar SMART antes (CrystalDiskInfo). Si malo → no clonar, mejor recuperación N1 + instalación limpia.
- **Windows no arranca tras cambiar disco** (BIOS no detecta MBR/EFI bien): Reparación de inicio con instalador Win soluciona el 90% de casos.
- **Activación se cae** tras clonado: a veces sucede si el SSD destino tiene número de serie distinto y la licencia digital se reasigna mal. Esperar 24h. Si persiste → contactar MS.
- **Clonado a SSD NVMe en sobremesa con BIOS Legacy**: BIOS muy viejas no arrancan desde NVMe. Necesita actualización BIOS o se queda en SATA.
- **Cliente con BitLocker activo**: clonado SE PUEDE hacer pero después BitLocker pide la clave de recuperación. Si el cliente la tiene → OK. Si no → ⚠️ STOP, no clonar hasta que la consiga.

---

## Tiempo total

- Disco origen 250GB: **30-45 min** clonado + 30 min preparación / cambio físico = **1.5h**.
- Disco origen 500GB: **45-60 min** clonado + 30 min = **2h**.
- Disco origen 1TB: **60-90 min** clonado + 30 min = **2.5h**.
- Disco origen >2TB: **2h+** clonado, mejor en taller.

---

## Reglas críticas

🔴 **TRIPLE comprobación origen vs destino** antes de confirmar clonado. Equivocarse = pérdida total de datos.
🔴 **CrystalDiskInfo al disco origen ANTES de clonar.** Si tiene sectores defectuosos → no clonar, mejor recuperar primero.
🔴 **Espacio usado origen ≤ tamaño destino.** Confirmar antes.
🔴 **BitLocker activo sin clave** → STOP, derivar.
🔴 **NO usar Macrium Reflect Free a clientes nuevos** (descontinuado, no actualiza).
🔴 **Foto antes/después del clonado** + estado SMART antes/después.
🔴 **Disco viejo**: preguntar al cliente si lo quiere o lo borro/destruyo. NO tirar a la basura sin preguntar (datos personales).
🔴 **Activación Windows** debe seguir OK tras clonado. Si falla → no es problema de mi mano de obra (problema MS) pero ayudar al cliente a contactar soporte.
🔴 **NUNCA clonar a un SSD que ya tiene Windows funcionando** sin avisar (sobrescribes su sistema).
