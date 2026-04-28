# Recuperación contraseña Windows local (45€)

> Tiempo realista: **30-60 min** (depende del método y de si arranca a la primera)
> Bloque tarifa: **B — Mantenimiento Software**
> Modalidad: domicilio (taller posible, +25€ a la inversa: en taller estándar, en domicilio sin recargo este caso por urgencia típica)

---

## Qué es y qué NO es

**SÍ es:** desbloquear una **cuenta LOCAL** de Windows 10 / 11 cuya contraseña el cliente ha olvidado. Recuperar acceso al PC sin formatear, conservando archivos, programas y configuración.

**NO es:**
- ❌ **Cuenta Microsoft** (correo @hotmail / @outlook / @gmail vinculado): se resetea desde [account.microsoft.com](https://account.microsoft.com), NO es reparación técnica. **Decirle al cliente que lo haga él** desde otro dispositivo. Si insiste, le ayudo gratis con la web (5 min, no es servicio).
- ❌ **PIN olvidado pero contraseña sabida**: cliente la usa y va al menú Cuentas → Opciones de inicio de sesión → cambiar PIN. NO es servicio.
- ❌ **BitLocker activo sin clave de recuperación**: ⚠️ STOP, derivar a **Recuperación N1 130€** o **N2 350-800€** según gravedad. Sin la clave de recuperación NO se puede romper BitLocker en tiempo razonable.
- ❌ **Cuenta de dominio empresarial / Active Directory**: NO se toca. Cliente debe ir al admin de su empresa.

---

## Antes (preparación material)

### En el maletín (USB MASTER)
- [ ] **USB Ventoy rojo** (BACKUP) con `krd_2024.iso` (Kaspersky Rescue Disk con `chntpw`).
- [ ] **USB Lazesoft Recovery Suite** (alternativa más amigable, plan A en mayoría de casos).
- [ ] Pendrive vacío 4GB+ por si hay que crear uno nuevo en el momento.

### Confirmar por WhatsApp antes de salir
- [ ] **¿Cuenta local o Microsoft?** Si dice "le pongo el correo" → NO es servicio nuestro, derivar al reset web.
- [ ] **¿BitLocker activo?** Pantalla azul al arrancar pidiendo "clave de recuperación" → STOP, no es 45€.
- [ ] **Versión Windows** (10, 11) y **edición** (Home, Pro). Pro tiene casos especiales.
- [ ] **¿Hay datos importantes?** Si la cosa sale mal → Plan B es formatear, conviene saberlo.

### Material en mochila
- [ ] Portátil propio para soporte si me cuelgo en la BIOS.
- [ ] Adaptador USB-C → USB-A por si el cliente tiene portátil ultradelgado moderno.
- [ ] Resguardo papel firmado: descripción equipo + qué se va a hacer + asume conservación datos.

---

## Al llegar

- [ ] Comprobar visualmente la pantalla de login: confirmar que es **cuenta local** (sale el nombre de usuario sin @ correo). Si sale @gmail / @outlook / @hotmail / @live → ⚠️ **es cuenta Microsoft, no es nuestro servicio**, parar y explicar.
- [ ] Anotar **nombre exacto del usuario** que aparece en la pantalla de login.
- [ ] Reiniciar y entrar a **BIOS** (F2, F12, Del, Esc según marca):
  - Comprobar que **Secure Boot** está deshabilitable (si está bloqueado por contraseña BIOS → preguntar al cliente; si no la sabe → cambiar plan, ver Errores frecuentes).
  - Comprobar opción **Boot from USB**.
- [ ] Enchufar USB Ventoy rojo o USB Lazesoft.
- [ ] Cerrar BIOS guardando.

---

## Durante — Software paso a paso

### MÉTODO A — Lazesoft Recovery Suite Home (plan A, más rápido y limpio)

**Cuándo usarlo:** Windows 10 / 11 Home o Pro, cuenta local estándar. **90% de los casos.**

#### Paso 1 — Arrancar Lazesoft

1. Encender PC con USB Lazesoft enchufado.
2. Pulsar tecla boot menu (F12 / F11 / Esc según marca → ver chuleta).
3. Seleccionar **USB-HDD: Lazesoft**.
4. Espera ~1 min. Aparece menú con 4 opciones.
5. Pulsar **`1` Live CD! Password Recovery**. Enter.
6. Si pide license → **"Home Edition (Free for Personal Use)"**. Enter.

#### Paso 2 — Resetear contraseña

1. Pantalla principal: cuatro botones grandes.
2. Click **Reset Windows Password** (botón superior izquierda).
3. Acepta el aviso "for non-commercial use" → **Yes**.
4. Click **Next**.
5. Selecciona la **instalación de Windows** detectada (suele ser una sola, en `C:\Windows`). Si hay dos (raro) → la grande, no la de fábrica de recuperación.
6. Click **Next**.
7. Lista de usuarios. Selecciona el usuario que el cliente quiere desbloquear (anotado al llegar).
8. Click **Next**.
9. Marcar **`☑ Reset/Unlock Password`** (deja la cuenta sin contraseña, el cliente puede ponerse una nueva al iniciar sesión).
10. Click **RESET / UNLOCK**.
11. Espera 5-10 segundos. Mensaje **"Password is reset successfully"**.
12. Click **Finish**.
13. Cierra ventana → menú principal → **Restart Computer**. Quita el USB.

#### Paso 3 — Verificar

1. Windows arranca normal.
2. En la pantalla de login del usuario → pulsa Enter directamente sin escribir contraseña.
3. **Entra al escritorio.** ✅
4. Si quiere poner contraseña nueva: Win + I → Cuentas → Opciones de inicio de sesión → Contraseña → Agregar.

---

### MÉTODO B — chntpw vía krd Live USB (plan B si Lazesoft falla)

**Cuándo usarlo:** Lazesoft no detecta usuario, error "registry hive locked", Windows en disco encriptado parcialmente, instalaciones raras.

#### Paso 1 — Arrancar krd

1. Encender PC con USB Ventoy rojo.
2. Boot menu → **USB-HDD: Ventoy**.
3. Menú Ventoy: seleccionar **`krd_2024.iso`**. Enter.
4. Menú Kaspersky: seleccionar **"Kaspersky Rescue Tool"** → modo gráfico inglés. Enter.
5. Aceptar EULA (scroll abajo del todo, pulsar `1` aceptar).
6. Espera ~1 min. Carga escritorio Linux con icono carpeta.

#### Paso 2 — Montar partición Windows

1. Doble click en icono **"Computer"** (escritorio).
2. Localizar la partición de Windows (suele ser la grande, 200GB+, etiquetada como NTFS sin nombre o "Windows"). NO confundir con "Recovery" (500MB) ni "EFI" (100MB).
3. Click derecho sobre ella → **Mount**.
4. Anota el punto de montaje que aparece, suele ser `/mnt/disk/sda3` o similar.

#### Paso 3 — Abrir terminal

1. Click derecho en escritorio → **Open Terminal**. (Si no aparece: menú inferior izquierda → Terminal.)
2. Escribir y Enter:
   ```
   cd /mnt/disk/sda3/Windows/System32/config
   ```
   (Cambiar `sda3` por lo que apuntaste en paso anterior.)
3. Comprobar que el archivo SAM existe:
   ```
   ls -la SAM
   ```
   Debe salir un archivo de unos 30-60KB. Si no aparece → has montado partición equivocada, vuelve atrás.

#### Paso 4 — Ejecutar chntpw

1. Lanzar la herramienta:
   ```
   chntpw -i SAM
   ```
2. Aparece menú con opciones:
   ```
   1 - Edit user data and passwords
   2 - List groups
   9 - Registry editor, now with full write support!
   q - Quit (you will be asked if there is something to save)
   ```
3. Pulsar **`1`** + Enter.
4. Lista de usuarios con RID. Buscar el usuario del cliente (anotado).
5. Escribir el RID (ej. `01f4`) o el username completo + Enter.
6. Aparece submenú:
   ```
   1 - Clear (blank) user password
   2 - Unlock and enable user account
   3 - Promote user (make user an administrator)
   4 - Add user to a group
   5 - Remove user from a group
   q - Quit editing user, back to user select
   ```
7. Pulsar **`1`** + Enter → **`Password cleared!`**.
8. Pulsar **`q`** + Enter (sale del usuario).
9. Pulsar **`q`** + Enter de nuevo (sale del menú principal).
10. **¡IMPORTANTE!** Pregunta `Hives that have changed: 0 - <SAM>. Write hive files? (y/n)` → pulsar **`y`** + Enter.
11. Confirma `Sam: OK`.

#### Paso 5 — Reiniciar

1. En terminal:
   ```
   reboot
   ```
2. Quitar USB rojo cuando empiece a apagar.
3. Windows arranca → login del usuario → Enter directo sin contraseña → ✅ entra.

---

### MÉTODO C — Cuenta admin oculta (plan C si A y B fallan)

**Cuándo usarlo:** muy raro, casos donde SAM está corrupta o el sistema bloquea el reset.

1. Arrancar Windows con USB instalación Win 10 / 11 (USB Arsenal rojo Ventoy).
2. En instalador → **Reparar el equipo** → **Solucionar problemas** → **Símbolo del sistema**.
3. En consola, escribir:
   ```
   move C:\Windows\System32\Utilman.exe C:\Utilman_backup.exe
   copy C:\Windows\System32\cmd.exe C:\Windows\System32\Utilman.exe
   ```
4. Reiniciar normal.
5. En pantalla de login → click icono **"Accesibilidad"** (esquina inferior derecha).
6. Se abre **una consola con permisos SYSTEM**. ✅
7. Crear usuario admin temporal:
   ```
   net user TecnicoMPC Pass1234! /add
   net localgroup Administradores TecnicoMPC /add
   ```
8. Cerrar consola. Login con **TecnicoMPC** / **Pass1234!**.
9. Una vez dentro: cambiar contraseña del usuario original desde Panel de Control → Cuentas de usuario.
10. **LIMPIAR** después: arrancar de nuevo con USB Win, consola, restaurar Utilman:
    ```
    copy C:\Utilman_backup.exe C:\Windows\System32\Utilman.exe
    del C:\Utilman_backup.exe
    ```
11. Borrar usuario TecnicoMPC desde dentro de Windows: `net user TecnicoMPC /delete`.

⚠️ Este método deja huellas (tienes que borrarlas tú al final). NO usarlo si no es estrictamente necesario.

---

## Al cerrar

- [ ] **Verificar acceso real** delante del cliente: que entre con Enter, navegue, abra el navegador, vea sus archivos.
- [ ] **Recordarle que ponga contraseña nueva** desde Configuración → Cuentas (o que use PIN).
- [ ] **Decirle que NO vincule cuenta Microsoft** si no quiere depender de internet — explicar pros/contras 1 minuto.
- [ ] **Recoger USB** y verificar que NO queda nada enchufado.
- [ ] Resguardo firmado entregado al cliente.
- [ ] Cobrar **45€** (Bizum o efectivo).
- [ ] Lanzar `entrega.bat` del maletín → genera factura `MPC-2026-XXXX` + cartel Bizum + WhatsApp seguimiento.
- [ ] Frase de cierre: **"Si no lo arreglamos, no cobramos. Hoy salió, así que cobramos. Garantía 30 días por si vuelve a pasar."**

---

## Errores frecuentes

_Pendiente actualizar tras 5 visitas reales._

Casos ya identificados anticipados:
- **BIOS bloqueada con contraseña** que el cliente no recuerda: si está bloqueada, no se puede deshabilitar Secure Boot ni elegir USB → **plan B real:** sacar el disco, conectarlo a mi portátil con adaptador USB-SATA / NVMe, ejecutar Lazesoft sobre el disco extraído. Lleva +30 min y +1 paso "abrir el equipo". Cobrar 45€ igual.
- **Equipo con TPM + cuenta Microsoft + Windows 11 Home** que el cliente "cree" que es local: comprobar al llegar antes de empezar. Si es Microsoft → reset web 5 min gratis y se cobra **0€** (asesoría no aplica si fue 5 min).
- **Surface / portátiles ultradelgados con SSD soldado**: no se puede sacar el disco → si BIOS está bloqueada, derivar a soporte fabricante. NO cobrar.

---

## Tiempo total

- Lazesoft sin complicaciones: **30-40 min** + desplazamiento.
- chntpw vía krd: **45-60 min** + desplazamiento.
- Plan C Utilman: **60-90 min** (más limpieza posterior).

---

## Reglas críticas

🔴 **CONFIRMAR cuenta LOCAL antes de aceptar el servicio.** Si es Microsoft, no se cobran 45€. Es reset web gratis.
🔴 **BitLocker activo sin clave de recuperación → STOP.** Derivar a N1 130€ o N2 350-800€ según gravedad. **NO intentar romper BitLocker.**
🔴 **NO usar Method C (Utilman)** si A o B han funcionado. Deja huellas y hay que limpiarlas.
🔴 **Resguardo firmado obligatorio.** Reset password puede asustar al cliente si interpreta mal "te ha entrado en el equipo". El papel cubre.
🔴 **NUNCA mirar archivos personales del cliente** — abrir Documentos para "comprobar que está todo" es lo máximo. NO entrar a Fotos, navegador, correo.
🔴 **NO instalar nada de tu cosecha** (antivirus, "limpiadores"). Solo desbloquear y salir.
🔴 **Si el cliente pide guardar la contraseña nueva en algún sitio "para que no se le olvide"** → recomienda Bitwarden gratis. NO la apuntes tú en ningún sitio.
