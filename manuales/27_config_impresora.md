# Configuración impresora / escáner (30€ puntual · >1h pasa a 45€/h)

> Tiempo realista: **45-60 min** (servicio NUEVO en v3.2)
> Bloque tarifa: **E — Extras**
> Modalidad: domicilio (donde está la impresora)

---

## Qué es y qué NO es

**SÍ es:** instalar impresora wifi/USB, conectarla a uno o varios PCs, configurar app móvil, hacer página de prueba, escaneo a PDF, configurar bandeja papel, alinear cabezales si toca, asesoría para comprar tinta/tóner.

**NO es:**
- ❌ **Reparación de impresora rota** (atascos persistentes, error firmware, hardware): derivar al SAT del fabricante.
- ❌ **Compra de impresora** (eso es Asesoría → consejo, sin coste).
- ❌ **Configuración a domicilio Plus** (más de 1h, varios usuarios) → pasa automáticamente a 45€/h estándar.

**Casos típicos:**
- Cliente acaba de comprar impresora HP / Canon / Epson y no sabe configurarla.
- Cliente cambió router y la impresora dejó de funcionar en wifi.
- Cliente tiene varios PCs en casa y quiere que todos impriman.
- Cliente con escáner y quiere "escanear a PDF y enviarlo por correo".

---

## Antes (preparación)

### Confirmar por WhatsApp
- [ ] **Marca y modelo** impresora exacto.
- [ ] **Tipo conexión deseada**: wifi / USB cable / red Ethernet.
- [ ] **¿Cuántos PCs** debe acceder?
- [ ] **¿App móvil** (HP Smart, Canon Print, Epson iPrint) → preguntar si quieren imprimir desde móvil/tablet.
- [ ] **¿Escáner** sí/no? Si sí, ¿formato preferido (PDF, JPG)?

### Material en mochila
- [ ] **Hoja A4 blanco** para test impresión.
- [ ] **Cable USB tipo B** (impresoras estándar) por si hace falta y cliente no lo tiene.
- [ ] **USB Arsenal MASTER** sin drivers preinstalados (los descargo siempre frescos web fabricante).
- [ ] **Móvil** con app del fabricante a mano para mostrar al cliente.

---

## Al llegar

- [ ] Foto exterior impresora estado actual.
- [ ] Confirmar **wifi de casa funcional** (sin esto, configuración wifi imposible).
- [ ] **Modelo confirmado** vs etiqueta trasera.
- [ ] Cronómetro empieza al iniciar trabajo.

---

## Durante — Configuración paso a paso

### Paso 1 — Encender e iniciar impresora

1. Conectar impresora a corriente.
2. Encender.
3. **Setup inicial** si es la primera vez:
   - Idioma: Español.
   - Fecha y hora.
   - País.
   - Cargar papel y cartuchos.

### Paso 2 — Conectar a wifi

**Caso A — HP / Canon / Epson modernas con app:**
1. Descargar **app del fabricante** en el móvil del cliente (preguntar antes):
   - HP → **HP Smart**.
   - Canon → **Canon PRINT**.
   - Epson → **Epson iPrint** o **Epson Smart Panel**.
2. App detecta impresora.
3. App pide **wifi del cliente + contraseña**.
4. Conexión automática.
5. Imprimir página de prueba desde app.

**Caso B — Sin app (modelos viejos):**
1. En la impresora: menú → Configuración → Red → Wifi.
2. Asistente wifi → seleccionar SSID del cliente → introducir contraseña.
3. Imprimir hoja de configuración (estado de red) para confirmar IP.

**Caso C — USB cable:**
1. Conectar cable USB al PC del cliente.
2. Windows detecta automáticamente, descarga driver Windows Update.
3. Si no lo detecta → web fabricante → descargar driver específico → instalar.

### Paso 3 — Instalar driver en cada PC

**Windows 11/10:**
1. Configuración → Bluetooth y dispositivos → Impresoras y escáneres.
2. **Agregar dispositivo**.
3. Espera escaneo de red.
4. Aparece la impresora → **Agregar**.
5. Si NO aparece (impresora antigua o red rara) → **"La impresora no está en la lista"** → opciones manuales:
   - **Buscar por nombre o IP TCP/IP** (mirar IP en hoja de configuración impresa antes).

**Si Windows no descarga driver automático:**
1. Web del fabricante → modelo exacto → descargas.
2. Descargar driver Windows 64-bit.
3. Instalar.
4. Reiniciar si lo pide.

### Paso 4 — Imprimir página de prueba en cada PC

1. Configuración → Impresoras → seleccionar la impresora → **Administrar**.
2. **Imprimir página de prueba**.
3. Verificar que sale OK.
4. Si NO imprime → revisar:
   - Estado impresora online.
   - Cola de impresión vacía.
   - Driver actualizado.

### Paso 5 — Configurar escáner (si aplica)

1. Si la impresora tiene escáner integrado (multifunción):
   - **Windows Fax y Escáner** (built-in Win 10/11) → **Nuevo escaneo** → seleccionar dispositivo → tipo (foto / documento) → escanear.
   - **App fabricante** (HP Smart, Canon PRINT) → opción Escanear → guardar como PDF.
2. Configurar **carpeta destino** habitual (`Documentos\Escaneos\`).
3. Configurar **formato preferido** del cliente (PDF normal).
4. Demo: escanear hoja prueba → guardar → abrir PDF resultado.

### Paso 6 — Configurar app móvil (si cliente quiere)

1. App fabricante en móvil del cliente.
2. Login con cuenta cliente (si pide) o sin cuenta.
3. **Imprimir desde móvil**:
   - Foto de la galería → compartir → imprimir → seleccionar impresora.
4. **Escanear desde móvil**:
   - App → escanear desde el escáner físico → guardar PDF en móvil.

### Paso 7 — Configurar tóner / tinta low (alertas)

1. Configurar **email de notificación** o **app móvil** que avise cuando tinta/tóner está bajo.
2. Asesorar al cliente sobre dónde comprar tinta/tóner:
   - **Originales fabricante** (HP/Canon/Epson) → caros pero garantía.
   - **Compatibles de calidad** (TonerYa, Tintaria, RecordIt) → 30-50% más baratos, calidad decente.
   - **Genéricos AliExpress** → no recomendado, riesgo manchar cabezales.

---

## Al cerrar

- [ ] **Demo final delante cliente**: imprimir desde PC + imprimir desde móvil (si aplica) + escanear (si aplica).
- [ ] **Hoja resumen escrita** entregada al cliente con:
  - SSID wifi al que está conectada la impresora.
  - IP fija o reservada (si aplica).
  - Modelo + nº serie.
  - Web fabricante para drivers futuros.
  - Marca tinta/tóner recomendada.
- [ ] Cobrar **30€** Bizum/efectivo.
- [ ] `entrega.bat` → factura.
- [ ] Hook cierre: *"Garantía 30 días. Si en 30 días deja de imprimir por algo de la configuración, vuelvo gratis. Si cambias de router o de wifi, hay que reconfigurar y eso ya es un nuevo servicio."*

### Si supera 1h

- Avisar al cliente al pasar 50 min: "Esto va a llevar más de la hora prevista. Pasa a tarifa estándar 45€/h. ¿Sigo o paro aquí?".
- Si sigue → cobrar 30€ + (45€ x cada 30 min adicional) en bloques.
- Ej: 1h 30min total → 30€ (1ª h) + 22.5€ (30 min extra) = **52.5€**.

---

## Errores frecuentes

_Pendiente actualizar tras 5 visitas reales._

Casos anticipados:
- **Wifi del cliente con caracteres raros** en SSID o pass: a veces apps fabricante se atragantan. Truco: cambiar SSID a algo simple → configurar → restaurar SSID.
- **Impresora se queda en "offline" recurrente**: probable IP dinámica que cambia. Solución: reservar IP fija en router (si cliente sabe entrar) o configurar en la impresora IP estática manualmente.
- **Cliente con varios SSIDs (wifi 2.4G + 5G)**: muchas impresoras solo soportan 2.4G. Conectar a la red 2.4G específicamente.
- **App fabricante no detecta impresora**: cierto firmware viejo no es compatible con app reciente. Actualizar firmware impresora primero (web fabricante o desde la propia impresora).
- **Escaneo guarda en formato raro** (TIFF, JP2): cambiar configuración por defecto a PDF en app fabricante.

---

## Tiempo total

- **45-60 min** caso normal (1 impresora + 1 PC + app móvil).
- **60-90 min** si son 3+ PCs o configuración avanzada (escáner red, perfiles).

---

## Reglas críticas

🔴 **AVISAR al cliente cuando se pasa 1h** y servicio pasa a tarifa estándar 45€/h.
🔴 **Hoja resumen escrita** obligatoria para que el cliente recuerde la configuración.
🔴 **NO instalar suite completa fabricante** con antivirus, recordatorios pop-up, etc. Solo driver + app móvil. El bloatware de HP/Canon/Epson es brutal.
🔴 **NO comprar tinta/tóner** por el cliente. Solo asesorar dónde y qué comprar.
🔴 **Configuración wifi solo si cliente conoce su contraseña wifi**. Si dice "no me sé la del router" → orientarle a buscarla (etiqueta del router) o derivar a otro día.
🔴 **Cliente espera que la impresora "imprima sola desde el móvil"**: depende de modelo. Avisar antes de presupuestar si su impresora vieja NO tiene wifi → proponer cable USB + PC compartida en red.
🔴 **NO dejar cuenta de cliente vinculada a app fabricante** (HP Instant Ink etc.) sin que él lo solicite. Privacidad.
