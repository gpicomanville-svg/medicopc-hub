# Limpieza Completa — 90€

**ID tarifa:** `pack_limpieza_completa`
**Bloque:** B Mantenimiento · Software
**Tiempo realista:** 90 min (rango 60-120)
**Cuando aplica:** PC funciona pero está lento, ruidoso, calienta. Cliente nota degradación. Polvo visible en filtros. Pasta térmica vieja. **NO** Windows roto (eso es Formateo+Backup) **NO** sin arranque (eso es Diagnóstico + lo que toque).

---

## Antes de visita

- **Confirmar al teléfono** que el PC enciende y arranca a Windows aunque sea lento. Si no arranca → cambiar servicio.
- **Confirmar credenciales Windows** del cliente (login). Si no las tiene → +Recup contraseña 45€ aparte.
- **Pieza extra a confirmar**: si la pasta térmica lleva >2 años, el cliente debe saber que se sustituye. Coste pasta incluido en este pack.

**Llevar en USB Arsenal Master (D:):**
- Maletín completo (siempre).

**Llevar en mochila:**
- Pasta térmica (KTC1 o Arctic MX-6).
- Pads térmicos (Thermalright varios grosores).
- Kit destornilladores (PH0, PH1, PH2 + Torx pequeño para portátiles).
- Brocha antiestática + bote aire comprimido (o soplador eléctrico si tienes).
- Bayeta microfibra + isopropílico 90%+.

---

## Al llegar (5-10 min)

1. **Saludar cliente, ubicar PC**. Foto frontal del estado físico inicial (móvil empresa cuando haya).
2. Lanzar **`Scripts\0_LLEGADA\llegada.bat`** desde USB → genera checklist de estado, cliente firma en tablet.
3. Mientras firma: pregunta clave **"¿qué notas peor?"** (lentitud arranque / juegos / ruido / temperatura). Te dice el síntoma principal, lo apuntas mentalmente para validarlo después.

---

## Durante

### Software (corre mientras desmontas)

1. **`Scripts\11_DIAGNOSTICO_LLEGADA\guiado.bat`** captura SMART, hardware, temps actuales (HWiNFO en silencio), eventos sistema. Punto de partida medible.
2. **AdwCleaner** (`Tools\AdwCleaner\AdwCleaner.exe`) → escaneo completo → quitar adware + PUP detectado. Reinicio que pida → reinicio.
3. **Sysinternals Autoruns** (`Tools\Sysinternals\Autoruns.exe`) → revisar pestañas Logon + Scheduled Tasks + Services. Desmarcar lo basura (toolbars, updaters obsoletos, programas que el cliente no usa). **NO BORRAR**, solo desmarcar para conservar trazabilidad.
4. Limpieza temporales: `cleanmgr /sageset:1` luego `cleanmgr /sagerun:1` con todo marcado. Alternativa: BleachBit si quieres más profundidad.
5. Caché navegadores Edge + Chrome + Firefox (NO marcar passwords ni autofill).
6. **Defrag** solo si HDD (`Optimizar y desfragmentar unidades`). En SSD el sistema lanza TRIM solo, no tocar.

### Físico (técnico)

1. **Apagar PC**, desconectar todo, llevar a mesa de trabajo.
2. **Abrir caja**. Foto del interior con polvo (móvil).
3. **Soplado / brocha** en orden:
   - Filtros frontales y superiores (sacarlos si se pueden y golpear contra la basura).
   - Aspas ventiladores (sujetar el aspa con dedo para que no gire al soplar — soplar girando rompe rodamiento).
   - Disipador CPU (de arriba a abajo para que el polvo salga, no entre).
   - Disipador GPU si accesible.
   - Fuente (no abrir, soplar por las rejillas).
4. **Sacar disipador CPU**:
   - Aflojar tornillos en cruz, no de seguido.
   - Despegar girando suave si está pegado por pasta vieja seca.
   - Limpiar pasta vieja del IHS y del disipador con isopropílico + bayeta.
5. **Aplicar pasta nueva** (gota tamaño grano arroz centro IHS, NO esparcir, la presión del disipador la reparte sola).
6. **Pads térmicos**: solo cambiar los que estén SECOS o aplastados sin volumen. Si están blandos y húmedos, dejar.
7. **Reensamblar disipador** apretando en cruz, sin pasarse de torque.
8. **Foto interior limpio**.
9. **Cerrar caja**, conectar todo, encender.
10. Validar boot OK + entrar a Windows + comprobar temps con HWiNFO (CPU idle <50°C objetivo, antes seguramente >65°C).

---

## Al cerrar (10-15 min)

1. Sentar al cliente delante: enseñar **temps antes vs después** en HWiNFO (5-15°C menos típico).
2. Lanzar **`Scripts\14_ENTREGA\entrega.bat`** desde USB → genera 3 entregables en 30s:
   - Cartel pago Bizum PDF (A4 con QR, número, monto).
   - Factura simplificada PDF (cumple AEAT art. 7).
   - Texto WhatsApp con tono cálido al portapapeles.
3. **Cobrar 90€** efectivo o Bizum. Si zona M30/M40/lejana → +20/30/45€.
4. Trigger en chat Claude: **"hemos terminado"** → dispara `register_session` + `cerrar_entrega` (BBDD + factura registrada).
5. Pegar el WhatsApp al cliente con el botón de su teléfono.

---

## Errores frecuentes / casos raros

_Pendiente actualizar tras 5 visitas reales._

---

## Tiempo total estimado

- **Mínimo**: 60 min (PC limpio relativamente, caja accesible, todo va fluido).
- **Realista**: 90 min.
- **Jodido**: 120 min (caja apretada mini-ITX, disipador agarrado, fuente con polvo extremo, BIOS con eventos raros que requieren mirar).
