# Asistencia remota (30€ mín 30 min · 45€/h adicional)

> Tiempo realista: **30 min - 2h** por sesión
> Bloque tarifa: **E — Extras**
> Modalidad: remota (sin desplazamiento)

---

## Qué es y qué NO es

**SÍ es:** intervención en el PC del cliente vía AnyDesk (o TeamViewer alternativo). Para problemas software simples y rápidos donde no hace falta visita física.

**NO es:**
- ❌ **Hardware** (cambios componentes, limpieza interior). Imposible remoto.
- ❌ **PC que no arranca**. Necesita visita o recogida.
- ❌ **Recuperación datos**. Puede empeorar el daño desde remoto.
- ❌ **Soporte continuo** (mantenimiento mensual): aparcado para Pyme/MSP julio 2026+.

**Casos típicos:**
- Cliente no sabe configurar OneDrive / cuenta correo / impresora wifi.
- Programa específico no abre (resolver instalando dependencias).
- Error de Windows (DNS roto, certificado web caducado, registro corrupto leve).
- Configuración Outlook / Thunderbird / firma email.
- Dudas software ofimático puntuales.
- Quitar bloatware fácil (3-4 programas mal desinstalados).

---

## Antes (preparación material)

### Confirmar por WhatsApp / llamada
- [ ] **Síntomas exactos** y captura de pantalla del error si hay.
- [ ] **Cliente puede arrancar el PC y conectar al wifi** — sin esto, no hay remota posible.
- [ ] **Cliente acepta tarifa**: 30€ los primeros 30 min · 45€/h en bloques de 30 min adicionales.
- [ ] **Cliente tiene AnyDesk instalado** (web `anydesk.com`, descargar versión gratis particular).
  - Si no lo tiene → guiar telefónicamente para descargar (5-10 min, no se cobra ese tiempo).

### Material en taller
- [ ] **PC propio operativo** con AnyDesk abierto.
- [ ] **Conexión estable** (cable Ethernet preferible al wifi).
- [ ] **Auriculares con micro** para llamada paralela mientras se trabaja.
- [ ] **Notas** o ChatGPT/Claude abierto por si surge consulta técnica rápida.
- [ ] **Cronómetro** móvil (cobrar por tiempo real).

---

## Al iniciar sesión (online)

### Paso 1 — Conectar
1. Cliente arranca AnyDesk en su PC y dicta el **AnyDesk-ID** (9 dígitos).
2. Yo introduzco ese ID en mi AnyDesk → "Conectar".
3. En el PC del cliente aparece **ventana solicitud conexión** con mi nombre + miniatura mi cara.
4. Cliente pulsa **"Aceptar"**.
5. Conectado. Pantalla del cliente visible en mi monitor.

### Paso 2 — Iniciar cronómetro y avisar
- [ ] **Inicio cronómetro** móvil cuando empiezo a trabajar realmente (no durante el "ya estoy conectándote, espera").
- [ ] **Mensaje inicial al cliente** vía chat AnyDesk o llamada: "Buenos días, [nombre]. Soy Guillermo de MedicoPC. Empezamos. ¿Confirmamos que el problema es X?"

### Paso 3 — Pedir control total (si hace falta)
- [ ] Por defecto AnyDesk da control completo, pero confirmar.
- [ ] Si necesitas permisos elevados (UAC) → cliente verá la ventana UAC y debe hacer clic "Sí" desde su lado (no se controla remoto sin Plus, normalmente).

---

## Durante — Ejecución del trabajo

### Reglas de comportamiento durante remota

- **Hablar con el cliente** mientras trabajo. Decirle qué estoy haciendo (1 frase corta cada 30 segundos).
- **Si el cliente está delante**: que vea lo que hago, le tranquiliza.
- **Si el cliente se va a hacer otra cosa**: avisar de cuánto va a tardar y comprometerse a llamarle al terminar.
- **NO abrir archivos personales** (Documentos, Fotos, navegador). NUNCA. Excepto si el problema lo requiere y el cliente lo autoriza explícitamente.
- **NO instalar nada** sin avisar previamente al cliente.

### Casos típicos paso a paso

#### Caso A — Configurar Outlook nueva cuenta
1. Outlook → Archivo → Agregar cuenta.
2. Tipo: IMAP (recomendado) o Exchange (si es Office365 empresa).
3. Datos servidor (preguntar al cliente o consultar web proveedor).
4. Sincronizar y verificar correo entra.

#### Caso B — Resolver impresora WiFi
1. Configuración → Bluetooth y dispositivos → Impresoras y escáneres.
2. **Quitar dispositivo** la impresora actual.
3. **Agregar dispositivo** → Buscar impresora wifi.
4. Si no aparece → ir a la web del fabricante (HP / Canon / Epson), descargar driver, instalar.
5. Imprimir página de prueba.

#### Caso C — Quitar adware del navegador
1. Edge / Chrome → menú ⋮ → Configuración → Restablecer configuración.
2. Si persiste → AdwCleaner desde el USB del cliente (si lo tiene) o descargar versión web.
3. Reiniciar.

#### Caso D — Liberar espacio disco
1. Limpieza disco (`cleanmgr`) admin.
2. Storage Sense activado.
3. Desinstalar programas no usados (Aplicaciones).

---

## Al cerrar (online)

### Paso 1 — Verificar el problema resuelto
- [ ] Demo al cliente: el síntoma original ya no se presenta.
- [ ] Si NO está resuelto del todo → opciones:
  - Continuar (cobrar tiempo adicional, avisar antes).
  - Visitar / recoger (si requiere hardware).

### Paso 2 — Cierre cronómetro
- [ ] Tiempo total trabajado.
- [ ] Cálculo: 30€ los primeros 30 min, +22.5€ por cada 30 min siguientes (= 45€/h).

### Paso 3 — Desconexión limpia
- [ ] **Cerrar AnyDesk** desde mi lado.
- [ ] Cliente puede cerrar AnyDesk también.
- [ ] **NO dejar AnyDesk en arranque automático** del cliente. Si lo dejaste para hacer algo, asegurarse de que no se queda activo siempre (riesgo seguridad).

### Paso 4 — Cobro
- [ ] Bizum o transferencia (no efectivo en remota).
- [ ] Enviar **factura por email** (a MO julio: con Pixel 8a y `entrega.bat` adaptado para remoto).
- [ ] Hook cierre: *"Cualquier duda en próximos 30 días sobre lo trabajado hoy, llamada gratis."*

---

## Errores frecuentes

_Pendiente actualizar tras 5 visitas reales._

Casos anticipados:
- **Cliente espera resolver problema gordo en 30 min**: si va a tardar más, AVISAR al cliente al pasar 25 min: "esto va para 1h, ¿continuamos?" antes de seguir.
- **Cliente desconecta a mitad** sin avisar: cobrar el tiempo trabajado igual. Cláusula "tarifa por tiempo iniciado".
- **Conexión inestable**: si AnyDesk se cae 3 veces y no avanzo → derivar a visita presencial. No cobrar la remota fallida (consideración cliente).
- **PC del cliente con virus serio** que reaparece tras limpieza: avisar que el camino correcto es Formateo+Backup 80€ con visita.
- **Cliente pide guardarle contraseñas** en el navegador: hacerlo SI él lo dicta. NO consultar contraseñas almacenadas existentes.

---

## Tiempo total

- **30 min** problema simple bien identificado.
- **45-60 min** problema medio (configuración Outlook + impresora).
- **1.5-2h** problema complejo (mejor evaluar visita).

---

## Reglas críticas

🔴 **NO abrir archivos personales** (Documentos, Fotos, navegador, correo) salvo que el problema lo requiera Y el cliente lo autorice explícitamente.
🔴 **NO instalar software adicional** sin avisar previamente.
🔴 **AVISAR cuando el tiempo se va a salir de los 30 min iniciales.** Confirmación cliente antes de seguir.
🔴 **Cliente con virus serio o hardware fallando** → recomendar visita presencial. Remota no cubre eso.
🔴 **NO dejar AnyDesk en arranque automático** del cliente. Cerrar al terminar.
🔴 **Cobro Bizum / transferencia.** No efectivo en remota.
🔴 **Si la conexión es muy inestable** y no avanzo → no cobrar la remota fallida, derivar a visita.
🔴 **Hablar al cliente** mientras trabajo. Silencios largos asustan al cliente que ve el cursor moverse solo.
