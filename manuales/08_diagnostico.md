# Diagnóstico + presupuesto (Gratis si reparamos · 25€ desplazamiento si no)

> Tiempo realista: **30-60 min** en domicilio
> Bloque tarifa: **A — Diagnóstico**
> Modalidad: **siempre a domicilio gratis** (es el momento de captar al cliente)

---

## Qué es y qué NO es

**SÍ es:** visita inicial al equipo del cliente para diagnosticar la avería, valorar coste y plazos, y decidir el servicio que se aplicará. Es el **hook de captación principal del negocio**. Si el cliente acepta presupuesto → no se cobra diagnóstico. Si rechaza presupuesto → se cobran 25€ por desplazamiento.

**NO es:** intervención. Aquí no se repara, no se formatea, no se abre el equipo más que para inspección visual. Si la avería es trivial (cable suelto, ajuste rápido <5 min) → arreglar en sitio cobrando mínimo 25€ desplazamiento o 30€ remota equivalente.

---

## Antes (preparación)

### Confirmar por WhatsApp antes de salir
- [ ] **Síntoma exacto** del problema. Pedirle que lo escriba con sus palabras.
- [ ] **¿Arranca o no arranca?** (Cambia el protocolo radicalmente.)
- [ ] **¿Cuándo empezó?** Hoy / esta semana / hace meses.
- [ ] **¿Pasó algo antes?** Subida tensión, golpe, derrame líquido, instalación de algo, actualización Windows.
- [ ] **Marca y modelo** del equipo (foto de la pegatina si no lo sabe).
- [ ] **Edad aproximada** del PC (para regla del 50%).
- [ ] **Dirección y franja horaria**.
- [ ] **Confirmación escrita por WhatsApp**: _"Diagnóstico gratuito si reparamos. 25€ desplazamiento si no aceptas presupuesto. ¿OK?"_ → guardar el "OK" del cliente.

### Material en mochila (obligatorio)
- [ ] **USB Arsenal MASTER** con scripts diagnóstico llegada (genera `DL-yymmdd-HHmmss`).
- [ ] **USB Ventoy rojo** (BACKUP) con: krd, GParted, Clonezilla, MemTest86, W10/W11 ISOs.
- [ ] **Portátil propio** para soporte.
- [ ] **Multímetro pequeño** (probar fuente sobremesa, batería portátil).
- [ ] **Clip enderezado** (puente PS_ON fuente sobremesa).
- [ ] **Destornilladores precision** (por si hay que abrir).
- [ ] **Linterna**.
- [ ] **Resguardo papel** + bolígrafo.

---

## Al llegar

- [ ] Saludo, cara amable, explicar **proceso 1 minuto**: "Voy a echar un vistazo, te explico qué le pasa y te paso presupuesto. Si te encaja seguimos, si no, son 25€ por la visita."
- [ ] Foto del equipo cerrado **antes de tocarlo**.
- [ ] Pedir al cliente que **enseñe el problema en directo** si arranca.

---

## Durante — Protocolo según síntoma

### Caso A — El equipo arranca pero va mal

#### Paso 1 — Lanzar diagnóstico llegada (USB Arsenal)
1. Enchufar USB MASTER.
2. Ejecutar `MEDICOPC.exe` → opción **"Diagnóstico llegada"**.
3. Genera carpeta `C:\MedicoPC_Logs_Cliente\DL-yymmdd-HHmmss\` con info sistema, eventos críticos, estado discos (CDI), procesos pesados, RAM, redes.
4. Mientras corre (3-5 min) → preguntar cosas al cliente.

#### Paso 2 — Inspección visual (en paralelo al script)
- [ ] Administrador de tareas → pestaña Procesos: ver % CPU/RAM/Disco. Si Disco al 100% constante → SSD viejo o malware.
- [ ] Configuración → Sistema → Almacenamiento: si <10% libre → causa probable de lentitud.
- [ ] Bandeja del sistema: cuántos iconos hay (cuanto más, peor).
- [ ] Programas instalados: ver bloatware obvio (toolbars, McAfee/Norton de preinstalación, "PC Cleaners", drivers chinos).
- [ ] Visor de eventos → últimos 7 días → eventos críticos.

#### Paso 3 — Revisar logs del DL-yymmdd
- **CDI** marca *Reallocated Sector Count >0* o estado *Precaución/Malo* → SSD/HDD muriendo.
- **MemoryDiagnostic** con errores → RAM defectuosa.
- **Eventos**: BSODs recientes, kernel panics.

#### Paso 4 — Diagnosticar y presupuestar

| Síntoma | Causa probable | Servicio | Precio |
|---------|----------------|----------|--------|
| HDD mecánico (no SSD) | Lentitud estructural | SSD pieza + 30€ MO + 50€ clonado | 145-180€ |
| Bloatware + posible malware | Software | Limpieza Completa | 80€ |
| Disco lleno >90% | Saturación | Limpieza Básica o Completa | 60-80€ |
| Windows 4+ años sin formatear | Sistema podrido | Formateo + Backup | 80€ |
| RAM 4GB en Windows 11 | Insuficiente | RAM pieza + 30€ MO | 70-160€ |
| GPU sucia / pasta seca (gaming) | Térmico | Limpieza+GPU o Pack Gaming | 120-150€ |
| Cliente quiere cambiar PC viejo entero | Migración | Migración | 100€ |

### Caso B — El equipo NO arranca

#### Paso 1 — Distinguir nivel de muerte
- ¿Se enciende? ¿Suena ventilador? ¿Se ven luces?
- ¿Llega a la pantalla del logo / BIOS?
- ¿Llega a la rueda de Windows?
- ¿Llega al login pero peta antes/después?

Cada nivel descarta un componente.

#### Paso 2 — Protocolo "no arranca" 8 pasos

1. **Comprobar enchufe.** Sí, suena de coña pero un 5% de "no arranca" es enchufe suelto, regleta apagada o cable de red sin clavar al PC.
2. **Comprobar fuente** (sobremesa): puente PS_ON con clip → ventiladores giran. Si no giran → fuente muerta. Cambio fuente desde 45€ MO + pieza.
3. **Comprobar BIOS POST**: pulsar power, ver si se enciende algo en pantalla. Si pantalla negra pero PC enciende → problema GPU, RAM o monitor.
4. **Reset CMOS**: quitar pila CR2032 30 segundos, volver a poner. A veces revive.
5. **Quitar GPU dedicada** (sobremesa): si la CPU tiene iGPU, conectar monitor a salida de placa base. Si arranca → GPU muerta.
6. **Quitar RAM y dejar solo 1 módulo** en slot principal: si arranca → RAM defectuosa o slot defectuoso. Probar todos los módulos uno a uno y todos los slots.
7. **Sacar disco**: arrancar sin disco, ver si llega a BIOS. Si BIOS aparece → disco muerto (no es la placa). Si sigue sin BIOS → es placa o CPU.
8. **Si nada de esto → problema placa base o CPU**: derivar a presupuesto cerrado de PC nuevo (regla del 50%).

#### Paso 3 — Casos especiales no arranca
- **Pantalla azul recurrente con código** → apuntar el código BSOD, buscar significado.
- **Suena pitido al encender** → códigos beep (1 corto OK, 1 largo + 2 cortos = GPU, 3 cortos = RAM, depende de la BIOS).
- **Se enciende y apaga en bucle** → fuente fallando bajo carga, o cortocircuito en placa.
- **Pantalla Windows con error 0xC0000... + Recovery** → BCD roto. Reparar arranque desde USB W10/W11 (15-20 min) o formatear.
- **BitLocker pidiendo clave de recuperación** → cliente debe recuperarla de [account.microsoft.com](https://account.microsoft.com). Si no la tiene → datos perdidos, derivar a Recup N2.
- **Cargador no entra / DC jack roto** (portátil): pieza 15€ + MO según equipo (45-80€).
- **Líquido derramado**: ⚠️ apagar inmediatamente, NO encender. Derivar a partner microsoldadura. NO es nuestro servicio.

### Caso C — Avería física obvia
- Pantalla rota portátil → cambio pantalla desde 90€ + pieza.
- Bisagra rota → bisagras desde 50€ + pieza.
- Teclado con teclas rotas → teclado desde 70€ + pieza.
- Batería hinchada → ⚠️ urgente cambio batería desde 80€ + pieza. NO seguir usando.

---

## Al cerrar

### Caso A — Cliente acepta presupuesto

- [ ] Decirle precio en alto, claro y cerrado: "**80€** Limpieza Completa, te lo dejo nuevo. Tiempo: hora y media. ¿Lo hago ahora o lo recogemos para hacerlo en taller?"
- [ ] **Modalidad por defecto: taller** en servicios largos. Si quiere domicilio +25€.
- [ ] Si recogemos → resguardo firmado con descripción equipo + número de serie + estado físico + qué se va a hacer + fecha entrega estimada.
- [ ] Foto del equipo en su estado actual con el cliente delante.
- [ ] **NO cobrar 25€ desplazamiento** porque va a haber servicio.
- [ ] Programar siguiente visita / entrega.

### Caso B — Cliente NO acepta presupuesto

- [ ] Sin discutir. Dejarle libre. Posible vuelta más adelante.
- [ ] Cobrar **25€** Bizum o efectivo por desplazamiento.
- [ ] Lanzar `entrega.bat` → factura `MPC-2026-XXXX` con concepto "Diagnóstico técnico domicilio · No acepta presupuesto".
- [ ] Frase: **"Si cambias de opinión en 30 días, los 25€ se descuentan del servicio que pidas."**

### Caso C — Avería trivial resuelta en sitio (<10 min)

- [ ] Si es trivial (cable suelto, ajuste, tecla destrabar, monitor mal conectado) → arreglar en sitio.
- [ ] Cobrar mínimo **25€** desplazamiento. NO regalar nunca.
- [ ] Frase: "Bueno, era esto. Son 25€ por la visita y reparación rápida. Hecho."

---

## Errores frecuentes

_Pendiente actualizar tras 5 visitas reales._

Anticipados:
- **Cliente confunde diagnóstico con asesoría compra**: redirigir a chat WhatsApp gratis (asesoría YA NO es servicio cobrable).
- **Cliente exige reparación en sitio cuando es servicio largo**: explicar que en taller sale igual de precio y mejor calidad. Si insiste → +25€ recargo domicilio.
- **Cliente rechaza presupuesto y se enfada por los 25€**: por eso la confirmación WhatsApp por escrito antes de salir es obligatoria.
- **Avería intermitente no reproducible en 60 min**: cerrar diagnóstico con "necesita pruebas en taller". Cobrar 25€ desplazamiento si no quiere llevar a taller.

---

## Tiempo total

- Diagnóstico simple PC arranca: **30-45 min** + desplazamiento.
- Protocolo no arranca completo: **45-60 min**.
- Arreglo trivial en sitio: **30 min** total.

---

## Reglas críticas

🔴 **AVISAR SIEMPRE por WhatsApp antes de salir** que el diagnóstico es gratis si repara y 25€ si rechaza presupuesto. **Confirmación escrita por su parte** antes de coger el coche.
🔴 **Foto del equipo al llegar y al irse** si lo abro.
🔴 **NO regalar reparaciones triviales**. Mínimo 25€. Educa al cliente, valora tu tiempo.
🔴 **Si la avería es física complicada (líquido, golpe fuerte, microsoldadura, BGA)** → derivar honestamente. NO inventar.
🔴 **NO presupuestar a la baja para captar y luego subir.** Honesto desde el principio.
🔴 **Si tras 8 pasos del protocolo "no arranca" no localizas la causa** → es placa o CPU, derivar a PC nuevo (regla del 50%).
🔴 **NUNCA empezar a reparar sin presupuesto firmado/aceptado por escrito** (WhatsApp vale como prueba).
