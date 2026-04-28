# Chuleta — Recuperación contraseña Windows local

> Para llevar en bolsillo / impresa en mochila. Comandos exactos, sin teoría.
> Servicio: **Recuperación pass Windows local 45€** · Manual completo en `09_recuperacion_pass_windows.md`.

---

## Decisión rápida — ¿es nuestro servicio?

```
Pantalla login muestra @gmail / @outlook / @hotmail / @live  →  NO es local. Cuenta MS.
                                                                   Reset web 5 min, cobrar 0€.

Pantalla login muestra solo nombre usuario sin @  →  SÍ es local. Adelante 45€.

Pide "clave de recuperación BitLocker" al arrancar  →  STOP. No es 45€.
                                                       Derivar a N1 130€ o N2 350-800€.

Cuenta de dominio empresa / Active Directory  →  NO se toca. Admin de su empresa.
```

---

## MÉTODO A — Lazesoft (plan A, 90% casos)

### Boot
```
1. USB Lazesoft enchufado.
2. F12 / F11 / Esc → boot menu.
3. USB-HDD: Lazesoft.
4. Esperar ~1 min.
5. Pulsar 1 → Live CD! Password Recovery → Enter.
6. Si pide license → Home Edition (Free for Personal Use) → Enter.
```

### Reset
```
1. Click Reset Windows Password.
2. Aviso non-commercial → Yes.
3. Next.
4. Seleccionar instalación Windows en C:\Windows → Next.
5. Seleccionar usuario → Next.
6. Marcar ☑ Reset/Unlock Password.
7. Click RESET / UNLOCK.
8. Esperar 5-10 segundos → "Password is reset successfully".
9. Finish → Restart Computer → quitar USB.
10. Login: Enter sin contraseña → entra al escritorio.
```

---

## MÉTODO B — chntpw vía krd (plan B si Lazesoft falla)

### Boot
```
1. USB Ventoy rojo enchufado.
2. F12 → boot menu → USB-HDD: Ventoy.
3. Menú Ventoy → krd_2024.iso → Enter.
4. Menú Kaspersky → Kaspersky Rescue Tool → modo gráfico inglés.
5. Aceptar EULA: pulsar 1.
6. Esperar ~1 min hasta escritorio Linux.
```

### Montar partición Windows
```
1. Doble click en "Computer" del escritorio.
2. Localizar partición NTFS grande (200GB+, sin nombre o "Windows").
3. NO confundir con Recovery (500MB) ni EFI (100MB).
4. Click derecho → Mount.
5. Anotar punto de montaje (ej: /mnt/disk/sda3).
```

### Terminal y chntpw
```
Click derecho escritorio → Open Terminal.

cd /mnt/disk/sda3/Windows/System32/config

ls -la SAM
   (debe salir archivo 30-60KB; si no aparece → mal montaje)

chntpw -i SAM
```

### Menú chntpw
```
Aparece:
   1 - Edit user data and passwords
   2 - List groups
   9 - Registry editor
   q - Quit

→ Pulsar 1 + Enter.

Lista usuarios con RID:
→ Escribir el RID (ej: 01f4) o username + Enter.

Submenú usuario:
   1 - Clear (blank) user password
   2 - Unlock and enable user account
   3 - Promote user (make admin)
   4 - Add user to a group
   5 - Remove user from a group
   q - Quit

→ Pulsar 1 + Enter → "Password cleared!"
→ Pulsar q + Enter (sale del usuario).
→ Pulsar q + Enter (sale del menú principal).

CRÍTICO:
   Pregunta: "Hives that have changed: 0 - <SAM>. Write hive files? (y/n)"
   → Pulsar y + Enter.
   Confirma: "Sam: OK".
```

### Reiniciar
```
reboot
```
Quitar USB rojo cuando empiece a apagar. Login → Enter sin contraseña → entra.

---

## MÉTODO C — Utilman trick (último recurso)

### Boot con USB instalación Windows
```
1. USB Ventoy rojo → W11_25H2_ES.iso → Boot.
2. Pantalla instalador → "Reparar el equipo".
3. Solucionar problemas → Símbolo del sistema.
```

### Sustituir Utilman por cmd
```
move C:\Windows\System32\Utilman.exe C:\Utilman_backup.exe
copy C:\Windows\System32\cmd.exe C:\Windows\System32\Utilman.exe
```

Reiniciar normal → quitar USB.

### Acceso SYSTEM en pantalla login
```
1. Pantalla login Windows.
2. Click icono "Accesibilidad" (esquina inferior derecha).
3. Se abre consola con permisos SYSTEM.
```

### Crear admin temporal
```
net user TecnicoMPC Pass1234! /add
net localgroup Administradores TecnicoMPC /add
```

### Login con TecnicoMPC y arreglar la cuenta original
```
- Cerrar consola.
- Login con TecnicoMPC / Pass1234!
- Panel Control → Cuentas usuario → cambiar pass del usuario original.
```

### LIMPIEZA OBLIGATORIA
```
1. Volver a arrancar con USB Ventoy → instalador → Reparar → Solucionar problemas → cmd.

copy C:\Utilman_backup.exe C:\Windows\System32\Utilman.exe
del C:\Utilman_backup.exe

2. Reiniciar a Windows normal.

3. Borrar usuario temporal:

net user TecnicoMPC /delete
```

⚠️ Si no limpias Utilman → cualquiera con USB Windows puede entrar como admin. **NUNCA dejar el truco aplicado en el PC del cliente.**

---

## Atajos BIOS comunes (boot menu)

```
ASUS portátil           F8
ASUS sobremesa          F8 / Esc
HP                      F9 / Esc
Lenovo                  F12
Dell                    F12
Acer                    F12
MSI                     F11
Gigabyte                F12
ASRock                  F11
Intel NUC               F10
Microsoft Surface       Volume Down + Power
```

Si BIOS bloqueada con contraseña que el cliente no recuerda:
- Sacar disco con adaptador USB-SATA / NVMe.
- Conectarlo a portátil propio.
- Aplicar Lazesoft o chntpw sobre el disco extraído.
- Cobrar 45€ + posible recargo (lleva +30 min).

---

## Códigos de error frecuentes

```
"User cannot log on because the user profile cannot be loaded"
   → Perfil usuario corrupto. Reset password no soluciona. Crear usuario nuevo + pasar archivos.

"This account has been locked out for security reasons"
   → Cuenta bloqueada por demasiados intentos. Reset password también desbloquea (Lazesoft → Reset/Unlock incluye unlock).

"The password expiration date has been reached"
   → Contraseña expirada. Reset password también pone expiración a "nunca" (configurar después en Win).

"The trust relationship between this workstation and the primary domain failed"
   → Cuenta de dominio. NO es nuestro servicio.
```

---

## Lista verificación pre-cliente

- [ ] USB Lazesoft creado y verificado (boot test reciente).
- [ ] USB Ventoy rojo con krd_2024.iso (verificado).
- [ ] USB Windows instalador (W11 / W10) por si Método C.
- [ ] Pendrive 4GB+ vacío de repuesto.
- [ ] Adaptador USB-SATA / NVMe (BIOS bloqueada).
- [ ] Portátil propio cargado (soporte si la cosa se complica).
- [ ] Resguardo papel firmado.
- [ ] Esta chuleta impresa o accesible offline.

---

## Tiempo realista

- Lazesoft sin complicaciones: **30 min** + desplazamiento.
- chntpw vía krd: **45-60 min** + desplazamiento.
- Utilman trick + limpieza: **75-90 min**.
- BIOS bloqueada (sacar disco): añadir +30 min.
