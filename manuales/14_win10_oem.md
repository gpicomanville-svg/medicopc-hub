# Instalación Windows 10 OEM (80€)

> Tiempo realista: **2-3h** + desplazamiento
> Bloque tarifa: **B — Mantenimiento Software**
> Modalidad: taller por defecto · domicilio +25€

---

## Qué es y qué NO es

**SÍ es:** instalación limpia de **Windows 10** sobre PC que **no soporta Windows 11** (sin TPM 2.0, CPU antigua, etc.) o cliente que **prefiere Win 10** sobre Win 11. ESU (Extended Security Updates) opcional bajo suscripción Microsoft.

**NO es:**
- ❌ **Win 11 OEM 80€**: para PCs modernos con TPM 2.0.
- ❌ **Formateo seco 70€**: para "limpiar" un PC con sistema previo.
- ❌ **Migración 100€**: incluye Win nuevo + datos del PC viejo.

**Cliente típico:**
- PC 2014-2018 con CPU pre-Coffee Lake / pre-Ryzen 2000.
- Cliente que rechaza Win 11 (UI, rendimiento, política).
- PC industrial / ofimática vieja que solo necesita aguantar 1-2 años más.

⚠️ **Avisar siempre al cliente:** Microsoft **terminó soporte estándar de Win 10 el 14 octubre 2025**. Existe **ESU consumer** (Extended Security Updates) por suscripción anual. Sin ESU → Win 10 sigue funcionando pero **sin parches de seguridad**. Decisión informada del cliente.

---

## Antes (preparación material)

### Confirmar por WhatsApp
- [ ] **Por qué Win 10 y no Win 11** (verificar que no es por desconocimiento).
- [ ] **Modelo PC** + año aproximado.
- [ ] **¿Tiene clave Win 10?** Si tiene clave OEM en BIOS → automática. Si no → comprar Keys4US o usar clave del PC anterior si está vinculada a cuenta MS.
- [ ] **¿Quiere ESU?** Si dice sí → coste extra Microsoft (no nuestro precio), explicar.

### Material en mochila
- [ ] **USB Ventoy rojo** con `W10_22H2_ES.iso`.
- [ ] **USB MASTER** con Tools.
- [ ] Cable Ethernet.
- [ ] Pendrive personal para backup clave OEM si la extraigo.

---

## Al llegar

### Paso 1 — Razonar Win 10 (última oportunidad de cambiar a Win 11)
- Si el PC SÍ soporta Win 11 (TPM 2.0 + Secure Boot + UEFI) → preguntar al cliente otra vez si está seguro. Win 11 tendrá soporte hasta 2031+.
- Si el PC NO soporta Win 11 → directo a Win 10 (no hay opción).
- Si el cliente dice "no me gusta la barra centrada" → recordarle que Win 11 se puede alinear izquierda. NO insistir más allá, respetar decisión.

### Paso 2 — Si es PC con Windows previo
- Extraer clave OEM (`wmic` o PowerShell `OA3xOriginalProductKey`).

### Paso 3 — Foto BIOS / configuración previa
Si hay configuraciones BIOS específicas → foto antes.

---

## Durante — Instalación

### Paso 1 — Arrancar instalador Win 10

1. USB Ventoy → `W10_22H2_ES.iso` → Boot in normal mode.
2. Idioma Español España, formato España, teclado Español. Siguiente.
3. Click **Instalar ahora**.
4. **Activación**: clave OEM si tienes / "No tengo clave" si no.
5. **Edición**: Home / Pro según corresponda.
6. EULA → aceptar.
7. **Personalizada**.

### Paso 2 — Particionado

#### Disco vacío
- Espacio sin asignar → Siguiente.

#### Disco con Windows previo
- Borrar TODAS las particiones del disco principal.
- Espacio sin asignar → Siguiente.
- ⚠️ NO tocar segundo disco.

### Paso 3 — Esperar instalación (15-30 min, reinicia 1-2 veces).

### Paso 4 — OOBE Windows 10

1. **Cortana** → desactivar voz si la activa.
2. **Región**: España.
3. **Teclado**: Español.
4. **Conectar a red**: WiFi o Ethernet.
5. **Cuenta**:
   - **Cuenta local** sigue siendo opción visible en Win 10 OOBE (más fácil que Win 11).
   - O cuenta MS si el cliente prefiere.
6. **PIN** temporal 1234.
7. **Privacidad**: TODO desactivado.
8. **Cortana**: declinar.
9. **OneDrive**: declinar.

### Paso 5 — Configuración post-instalación

#### Activación
1. Win + I → Actualización y seguridad → Activación.
2. Verificar estado.

#### Drivers
- Windows Update → buscar. Win 10 lleva una década, los drivers básicos vienen casi todos.
- Drivers específicos web fabricante (GPU, chipset).

#### Software esencial
- Pack winget mismo que Win 11.

### Paso 6 — ESU (si el cliente lo paga)

1. Win + I → Actualización y seguridad → Windows Update.
2. Ver si aparece opción **"Inscribirse en ESU"** (banner / botón).
3. Si aparece:
   - Cliente paga su suscripción consumer (~30€/año).
   - Inscripción con cuenta MS.
4. Si NO aparece (PC todavía no elegible):
   - Confirmar requisitos al cliente: Win 10 22H2 con todas las actualizaciones al día.
   - Volver a comprobar tras Windows Update completo.

⚠️ Si el cliente NO quiere pagar ESU → el PC sigue funcionando, pero **sin parches de seguridad nuevos**. Recomendar al cliente:
- Defender activo siempre.
- No abrir adjuntos raros.
- Navegador actualizado (Chrome/Firefox sí siguen actualizándose en Win 10 hasta 2028 aprox).
- Considerar paso a Win 11 con PC nuevo en próximos 12-18 meses.

---

## Al cerrar

- [ ] Demostrar:
  - Windows 10 activado.
  - Drivers OK.
  - Internet, programas básicos funcionan.
- [ ] **Avisar verbalmente y por WhatsApp**: "Windows 10 ya no recibe actualizaciones de seguridad estándar. Si quieres seguridad continua, hay que pasar a Win 11 (PC nuevo) o pagar suscripción ESU a Microsoft. Te lo apunto en el WhatsApp."
- [ ] Cambiar PIN temporal.
- [ ] Cobrar **80€** Bizum o efectivo.
- [ ] Lanzar `entrega.bat` → factura `MPC-2026-XXXX`.
- [ ] Frase cierre: **"Garantía 30 días en la instalación. Si Windows da problemas, vuelvo. Pero recuerda que ya no le llegan parches automáticos a este sistema."**

---

## Errores frecuentes

_Pendiente actualizar tras 5 visitas reales._

Anticipados:
- **PC que SÍ soporta Win 11** y cliente insiste en Win 10 por desconocimiento: explicar 2 minutos y dejar que decida. NO imponer.
- **Drivers Win 10 que YA NO existen** para hardware muy nuevo (RTX 50, Ryzen 9000): confirmar antes de empezar. Si no hay driver Win 10 → Win 11 obligado.
- **ESU no aparece como opción**: el PC tiene que estar 22H2 con todo al día. A veces requiere 1-2 reinicios y reintentos.
- **Cliente con cuenta MS sin verificar correo**: la activación digital falla. Pedirle que verifique correo antes de seguir.
- **PC pre-2010** con BIOS Legacy y CPU antiquísima: a veces ni Win 10 22H2 instala. Caso límite, valorar honestamente si el equipo merece la pena.

---

## Tiempo total

- Instalación Win 10: **45-60 min**.
- Drivers + Update: **30-45 min**.
- Software esencial: **10-15 min**.
- Configuración + entrega: **15-30 min**.
- **Total: 2-3h.**

---

## Reglas críticas

🔴 **Confirmar 2 veces que el cliente entiende** la situación de Win 10 fin de soporte.
🔴 **Si el PC soporta Win 11 → preguntar primero**. No imponer pero sí informar.
🔴 **Drivers Win 10 disponibles**: confirmar antes de instalar. Hardware muy nuevo puede no tener Win 10.
🔴 **ESU**: explicar coste extra Microsoft (no es nuestro precio). Cliente decide.
🔴 **NO tocar segundo disco** sin confirmación.
🔴 **NO bloatware** ni software pirata.
🔴 **Privacidad en cero**.
🔴 **Aviso WhatsApp** sobre fin soporte Win 10. Documenta que se le ha dicho. Cubre culo si vuelve en 6 meses con virus por no tener parches.
