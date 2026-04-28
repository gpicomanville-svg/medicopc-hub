# Formateo seco (70€)

> Tiempo realista: **2-3h**
> Bloque tarifa: **B — Mantenimiento Software**
> Modalidad: taller por defecto · domicilio +25€

---

## Qué es y qué NO es

**SÍ es:** instalación limpia de Windows desde cero **SIN guardar nada del usuario** (datos, programas, configuración). Versión rápida y barata para casos donde el cliente:
- No le importan los datos (ya los tiene en otro sitio).
- El PC está tan podrido que el backup no merece la pena rescatar.
- Va a regalar/vender el PC y quiere reset de fábrica.

**NO es:**
- ❌ **Formateo + Backup 80€**: incluye copia de Documentos, Fotos, Escritorio, marcadores navegador, perfiles correo. Servicio estándar para clientes que quieren conservar sus cosas.
- ❌ **Migración 100€**: PC viejo → PC nuevo conservando todo (datos + programas + config).
- ❌ **Recuperación de datos**: si el cliente quiere recuperar archivos perdidos → derivar a Recup N1 130€ ANTES de formatear.

⚠️ **POR QUÉ ESTE SERVICIO REQUIERE FIRMA EXPRESA DEL CLIENTE:**
Una vez formateado, los datos NO se recuperan en cliente normal. Si el cliente luego dice "es que tenía X foto" → problemón. La firma expresa cubre legalmente que el cliente ASUMÍA pérdida total de datos.

---

## Antes (preparación)

### Confirmar por WhatsApp con MUCHA claridad
- [ ] **3 veces escrito**: _"Confirmo que voy a formatear sin guardar NADA. Pierdes todos los archivos, fotos, documentos, correos guardados en este PC, programas instalados, contraseñas guardadas en navegador. ¿OK?"_
- [ ] Pedir respuesta **literal "sí, OK formateo seco, asumo pérdida de datos"** por escrito.
- [ ] Si duda → **DESVIAR a Formateo+Backup 80€**. Por 10€ más le salvas todo, vale la pena.

### Material en mochila / taller
- [ ] **USB Arsenal MASTER** con `MEDICOPC.exe` y scripts.
- [ ] **USB Ventoy rojo** con ISOs Windows 10 22H2 y Windows 11 25H2.
- [ ] **USB rufus + Media Creation Tool** por si el USB Ventoy falla.
- [ ] **Ethernet** (cable RJ45 + adaptador USB-Ethernet si portátil sin puerto).
- [ ] **Resguardo papel CON CLÁUSULA expresa de formateo seco**.

### Resguardo papel — texto cláusula formateo seco

```
FORMATEO SECO — CLÁUSULA OBLIGATORIA

Yo, [nombre cliente], con DNI [...], confirmo que he sido informado de
que el formateo seco implica la pérdida TOTAL e IRRECUPERABLE de:
- Documentos, fotos, vídeos, música almacenados en el equipo
- Programas instalados (Office, navegadores con marcadores, drivers)
- Cuentas guardadas en navegadores y aplicaciones
- Configuración del sistema operativo

He decidido proceder bajo mi total responsabilidad, asumiendo la
pérdida y renunciando a cualquier reclamación posterior por datos
borrados.

Equipo: [marca/modelo, nº serie]
Fecha: __/__/____
Firma cliente:
```

---

## Al llegar

- [ ] Saludar, foto del equipo cerrado.
- [ ] **Repasar verbalmente la cláusula con el cliente** delante de él.
- [ ] **Firma del cliente en el resguardo** ANTES de empezar.
- [ ] Comprobar que el cliente no se está olvidando algo: "¿estás seguro de que no quieres salvar fotos de los hijos / facturas / Office activado?". Si responde "no quiero salvar nada" → seguir. Si duda → STOP, ofrecer Formateo+Backup 80€.
- [ ] Llevar a taller (modalidad por defecto) o quedarse a hacer en domicilio si pagó +25€.

---

## Durante — Software paso a paso

### Paso 1 — Recopilar info del PC ANTES de formatear

1. Anotar:
   - **Versión de Windows** instalada (10 vs 11, edición Home/Pro).
   - **Tipo de licencia**: ¿OEM (en BIOS, vinculada a placa) o cuenta Microsoft?
   - **Modelo del equipo** y arquitectura (32 o 64 bits).
   - **TPM 2.0** disponible: Win + R → `tpm.msc` → ver versión.

2. **Comprobar clave OEM en BIOS**:
   - PowerShell admin: `Get-CimInstance SoftwareLicensingService -Property OA3xOriginalProductKey | Select-Object -ExpandProperty OA3xOriginalProductKey`
   - Si devuelve clave → la usaremos al reactivar tras formateo.
   - Si devuelve vacío → es licencia digital vinculada a cuenta Microsoft. Apuntar email del cliente para reactivar.

3. **Decidir versión a instalar**:
   - PC <5 años con TPM 2.0 → Windows 11.
   - PC sin TPM 2.0 → Windows 10 (con ESU si cliente quiere).
   - PC tipo "ofimática senior" → cliente puede preferir seguir con Win 10 por costumbre.

### Paso 2 — Crear USB instalador (si no se usa Ventoy)

Si el USB Ventoy no funciona en este equipo:
1. Insertar USB vacío 8GB+.
2. Ejecutar **Rufus** (USB Arsenal Tools).
3. Seleccionar ISO de Windows.
4. Esquema partición: **GPT** (UEFI moderno) o **MBR** (BIOS legacy si aplicable).
5. Sistema archivos: **NTFS**.
6. Click Empezar. Espera 5-15 min.

### Paso 3 — Boot desde USB

1. Apagar PC.
2. Enchufar USB Ventoy o el rufus.
3. Encender + tecla boot menu (F12 / F11 / Esc según marca).
4. Seleccionar USB.
5. Si es Ventoy → escoger ISO (Win 10 22H2 / Win 11 25H2).
6. Carga el instalador Windows.

### Paso 4 — Instalar Windows desde cero

1. Idioma: **Español (España)** + teclado español + zona horaria Madrid.
2. Click **"Instalar ahora"**.
3. Activación → **"No tengo clave"** (la metemos después si toca, no aquí).
4. Edición: la que confirmaste antes (Home / Pro).
5. Aceptar términos.
6. Tipo instalación → **"Personalizada: solo instalar Windows"**.
7. Lista de particiones del disco:
   - **Eliminar TODAS las particiones** (Recovery, EFI, datos, todo).
   - Quedará un único "espacio sin asignar".
   - Click "Siguiente" sobre el espacio sin asignar → Windows crea las particiones nuevas que necesite.
8. Empieza la instalación. **Tarda 15-30 min**.

### Paso 5 — Configuración inicial OOBE

#### Para Windows 11
1. Selector región → España.
2. Distribución teclado → Spanish.
3. Conectar a red → **Ethernet** (si tienes cable) o WiFi.
4. ⚠️ **IMPORTANTE**: Win 11 Home obliga cuenta Microsoft. Para **saltar** y crear cuenta local:
   - **Truco oobe\\bypassnro**: en la pantalla "Conectémosle a una red" → Shift + F10 → consola → escribir `oobe\bypassnro` → Enter.
   - PC reinicia. Vuelve a empezar OOBE pero ahora aparece la opción **"No tengo internet"**.
   - Click "No tengo internet" → "Continuar con configuración limitada" → cuenta local.
5. Nombre usuario local: el que el cliente diga, normalmente su nombre.
6. Contraseña: dejar VACÍA al principio (cliente la pondrá si quiere).
7. Preguntas de seguridad: rellenar las 3 (cliente al lado eligiendo).
8. Privacidad: **DESACTIVAR todo**:
   - Ubicación → No.
   - Encontrar dispositivo → No.
   - Datos diagnóstico → Solo necesarios.
   - Experiencias personalizadas → No.
   - Inking & typing → No.
   - Anuncios identidad → No.
9. Esperar configuración inicial. 5-10 min.

#### Para Windows 10
1. Mismo flujo pero más simple.
2. Cuenta local pulsando "Configurar para uso personal" → "Cuenta sin conexión" → "Experiencia limitada".

### Paso 6 — Activar Windows

1. Una vez en escritorio limpio:
2. Configuración → Sistema → **Activación**.
3. Si era OEM con clave en BIOS → debería activarse automáticamente al detectar la BIOS. Si no → introducir clave manualmente: "Cambiar clave de producto" → pegar clave OA3x.
4. Si era licencia digital cuenta Microsoft → iniciar sesión con la cuenta del cliente, Windows reconoce y activa.

### Paso 7 — Windows Update

1. Configuración → Windows Update → Buscar actualizaciones.
2. Instalar TODAS (puede tardar 30-60 min con varios reinicios).
3. Esperar a que diga "está actualizado".

### Paso 8 — Drivers

1. Ir a la web del fabricante del PC (HP / Lenovo / Acer / Asus / MSI / Dell):
   - Buscar "Soporte" + modelo exacto.
   - Descargar drivers más recientes para esa versión Windows.
2. **Mínimo a instalar**:
   - Chipset (placa base).
   - GPU (Intel / NVIDIA / AMD).
   - WiFi y Bluetooth.
   - Audio (Realtek normalmente).
   - Trackpad si portátil.
3. Reiniciar tras cada bloque importante.

### Paso 9 — Software base sin instalar

⚠️ En Formateo Seco **NO se instala software al cliente** (no es Pack ni Migración). Se entrega Windows limpio activado con drivers. Si quiere navegador, Office, etc. → "te lo configuro yo, son 30€ extra Asistencia remota" o cliente lo hace.

**Excepción**: instalar **Chrome o Edge limpio** (el que use) con su cuenta sincronizada, para que recupere marcadores y contraseñas Google/Microsoft. Esto es 5 min, vale la pena para experiencia cliente.

### Paso 10 — Comprobar funcionamiento

1. Abrir Configuración → Sistema → Acerca de: ver Windows activado, edición correcta.
2. Administrador dispositivos: ningún signo amarillo.
3. Test rápido: Internet (abrir web), audio (vídeo YouTube), webcam (Cámara nativa), trackpad/teclas.
4. Reiniciar 1 vez para confirmar arranque limpio.

---

## Al cerrar

- [ ] Devolver PC al cliente (o entregar en su casa si vino a recoger).
- [ ] Mostrar el sistema arrancando rápido y limpio.
- [ ] Recordarle: "el PC está como recién comprado. Si quieres Office, drivers especiales, programas concretos, dímelo y te paso presupuesto. Hoy no incluye software extra."
- [ ] Cobrar **70€** Bizum o efectivo.
- [ ] Lanzar `entrega.bat` → factura `MPC-2026-XXXX`.
- [ ] **GUARDAR el resguardo firmado** archivado por si hay reclamación futura.
- [ ] Frase cierre: **"Garantía 30 días en mano de obra. Si Windows da problemas por algo de la instalación, vuelvo gratis. Si quieres añadir programas, son 30€ remota o 80€ pack Win 11 OEM completo."**

---

## Errores frecuentes

_Pendiente actualizar tras 5 visitas reales._

Anticipados:
- **Cliente cambia de opinión a mitad del proceso**: "espera, ¿puedes salvarme las fotos?". STOP, abortar formateo si todavía hay disco vivo. Si ya empezó la partición → datos perdidos, recordar resguardo firmado.
- **Driver WiFi no se instala automático**: portátiles modernos a veces requieren driver del fabricante manual antes de coger Internet. Tener un USB con drivers WiFi pre-descargados de la web del fabricante (preparar antes de salir).
- **TPM 2.0 deshabilitado en BIOS pero el chip existe**: entrar BIOS → Security → activar Intel PTT / AMD fTPM / Discrete TPM. Reiniciar. Win 11 lo reconoce.
- **Windows 11 instalación en PC sin TPM 2.0** (cliente insiste): se puede saltar comprobación con `regedit` durante OOBE Shift+F10 → `regedit` → `HKLM\SYSTEM\Setup\LabConfig` → crear DWORDs `BypassTPMCheck=1`, `BypassSecureBootCheck=1`, `BypassRAMCheck=1`. Pero **Microsoft no lo soporta y puede no recibir actualizaciones futuras**. Avisar al cliente y, si insiste, dejar registrado por escrito.
- **Activación falla post-formateo**: si Windows no se activa con la clave OEM → Configuración → Activación → "Solucionar problemas" → "He cambiado el hardware recientemente" → iniciar sesión con cuenta MS asociada al equipo. Si no hay cuenta MS → contactar Microsoft soporte (es asunto del cliente, no nuestro).
- **Cliente no tiene la clave OEM** y no aparece en BIOS y no tiene cuenta MS asociada → Windows queda sin activar. Cliente debe comprar licencia (~30€ Win 11 OEM en PcComponentes). Avisar antes de empezar.

---

## Tiempo total

- Equipo con SSD y conexión Ethernet rápida: **2h**.
- Equipo con HDD viejo o WiFi lento (Updates tardan): **3h**.

---

## Reglas críticas

🔴 **CLÁUSULA FIRMADA OBLIGATORIA**. Sin firma, NO se hace formateo seco. Sin firma + cliente reclama datos = problema legal.
🔴 **NUNCA borrar las particiones sin haber confirmado verbalmente Y por escrito que el cliente entiende que pierde todo**.
🔴 **NO instalar Office crackeado / KMS / Office gratis** al cliente. Bajo ninguna circunstancia. Sale carísimo si Microsoft detecta y reclama. Cliente paga su Office o pone alternativas (LibreOffice, Office Online gratis).
🔴 **Activación OEM siempre primero** (BIOS); cuenta Microsoft segundo; clave digital tercero. NO meter claves piratas.
🔴 **NO restaurar nada del PC viejo** en formateo seco. Si cliente lo quiere, ese es **Formateo+Backup 80€**, vamos a desviarlo allí.
🔴 **Drivers SIEMPRE web fabricante**, nunca "Driver Booster" ni "DriverPack Solution" (instalan adware).
🔴 **Si tras Windows Update el sistema da BSOD recurrente** → posible incompatibilidad driver. Probar drivers más viejos del fabricante. Si persiste, considerar Windows 10 en vez de 11.
🔴 **Guardar resguardo firmado físico** archivado mínimo 1 año por si hay reclamación.
