# Limpieza Básica (60€)

> Tiempo realista: **45-75 min**
> Bloque tarifa: **B — Mantenimiento Software**
> Modalidad: domicilio o taller (sin recargo). Servicio corto, encaja bien en domicilio.

---

## Qué es y qué NO es

**SÍ es:** limpieza software del sistema (temporales, caché, bloatware preinstalado, programas obvios que sobran, arranque, navegadores) + limpieza exterior del PC (pantalla, teclado, ratón, carcasa con paño microfibra). PC va más rápido y se ve más cuidado, sin abrir nada.

**NO es:**
- ❌ **Apertura del equipo, soplado interior, pasta térmica**: eso es **Limpieza Completa 80€**.
- ❌ **Servicing GPU** (desmontar gráfica gaming): eso es **Limpieza+GPU 120€** o **Pack Gaming 150€**.
- ❌ **Antivirus profundo** con HitmanPro / Malwarebytes en safe mode: si hay malware confirmado → **Limpieza Completa 80€** (incluye anti-malware) o derivar.
- ❌ **Formateo + reinstalación**: si Windows está demasiado roto → **Formateo+Backup 80€**.

---

## Antes (preparación)

### Confirmar por WhatsApp
- [ ] **Síntoma**: PC lento, se calienta, el ventilador hace ruido, demasiados pop-ups.
- [ ] **¿Notas malware?** (pop-ups raros, navegador secuestrado, redirecciones). Si SÍ → propon Limpieza Completa 80€.
- [ ] **Edad PC** (>5 años con HDD mecánico → no merece Limpieza Básica, sale mejor SSD nuevo).

### Material en mochila
- [ ] **USB Arsenal MASTER** con: AdwCleaner, Malwarebytes Free portable, RKill, BleachBit, AutoRuns (Sysinternals).
- [ ] **Paño microfibra seco**.
- [ ] **Paño microfibra ligeramente húmedo** (alcohol isopropílico 70% en pequeño bote).
- [ ] **Bote aire comprimido** (pequeño, para limpiar entre teclas).
- [ ] **Cepillo blando** para teclado.
- [ ] **Bastoncillos de algodón** para esquinas.

---

## Al llegar

- [ ] Saludar, ver el PC en su sitio. Foto del estado inicial.
- [ ] Pedir al cliente que cierre todo lo que tenga abierto.
- [ ] Lanzar diagnóstico llegada `DL-yymmdd` mientras hablamos para tener línea base.
- [ ] Comprobar espacio libre en disco. Si <10% → avisar al cliente que sin liberar espacio no irá rápido aunque limpiemos.

---

## Durante — Software paso a paso

### Paso 1 — RKill (matar procesos basura activos)

1. Pendrive → `Tools\RKill\rkill64.exe` → click derecho → Ejecutar como administrador.
2. Espera 1-2 min. Mata procesos malware comunes y de adware activo.
3. Cuando termine genera log en escritorio. NO reiniciar todavía.

### Paso 2 — AdwCleaner (Malwarebytes adware/PUP)

1. `Tools\AdwCleaner\adwcleaner.exe` → click derecho → Ejecutar como administrador.
2. Click en **"Escanear ahora"**.
3. Espera 5-10 min mientras analiza.
4. Aparece lista de detecciones (extensiones navegador raras, programas adware, tareas programadas sospechosas).
5. Revisar la lista 30 segundos. Si reconoces algo legítimo del cliente → desmarcar. Por defecto, todo seleccionado se elimina.
6. Click **"Cuarentena"**.
7. Pide reiniciar. **NO reiniciar todavía** (queda paso 3).

### Paso 3 — Malwarebytes Free portable (escaneo malware)

1. `Tools\Malwarebytes\mbam-portable.exe`.
2. Pestaña Escaneo → **Escaneo completo** (tarda 20-40 min según disco).
3. Mientras escanea → seguir con paso 4 (limpieza Windows nativa) y paso 5 (físico).
4. Cuando termine → revisar amenazas. Cuarentena todo.

### Paso 4 — Limpieza Windows nativa

#### Liberador de espacio en disco
1. Win + R → `cleanmgr` → Enter.
2. Seleccionar C:\.
3. **"Limpiar archivos del sistema"** (botón abajo).
4. Marcar TODO menos:
   - "Descargas" (puede haber cosas del cliente)
   - "Archivos de programa descargados" (mejor sí)
   - "Vista previa miniaturas" (mejor sí)
5. Aceptar. Espera 5-15 min según basura acumulada.

#### Storage Sense
1. Configuración → Sistema → Almacenamiento → **Storage Sense**.
2. Activar. Configurar: borrar archivos en papelera tras 30 días, descargas no abiertas tras 60 días.

#### Programas que sobran
1. Configuración → Aplicaciones → Aplicaciones instaladas.
2. Ordenar por **fecha de instalación**.
3. Desinstalar bloatware obvio:
   - **McAfee / Norton** preinstalados (si no los paga).
   - **Toolbars de navegador**: Bing Bar, Yahoo Toolbar, Ask Toolbar.
   - **PC Cleaners**: Advanced SystemCare, CCleaner si no lo usa, "PC Optimizer Pro", "WinZip Driver Updater".
   - **Apps Lenovo / HP / Acer** obvias (Lenovo Vantage sí dejar, drivers; pero "Lenovo Pen Settings" si no usa lápiz, fuera).
   - **Aplicaciones Candy Crush / Bubble Witch / Dropbox Promotional** (Win 11 Home las trae preinstaladas).
4. **Preguntar al cliente** si reconoce algo dudoso antes de borrar.

### Paso 5 — Optimizar arranque (AutoRuns)

1. `Tools\Sysinternals\Autoruns64.exe` → click derecho → Ejecutar como administrador.
2. Pestaña **Logon** (la primera).
3. Botón **Options → Hide Microsoft Entries** (oculta procesos legítimos del sistema).
4. Aparecen 10-30 entradas según equipo.
5. Desmarcar (NO borrar, solo desactivar) lo que NO sea esencial:
   - Software de impresora (puede arrancar al imprimir).
   - Adobe Updater, Java Updater (raros últimamente).
   - Spotify, Discord, Steam si arrancan automáticos sin que cliente quiera.
   - Apps de cámara fabricante.
6. **Dejar SIEMPRE marcado**:
   - Antivirus (Defender o pagado).
   - Driver gráfico (NVIDIA Container, AMD Radeon).
   - Trackpad / sonido / drivers de hardware.
7. Pestaña **Scheduled Tasks**: lo mismo, ocultar Microsoft, desactivar tareas de adware/bloatware.
8. Cerrar Autoruns.

### Paso 6 — BleachBit (limpieza profunda)

1. `Tools\BleachBit\bleachbit_portable\bleachbit.exe`.
2. Marcar:
   - **System** → "Memory dump", "Recycle bin", "Temporary files", "Logs".
   - **Internet Explorer / Edge** → todo.
   - **Firefox / Chrome / Brave** según navegadores que use → "Cache", "Vacuum" (compacta BBDD historial). NO "Cookies" si no quiere reloguear cuentas.
3. Click **Vista previa** primero (muestra cuánto liberará, no borra).
4. Si OK → **Limpiar**.

### Paso 7 — Navegadores: extensiones sospechosas

#### Chrome
1. `chrome://extensions/`
2. Quitar extensiones no reconocidas: barras de búsqueda raras, "Easy Search", "Coupon Helper", VPN gratuitas, traductores no usados.

#### Edge
1. `edge://extensions/`
2. Mismo criterio.

#### Firefox
1. `about:addons`
2. Mismo criterio.

### Paso 8 — Verificación

1. Reiniciar PC.
2. Cronometrar arranque desde botón hasta escritorio listo. Si supera 90 segundos en disco mecánico → recomendar SSD. En SSD <30 segundos.
3. Comprobar que el navegador del cliente abre rápido (Chrome/Edge).
4. Administrador de tareas → comprobar que ningún proceso raro sigue arriba con CPU/RAM.

---

## Durante — Físico paso a paso (limpieza exterior)

### Pantalla
1. Apagar pantalla (más fácil ver suciedad).
2. Paño microfibra **seco** primero, en círculos suaves desde el centro hacia fuera.
3. Si hay manchas resistentes → microfibra ligeramente humedecida con alcohol isopropílico (NO mojar la pantalla directamente).
4. NUNCA limpiacristales con amoníaco (rompe el recubrimiento).

### Teclado
1. Volcar el teclado boca abajo y dar golpecitos suaves para sacar migas y polvo.
2. Bote de aire comprimido entre las teclas.
3. Cepillo blando entre teclas.
4. Microfibra húmeda con alcohol pasada por superficie de las teclas.

### Ratón
1. Microfibra húmeda alcohol por carcasa y rueda.
2. Bastoncillo alcohol para grietas.
3. Comprobar que el sensor óptico (parte inferior) no tiene pelos.

### Carcasa PC sobremesa o portátil (exterior)
1. Microfibra seca para polvo.
2. Microfibra húmeda alcohol para huellas dactilares y manchas.
3. NO abrir el equipo (eso es Limpieza Completa).

### Rejillas externas (sobremesa) y respiradero portátil
1. Bote de aire comprimido por la rejilla, **siempre desde fuera hacia dentro** (NO al revés, mete polvo).
2. Si los ventiladores están MUY sucios visibles desde fuera → NO se trata bien sin abrir. Recomendar Limpieza Completa al cliente como upgrade.

---

## Al cerrar

- [ ] Reiniciar PC delante del cliente y enseñar tiempo de arranque mejorado.
- [ ] Mostrar Administrador de tareas → bandeja sistema con menos iconos.
- [ ] Si has visto bloatware grave / malware → enseñar log de Malwarebytes/AdwCleaner: "esto tenías".
- [ ] Recomendar mantener: Defender Windows ON, no instalar "PC Optimizers", actualizar Windows mensual.
- [ ] Cobrar **60€** Bizum o efectivo.
- [ ] Lanzar `entrega.bat` → factura `MPC-2026-XXXX`.
- [ ] Frase cierre: **"Garantía 30 días en limpieza. Si vuelve la lentitud por algo que se nos haya escapado, vuelvo gratis."**

---

## Errores frecuentes

_Pendiente actualizar tras 5 visitas reales._

Anticipados:
- **Cliente trae PC viejo HDD mecánico**: limpieza ayuda 20%, no resuelve la lentitud estructural. Avisar antes de cobrar 60€ que la mejora será limitada. Mejor proponer SSD pieza + 30€ MO + 50€ clonado = 145€.
- **Cliente con cuenta sincronizada Google/Microsoft**: si borras caché del navegador puede pedirle reloguear. Avisar antes y tener a mano la opción de NO marcar cookies en BleachBit.
- **Defender Windows agresivo bloquea AdwCleaner / Malwarebytes**: añadir excepción temporal en Defender → Protección contra virus → Excepciones, ruta del USB. Quitar excepción al terminar.

---

## Tiempo total

- Sin malware: **45-60 min**.
- Con malware (escaneo Malwarebytes completo): **75 min**.

---

## Reglas críticas

🔴 **NO borrar archivos personales del cliente.** Documentos, Fotos, Descargas: mirar pero NO tocar sin permiso.
🔴 **NO desinstalar antivirus de pago activo** sin avisar al cliente. Aunque sea Norton penoso, es su licencia.
🔴 **NO desactivar arranque de drivers de hardware** (sonido, gráfica, trackpad, WiFi). Romper esto es romper el PC.
🔴 **NO usar limpiacristales con amoníaco** en pantalla. Rompe recubrimiento.
🔴 **NO meter aire comprimido boca abajo** ni demasiado cerca (puede congelar componentes).
🔴 **Si encuentras pornografía / contenido raro / archivos delicados** → ignorar, no comentar nada al cliente, no abrir, no mirar.
🔴 **Si encuentras malware confirmado** → considerar upgrade a Limpieza Completa 80€ con consentimiento. La diferencia 60→80€ cubre el escaneo profundo y reinstalación parcial.
