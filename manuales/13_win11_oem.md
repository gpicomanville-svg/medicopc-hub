# Instalación Windows 11 OEM (80€)

> Tiempo realista: **2-3h** + desplazamiento
> Bloque tarifa: **B — Mantenimiento Software**
> Modalidad: taller por defecto · domicilio +25€

---

## Qué es y qué NO es

**SÍ es:** instalación limpia de **Windows 11** sobre un PC **nuevo / sin sistema** o sobre un PC al que se le quiere instalar Win 11 desde cero. Incluye **licencia OEM activada** (clave que trae la BIOS o cliente trae clave Keys4US/oficial).

**NO es:**
- ❌ **Formateo seco 70€**: ese es para PC con Windows ya instalado que se quiere "limpiar". Win 11 OEM es para "PC sin sistema" o "quiero pasar a Win 11 desde Win 10".
- ❌ **Win 10 OEM 80€**: equipos sin TPM 2.0 que no soportan Win 11.
- ❌ **Migración 100€**: incluye Win nuevo + paso de archivos del PC viejo. Si el cliente quiere todos sus datos del PC anterior → vender Migración.

**Cliente típico:**
- PC montado a piezas que llega sin sistema operativo.
- PC nuevo de tienda con FreeDOS o Linux (cliente quiere Windows).
- Cliente con Windows 10 que quiere actualizar a Win 11 limpio (no upgrade en sitio).

---

## Antes (preparación material)

### Confirmar por WhatsApp
- [ ] **PC tiene TPM 2.0 + Secure Boot + UEFI?**
  - TPM 2.0 lo lleva todo PC desde 2019. Anteriores → puede o no.
  - Si NO tiene TPM 2.0 → vender **Win 10 OEM 80€** en su lugar (mientras quede soporte ESU).
- [ ] **¿Tiene clave Windows o se compra por Keys4US?**
  - Cliente trae clave OEM oficial → uso esa.
  - Cliente sin clave → recomendar comprar OEM en Keys4US (~12-15€) y le pasamos el coste o lo metemos en presupuesto.
  - PCs OEM nuevos (Lenovo, HP, Dell prebuild) ya traen clave en BIOS → automático.
- [ ] **Idioma preferido** (España / Hispanoamérica) y **edición** (Home / Pro).

### Material en mochila
- [ ] **USB Ventoy rojo** con `W11_25H2_ES.iso`.
- [ ] **USB MASTER** con Tools + pack winget esencial.
- [ ] **Cable Ethernet** corto.
- [ ] **Pendrive personal** para guardar clave OEM si la extraigo antes (caso PC con Win previo).

---

## Al llegar / al recibir equipo

### Paso 1 — Verificar requisitos Win 11

- [ ] **TPM 2.0 activo**: encender PC, entrar BIOS (Del / F2), buscar **Security → TPM** o **Trusted Platform Module**. Debe estar **Enabled**. Si está disabled → activar. Si no aparece la opción → no tiene TPM 2.0, **vender Win 10 OEM**.
- [ ] **Secure Boot enabled**: BIOS → Boot → Secure Boot. Activar si no está.
- [ ] **UEFI mode** (no Legacy): BIOS → Boot → UEFI/Legacy → UEFI. Si está en Legacy → cambiar.
- [ ] **CPU compatible Win 11**: Intel 8ª gen+ o Ryzen 2000+ son las oficialmente soportadas. Anteriores requieren bypass (Rufus o `LabConfig` en registro durante OOBE).
- [ ] **RAM ≥4GB** y **Almacenamiento ≥64GB** (estándar mínimo Microsoft).

### Paso 2 — Si es PC con Windows previo (caso "pasar de W10 a W11 limpio")
- Extraer clave OEM como en el manual de Formateo seco (`wmic` o PowerShell `OA3xOriginalProductKey`).
- Guardarla en pendrive personal por si acaso.

---

## Durante — Instalación

### Paso 1 — Arrancar instalador Win 11

1. USB Ventoy rojo enchufado.
2. Boot menu → USB Ventoy → `W11_25H2_ES.iso` → Boot in normal mode.
3. Selecciona idioma Español España, formato España, teclado Español. Siguiente.
4. Click **Instalar ahora**.
5. **Activación**: si tienes clave OEM extraída o cliente tiene clave física → meterla. Si PC OEM con clave en BIOS → automático. Si no hay clave → "No tengo clave de producto" (se activará después).
6. **Edición**: la que corresponda (Home / Pro). Si la clave OEM ya viene → marca automática.
7. EULA → aceptar.
8. **Personalizada** (instalación limpia).

### Paso 2 — Particionado

#### PC nuevo (disco vacío)
- Solo aparece "Espacio sin asignar". Seleccionarlo → Siguiente. Windows crea las 4 particiones automáticamente.

#### PC con Windows previo
- Ver lista de particiones del disco principal.
- **Borrar TODAS** del disco principal (EFI, MSR, Windows, Recovery).
- Quedará espacio sin asignar → Siguiente.
- ⚠️ **NO TOCAR segundos discos** (HDD/SSD de datos). Solo disco principal.

### Paso 3 — Esperar instalación

- 15-30 min. PC reinicia 1-2 veces solo.
- Cuando aparezca pantalla "Selecciona tu país" → fase OOBE.

### Paso 4 — OOBE

1. **País**: España.
2. **Teclado**: Español.
3. **Conectar a red**:
   - Win 11 Home y Pro **requieren cuenta MS + internet** por defecto.
   - **Truco cuenta local**: en pantalla "Conectar a red" → **Shift + F10** → consola → `OOBE\BYPASSNRO` → Enter → reinicia OOBE → ahora aparece opción "No tengo internet" + "Continuar con cuenta local".
   - O alternativa actualizada (W11 25H2): **Shift + F10** → `start ms-cxh:localonly` → asistente cuenta local directo.
   - Si el cliente quiere cuenta MS (mayoría) → conectar WiFi normal y seguir el flujo.
4. **Cuenta**:
   - Cuenta MS del cliente (correo + contraseña → si pregunta cuál usar, recomiendo el que ya use con MS si tiene Office o Xbox).
   - Cuenta local con bypass.
5. **PIN**: poner temporal 1234 si el cliente no está delante, luego cambiar.
6. **Privacidad**: desactivar TODO (telemetría, ubicación, anuncios, voz, escritura, datos diagnóstico opcional). Cliente activa lo que quiera después.
7. **OneDrive**: si pregunta de subir Documentos/Imágenes/Escritorio → **NO** (cliente puede activar después si quiere).
8. **Game Pass / Office trial**: declinar.

### Paso 5 — Configuración post-instalación

#### Activación
1. Win + I → Sistema → Activación.
2. Comprobar:
   - Si la clave OEM estaba en BIOS → **activado automáticamente** ✅.
   - Si metiste clave durante instalación → activado.
   - Si pendiente → meter clave ahora desde aquí.
3. Si dice "Windows está activado" o "Windows está activado con licencia digital vinculada a cuenta MS" → OK.

#### Drivers
1. **Windows Update**: Win + I → Windows Update → Buscar. Esperar 15-30 min, instala drivers críticos.
2. Drivers específicos web fabricante:
   - **GPU**: NVIDIA / AMD / Intel.
   - **Chipset placa**: Asus / MSI / Gigabyte / ASRock.
   - **Audio Realtek** si suena mal.
   - **WiFi/Lan** si no detecta.
   - **Lenovo Vantage / HP Support Assistant** SOLO si es portátil de marca y necesita firmware updates específicos.

#### Software esencial pre-instalado
Pack winget esencial (Scripts\01_LIMPIEZA\paquetes_esenciales.bat):
- Chrome o Firefox (preguntar).
- VLC.
- 7-Zip.
- Adobe Acrobat Reader.
- Bitwarden si lo usa.

NO instalar de oficio:
- Office (cliente con su licencia).
- Antivirus pago.
- Software pirata.
- Programas no pedidos.

#### Personalización rápida
- Botón inicio: alineado a la izquierda (la mayoría lo prefiere).
- Mostrar extensiones de archivo y archivos ocultos en Explorador (preferencia técnica, opcional).
- Modo oscuro / claro según gusto del cliente.
- Fondo escritorio neutro.

---

## Al cerrar

- [ ] Demostrar:
  - Windows 11 activado.
  - Drivers OK (sin amarillo en Administrador de dispositivos).
  - Internet funciona.
  - Programas básicos instalados.
- [ ] **Recordar**: que reinstale lo que necesite (Office, Steam, sus programas).
- [ ] **Cambiar PIN** delante de él si lo dejé en 1234.
- [ ] Cobrar **80€** Bizum o efectivo.
- [ ] Si compré clave Keys4US para el cliente → coste pieza adicional según tarifa (no incluido en los 80€).
- [ ] Lanzar `entrega.bat` → factura `MPC-2026-XXXX`.
- [ ] Frase cierre: **"Garantía 30 días. Si la activación se cae o algún driver da problemas, vuelvo gratis."**

---

## Errores frecuentes

_Pendiente actualizar tras 5 visitas reales._

Anticipados:
- **TPM 2.0 desactivado en BIOS** pero la placa lo soporta → activar en BIOS, todo bien.
- **CPU pre-2018 que no aparece en lista soportada por Win 11**: si insistes con Rufus/bypass → instala pero Microsoft puede dejar de dar updates en el futuro. Avisar al cliente y que decida.
- **Cuenta MS del cliente con 2FA y no recuerda la app autenticador**: pesadilla. Mejor cuenta local de momento, vincular después con cliente delante.
- **Activación falla 24h después de instalar**: a veces los servidores de Microsoft tardan. Esperar 24-48h. Si después sigue sin entrar → contactar MS support.
- **Driver GPU no instala** porque hay un driver nativo Windows que se mete por delante: desinstalar el de Windows desde Administrador de dispositivos, reiniciar, instalar el correcto.
- **PC con SSD muy lleno** que se queda sin espacio durante instalación: Win 11 ocupa 30-40GB. SSDs de 64GB ya no caben holgados → presupuesto SSD nuevo.

---

## Tiempo total

- Instalación Win 11: **45-60 min**.
- Drivers + Windows Update: **30-45 min**.
- Software esencial: **10-15 min**.
- Configuración + entrega: **15-30 min**.
- **Total: 2-3h.**

---

## Reglas críticas

🔴 **Verificar TPM 2.0 / Secure Boot / UEFI** antes de empezar. Si falla → vender Win 10 OEM o presupuestar TPM si la placa admite.
🔴 **Extraer clave OEM** antes de formatear si había Windows previo.
🔴 **NO TOCAR segundo disco** sin confirmación expresa.
🔴 **NO instalar bloatware ni software pirata.**
🔴 **Privacidad OOBE en cero** por defecto. Cliente activa lo que quiera.
🔴 **Recordar al cliente que cambie el PIN 1234** que dejé.
🔴 **Si la activación digital tarda** → no es problema de instalación, esperar 24-48h.
🔴 **Foto del PC con Windows arrancado y activado** al final. Documentación.
🔴 **Si el cliente trae clave Keys4US oficial** → meterla en activación. Si la clave es revendida pirata → activa pero puede caer en updates futuros, NO recomendar yo claves grises.
