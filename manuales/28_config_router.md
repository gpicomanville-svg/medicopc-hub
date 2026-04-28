# Configuración router WiFi (25-35€)

> Tiempo realista: **30-60 min** + desplazamiento
> Bloque tarifa: **E — Servicios complementarios**
> Modalidad: domicilio (router está en su casa) o remota (si el cliente accede al panel admin desde su PC).

---

## Qué es y qué NO es

**SÍ es:** configuración del router del cliente para optimizar su WiFi en casa: cambiar SSID, contraseña, banda 2.4 / 5 GHz, canal, WPA3, red de invitados, DNS, control parental, reservar IPs por MAC, port forwarding básico, restablecer router de cero. **25€** simple (cambiar pass / SSID), **35€** completa (todo lo anterior + invitados + WPA3 + canal optimizado + DNS).

**NO es:**
- ❌ **Reparar router roto físicamente**: no se repara, se cambia. Cliente compra nuevo.
- ❌ **Instalación fibra óptica desde cero** (eso lo hace la operadora).
- ❌ **Cambio operadora ISP** (decisión del cliente, no servicio técnico).
- ❌ **Red empresarial** (varios switches, VLANs, AP profesionales) — eso es bloque H pyme Q3 2026, no aplica ahora.
- ❌ **Cambio router del operador**: si Movistar / Vodafone / O2 alquilan el router, el cliente no puede cambiarlo libremente. Sí se puede comprar uno propio (Asus / TP-Link / Mikrotik) y poner el del operador en modo bridge → 35€ completa.

**Cuándo aplica:**
- WiFi lento, intermitente, con zonas muertas en casa.
- Cliente cambia contraseña porque vecino "se cuela".
- Router nuevo recién instalado por operador, configuración por defecto mala.
- Cliente compra repetidor / mesh y quiere integración con router principal.
- Cliente reportes WiFi cae cada noche → suele ser canal saturado.

---

## Antes (preparación)

### Confirmar por WhatsApp
- [ ] **Marca y modelo router**: foto de la pegatina inferior. Habitualmente:
  - Movistar: Mitrastar / ZTE / Askey.
  - Vodafone: Sercomm / Huawei.
  - O2: ZTE / Mitrastar.
  - Cliente compró por su cuenta: Asus, TP-Link, Netgear, FRITZ!Box, Mikrotik.
- [ ] **¿Tiene el cliente acceso administrador?** Necesario user/password panel admin. Si no lo sabe → ver pegatina o buscar default.
- [ ] **Síntomas concretos**: ¿qué quiere mejorar exactamente?
- [ ] **Casa / piso**: m², número plantas, paredes gruesas. Para diagnóstico cobertura.

### Material en mochila
- [ ] **Móvil con WiFi Analyzer** (Android: WiFi Analyzer Open Source) para ver canales saturados.
- [ ] **Portátil propio** con WiFi para test conexión y velocidad.
- [ ] **Cable Ethernet RJ45** corto.
- [ ] **Linterna** (router suele estar en sitios oscuros).

---

## Al llegar

- [ ] Foto router en su sitio (estado original).
- [ ] Localizar **etiqueta inferior**: SSID por defecto, password por defecto, MAC, modelo.
- [ ] Conectar mi portátil al router por Ethernet (más estable que WiFi para configurar).
- [ ] Abrir navegador → IP router (típicamente `192.168.1.1` / `192.168.0.1` / `192.168.100.1`).
- [ ] Login con credenciales de pegatina (admin / admin, cliente teclea password si la cambió antes).

---

## Durante — Software paso a paso

### Paso 1 — Diagnóstico WiFi inicial (con WiFi Analyzer móvil)

1. Móvil con WiFi Analyzer abierto en sitio donde el cliente reporta problema.
2. Pestaña **Channels** (2.4 GHz):
   - Ver tu red.
   - Ver redes vecinas.
   - **Saturación canal**: si tu red está en canal 6 y hay otras 8 redes en canal 6 → mover a canal 1 o 11 (mejor disponible).
3. Pestaña **5 GHz**: igual pero en banda 5GHz (canales 36-165).
4. Pestaña **Signal Strength**: ¿llegan -65 dBm? Bien. ¿-80 dBm? Mal, repetidor o reubicación router.

### Paso 2 — Cambiar SSID y contraseña

#### Pasos genéricos (varía por marca)

1. Panel admin → **WiFi / Wireless / Inalámbrico**.
2. **SSID**: cambiar nombre red. Algo discreto (no "Familia Pérez 2A"). Ejemplo: nombre random (`MovistarPlus_2024`, `R7-ABC`).
3. **Contraseña WPA**: cambiar. Mínimo 12 caracteres, mezcla letras + números + símbolos. **Cliente la teclea** y la apunta en papel (o yo se la mando por WhatsApp si él la elige).
4. **Tipo seguridad**:
   - **WPA3** si router moderno la soporta (mejor opción).
   - **WPA2-PSK (AES)** si no soporta WPA3 (válido).
   - **NUNCA WEP** (rota desde 2003).
   - **NUNCA WPA1** ni TKIP.
5. Guardar y aplicar.

### Paso 3 — Configurar bandas 2.4 GHz y 5 GHz

1. **2.4 GHz**: alcance largo, atraviesa paredes, velocidad limitada. Ideal cosas IoT, móviles antiguos.
2. **5 GHz**: alcance corto, no atraviesa paredes bien, velocidad alta. Ideal portátiles cerca, smart TV.

#### Decisión single SSID vs SSID separado
- **Single SSID** (mismo nombre 2.4 + 5): cómodo, dispositivos eligen automáticamente. Recomendado por defecto.
- **SSID separado** (`MyWifi_2.4` / `MyWifi_5`): control fino, útil si dispositivos no eligen bien.

### Paso 4 — Optimizar canal

1. Según diagnóstico WiFi Analyzer:
2. **2.4 GHz**: usar canal 1, 6 o 11 (no overlapping).
3. **5 GHz**: cualquier canal libre (suele haber menos saturación).
4. **Ancho de canal**:
   - 2.4 GHz → 20 MHz (máx compatibilidad).
   - 5 GHz → 80 MHz (mejor velocidad) o 160 MHz si router gama alta.

### Paso 5 — Red de invitados (si cliente quiere)

1. Activar red separada **"Invitados"** o "Guest".
2. SSID distinto, password distinto.
3. **Aislamiento de red**: invitados NO pueden ver dispositivos de la red principal (importante si cliente tiene NAS / impresora compartida).
4. Limitación ancho banda opcional.

### Paso 6 — DNS personalizado (mejora privacidad y velocidad)

1. Panel admin → **WAN / Internet / DNS**.
2. Cambiar DNS por defecto del operador (que va lento + telemetría) por:
   - **Cloudflare 1.1.1.1 / 1.0.0.1** (más rápido, privado).
   - **Google 8.8.8.8 / 8.8.4.4** (estable, conocido).
   - **Quad9 9.9.9.9** (filtro malware).
3. Guardar.

### Paso 7 — Control parental (si cliente lo pide)

1. Algunos routers tienen módulo "Parental Control".
2. Configurar:
   - Dispositivos hijos (por MAC).
   - Horarios bloqueo (ej. desde 22h a 7h sin internet).
   - Filtros web (bloqueo categorías adultas, redes sociales, gaming).

### Paso 8 — Reserva IPs por MAC (DHCP estático)

Útil si tiene impresora / NAS / cámaras IP que necesitan IP fija.
1. Panel → **DHCP / Reservas IP**.
2. Añadir cada dispositivo: MAC + IP fija dentro del rango (ej. 192.168.1.50).
3. Reiniciar dispositivos para que tomen la IP nueva.

### Paso 9 — Port forwarding (avanzado, raro)

Solo si cliente tiene servidor en casa, cámaras accesibles desde fuera, etc.
1. Panel → **Port Forwarding / NAT**.
2. Abrir puertos específicos al dispositivo interno.
3. Avisar cliente del riesgo seguridad (puertos abiertos = más expuesto).

### Paso 10 — Test final velocidad y cobertura

1. Test velocidad desde mi portátil:
   - **fast.com** (Netflix, mide bajada).
   - **speedtest.net** (mide bajada + subida + ping).
2. Test cobertura recorriendo casa con el móvil → ver dB en cada habitación.
3. Si zonas muertas siguen → recomendar:
   - Cambiar ubicación router (centro casa, alto, sin obstáculos).
   - Repetidor WiFi (TP-Link RE315 / Asus RP-AC54).
   - Mesh (TP-Link Deco / Asus ZenWiFi / Eero) para casas grandes.

---

## Al cerrar

- [ ] Mostrar al cliente:
  - Su nueva contraseña apuntada (papel + WhatsApp).
  - Velocidad mejorada (test antes/después).
  - Cobertura.
- [ ] Cambiar también la contraseña del **panel admin del router** (default `admin/admin` es público): nueva contraseña fuerte, **cliente la teclea**, apuntar en papel.
- [ ] Cobrar **25€** (simple) o **35€** (completa con todo).
- [ ] Lanzar `entrega.bat` → factura `MPC-2026-XXXX`.
- [ ] Frase cierre: **"WiFi optimizado. Garantía 30 días en configuración. Si vuelve la lentitud o la red se cae → vuelvo gratis dentro del mes."**

---

## Errores frecuentes

_Pendiente actualizar tras 5 visitas reales._

Anticipados:
- **Cliente bloqueado fuera del panel admin** porque cambió pass y la olvidó: factory reset del router (botón pinhole 10 segundos), volver a configurar todo desde cero. Avisar al cliente del coste tiempo.
- **Router antiguo (>5 años) sin WPA3 ni 5GHz**: solo se puede mejorar hasta cierto punto. Recomendar router nuevo (TP-Link Archer AX23 ~50€ es el sweet spot).
- **Cobertura mala en piso pisos altos / casa grande**: 1 router no llega. Recomendar mesh o repetidor + recargo si lo instalo (35€ + tiempo extra).
- **Operador bloquea cambios** (Movistar Mitrastar antiguo solo permite SSID + password, no canal): explicar limitación al cliente. Solución es comprar router propio + bridge.
- **Cliente quiere "más velocidad" pero su línea contratada es 100 Mbps**: WiFi no puede dar más que la fibra contratada. Avisar antes.
- **Dispositivos viejos (móvil antiguo, TV antigua) no se conectan a WPA3**: bajar a WPA2 o WPA2/WPA3 mixto. Compatibilidad.
- **Cliente confía en "WiFi gratis vecino"**: NO ayudar a colarse en redes ajenas. Es delito.

---

## Tiempo total

- Cambio simple (SSID + pass): **20-30 min** → 25€.
- Configuración completa: **45-60 min** → 35€.

---

## Reglas críticas

🔴 **CLIENTE TECLEA contraseñas siempre**, yo NO las veo.
🔴 **Cambiar contraseña panel admin** del router (no solo WiFi). Default `admin/admin` es agujero seguridad público.
🔴 **WPA3 o WPA2-AES** solamente. NUNCA WEP, WPA1, TKIP.
🔴 **NO abrir puertos en NAT** sin que el cliente entienda el riesgo.
🔴 **NO ayudar a hackear redes vecinas**. Delito + ético.
🔴 **Apuntar nueva contraseña en papel + WhatsApp**, nunca solo de memoria.
🔴 **Si router del operador no permite cambios** → recomendar router propio en modo bridge. NO mentir al cliente.
🔴 **Foto del router antes y después**.
🔴 **NO instalar firmware modificado (DD-WRT, OpenWRT) sin que cliente sepa**: rompe garantía operador, bloquea acceso técnico operador. Servicio aparte, no estándar.
