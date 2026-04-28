# Recuperación de datos N2 (350-800€ + 60€ gestión)

> Tiempo realista: **5-15 días** (laboratorio partner)
> Bloque tarifa: **D — Recuperación de datos**
> Modalidad: derivación. NO se hace en MedicoPC.

---

## Qué es y qué NO es

**SÍ es:** derivación a un **laboratorio partner especializado** (sala limpia clase 100, herramientas PC-3000, Atola Insight, microscopios, equipo de soldadura BGA) cuando el disco del cliente:
- **No es accesible al sistema**: no detectado en BIOS, suena raro (clicks), tarjeta lógica quemada.
- **Daño físico**: cabezales pegados, rayas en plato, motor de giro muerto.
- **Daño electrónico**: PCB quemada por subida tensión, controlador SSD muerto.
- **Encriptado sin clave**: cliente perdió la clave de BitLocker / VeraCrypt y los datos son CRÍTICOS (raro pero pasa).

**Servicio MedicoPC en esto:** **gestión de la derivación**.
- Recoger disco del cliente.
- Diagnóstico previo gratuito (ver si es N1 o N2 realmente).
- Enviar al partner.
- Coordinar presupuesto del partner con el cliente.
- Recoger el disco + datos recuperados del partner.
- Entregar al cliente con factura clara (presupuesto partner + 60€ gestión MedicoPC).

**NO es:**
- ❌ **Recuperación N1 130€**: disco funcional, lógica software (PhotoRec, TestDisk). Eso lo hago yo.
- ❌ **Encriptado conocido (cliente tiene la clave)**: yo desencripto y recupero, es N1.
- ❌ **Disco con sectores defectuosos pero accesible**: sigue siendo N1, ddrescue + clasificador.
- ❌ **Desbloquear contraseña Windows**: eso es Recup pass 45€.

**Cómo se distingue N1 vs N2 en diagnóstico:**

| Síntoma | N1 (lo hago yo, 130€) | N2 (derivar, 350-800€ + 60€) |
|---------|----------------------|-----------------------------|
| Borrado accidental | ✅ | ❌ |
| Formateo accidental | ✅ | ❌ |
| Partición corrupta lógica | ✅ | ❌ |
| Disco accesible con sectores defectuosos (CDI ámbar) | ✅ | ❌ |
| Disco no detectado en BIOS | ❌ | ✅ |
| Disco hace clicks rítmicos | ❌ | ✅ |
| Disco no gira | ❌ | ✅ |
| Disco mojado / quemado | ❌ | ✅ |
| SSD con controlador muerto | ❌ | ✅ |
| Cabezal pegado al plato | ❌ | ✅ |

**Partners recomendados Madrid:**
- **OnRetrieval** (Madrid, sala limpia clase 100, presupuesto previo gratis): mi opción principal.
- **Recovery Labs** (Madrid, también con sala limpia): backup.
- **Salvar Tu Disco** (online, partners colaboradores): si los anteriores no pueden.

⚠️ **NO usar "supuestos especialistas" que cobran sin sala limpia**. Abrir un disco fuera de sala limpia mata los datos de forma irreversible.

---

## Antes (preparación)

### Confirmar por WhatsApp ANTES de la visita
- [ ] **Síntoma exacto**: ¿qué pasa al conectar? ¿hace ruido? ¿se detecta?
- [ ] **¿Cuánto valen los datos para él?** Si dice "no demasiado" → puede no merecer N2 (350-800€). Si dice "mi vida entera, fotos hijos, tesis doctorado, contabilidad empresa" → adelante.
- [ ] **Tipo disco**: HDD mecánico / SSD / USB pendrive / tarjeta SD.
- [ ] **Modelo y capacidad**.
- [ ] **¿Hay backup en otro sitio?** Si sí → quizá no merece N2.
- [ ] **Avisar precios** desde el principio: "Ojo, la recuperación N2 cuesta entre 350 y 800€ según gravedad, lo decide el laboratorio. No es servicio barato. ¿Sigues queriendo seguir?"

### Material en mochila
- [ ] **Adaptador USB-SATA** (probar disco mecánico).
- [ ] **Adaptador USB-NVMe** + **USB-M.2 SATA**.
- [ ] **Bolsa antiestática** para transportar disco al laboratorio.
- [ ] **Caja envío acolchada** (si hay que mandar por mensajería).
- [ ] **Resguardo papel CON CLÁUSULA expresa de derivación**.

### Resguardo papel — texto cláusula N2

```
RECUPERACIÓN DE DATOS N2 — CLÁUSULA OBLIGATORIA

Yo, [nombre cliente], con DNI [...], confirmo que MedicoPC va a entregar
el siguiente disco/dispositivo a un laboratorio partner especializado:

Equipo: [marca / modelo / capacidad / nº serie]

He sido informado de que:
1. El laboratorio entregará presupuesto previo en 24-72h. Si lo rechazo,
   solo pagaré 60€ gestión + posibles costes envío al laboratorio (~15€).
2. Si acepto, el coste final estará entre 350€ y 800€ según gravedad,
   más 60€ gestión MedicoPC.
3. La recuperación NO está garantizada al 100%. El laboratorio recupera
   lo que sea técnicamente posible y entregará informe.
4. El proceso tarda entre 5 y 15 días laborables.
5. NO podré reclamar a MedicoPC los datos no recuperados, ya que la
   derivación se hace bajo mi consentimiento y los daños del disco son
   anteriores a esta intervención.

Fecha: __/__/____
Firma cliente:
```

---

## Al llegar (diagnóstico previo)

- [ ] Foto del equipo cerrado.
- [ ] Confirmar visualmente el disco que da problemas.
- [ ] **Diagnóstico previo SIEMPRE**:
  1. Sacar el disco (sobremesa: cable; portátil: bahía 2.5"; SSD M.2: tornillo).
  2. Conectar a mi portátil con adaptador USB.
  3. ¿Se detecta?
     - **SÍ se detecta**: probablemente N1, no N2. Reagendar como N1 130€.
     - **NO se detecta**: pone estetoscopio en el disco mientras está enchufado:
       - Hace clicks rítmicos (HDD): cabezales tocando platos. **N2 confirmado**.
       - Suena pero no detectado: PCB quemada o firmware muerto. **N2**.
       - No gira nada (HDD): motor muerto o PCB sin alimentación. **N2**.
       - Silencio (SSD): controlador muerto. **N2**.
- [ ] Si N2 confirmado → resguardo firmado, llevar disco al laboratorio.

---

## Durante — Proceso derivación

### Paso 1 — Bolsa antiestática + transporte

1. Disco en bolsa antiestática.
2. Si voy en persona → llevo a OnRetrieval Madrid directamente.
3. Si envío → caja acolchada + bolsa antiestática + envío SEUR/MRW asegurado.

### Paso 2 — Entrega al partner

Aplica formulario del partner con:
- Datos cliente (nombre, teléfono, DNI).
- Datos MedicoPC como intermediario.
- Marca/modelo disco + nº serie.
- Síntomas.
- Datos prioritarios a recuperar (fotos / documentos / contabilidad / vídeos).
- Capacidad disco + estimación uso.
- Aceptación presupuesto previo gratuito.

### Paso 3 — Esperar presupuesto del partner (24-72h)

1. Partner manda presupuesto detallado por email:
   - Coste recuperación (350-800€ según gravedad).
   - Plazo entregable.
   - Lista de datos recuperables previa.
2. **Reenviar al cliente** AÑADIENDO los 60€ gestión MedicoPC al final.
3. Cliente decide:
   - **Acepta** → confirmar al partner, esperar entregable.
   - **Rechaza** → recoger disco SIN datos recuperados. Cobrar 60€ gestión + envío si hubo.

### Paso 4 — Recuperación en laboratorio

1. Tarda 5-15 días laborables según complejidad.
2. Mientras tanto, **mantener al cliente informado** semanal. Mensaje WhatsApp tipo:
   _"Hola [nombre], el laboratorio sigue trabajando. Plazo estimado [fecha]. Te aviso en cuanto tenga novedades."_

### Paso 5 — Entrega del partner

1. Partner devuelve:
   - Disco original (recuperable o no).
   - **Disco nuevo o USB con datos recuperados** (si éxito).
   - Informe de recuperación.
   - Factura del partner.

### Paso 6 — Entrega al cliente

1. Llamar al cliente para coordinar entrega.
2. Llevar a su casa o cliente recoge.
3. Conectar el disco/USB con datos recuperados a su PC delante de él, comprobar que se ven los archivos críticos (Fotos, Documentos).
4. Cobrar **factura del partner + 60€ gestión MedicoPC**.
5. Entregar:
   - Disco original.
   - Disco/USB con datos recuperados.
   - Informe partner (pdf o papel).
   - Factura MedicoPC con desglose: "Servicio recuperación N2 (laboratorio partner): Xeur. Gestión técnica MedicoPC: 60€."

---

## Al cerrar

- [ ] Cliente firma recibí.
- [ ] Lanzar `entrega.bat` → factura `MPC-2026-XXXX` con desglose claro.
- [ ] Recordar al cliente: **"Esto te ha pasado por no tener backup. Te recomiendo configurar OneDrive automático o disco externo. Te lo configuro yo en 30€ remota."** (oportunidad upsell legítimo).
- [ ] Frase cierre: **"Datos recuperados. NO hay garantía sobre los datos en sí (ya estaban dañados de origen) pero el laboratorio entrega lo que pudo extraer. Si necesitas configurar backup automático para que no vuelva a pasar, dímelo."**

---

## Errores frecuentes

_Pendiente actualizar tras 5 derivaciones reales._

Anticipados:
- **Cliente cree que disco está muerto pero es problema PC**: cargador no enchufado, cable SATA suelto, BIOS no detectaba pero el disco está OK. Diagnóstico previo MedicoPC ahorra al cliente la derivación injusta.
- **Cliente rechaza presupuesto partner**: volver a recoger disco + cobrar 60€ gestión + posible envío. NO regalar gestión.
- **Partner no recupera nada útil**: si se confirma 0 archivos importantes recuperados → 60€ gestión sigue siendo cobrable (no es culpa de MedicoPC). Pero ofrecer al cliente 30% descuento gestión (40€ en vez de 60€) por buena fe si la pérdida fue total. Decisión caso a caso.
- **Datos recuperados en USB partner pero cliente no sabe usar**: configurar copia a su disco interno cobrando 30€ remota o gratis 5 min como upsell de buena imagen.
- **Cliente cobra 800€ partner + 60€ gestión y se enfada**: por eso la cláusula firmada es OBLIGATORIA. Si firmó → contrato vinculante. Si no firmó → problema.

---

## Tiempo total

- Diagnóstico previo en visita: **30-45 min**.
- Transporte al laboratorio: **30-60 min** (en persona) o **24-48h** (envío).
- Recuperación partner: **5-15 días laborables**.
- Entrega final cliente: **30 min**.

**MedicoPC tiempo invertido total: 1.5-2.5h en visitas + tiempo de gestión emails (~30 min total).** El grueso del tiempo lo invierte el partner.

---

## Reglas críticas

🔴 **CLÁUSULA FIRMADA OBLIGATORIA** antes de llevar disco al partner.
🔴 **Diagnóstico previo SIEMPRE**, gratis, en visita: confirmar que es N2 y no N1. Ahorra dinero al cliente injusto.
🔴 **NUNCA abrir un disco mecánico fuera de sala limpia**. Fin de los datos.
🔴 **NUNCA prometer recuperación al cliente** ("seguro lo recuperan"). Promete: "el laboratorio recuperará lo que sea técnicamente posible".
🔴 **NO inventar precio** del partner. Esperar presupuesto real, sumar 60€ gestión, reenviar al cliente.
🔴 **60€ gestión SIEMPRE cobrable** salvo gesto comercial decidido caso a caso.
🔴 **Bolsa antiestática + caja acolchada** obligatorio en transporte. Disco más golpe = más datos perdidos.
🔴 **Mantener cliente informado semanal** durante el proceso. La impaciencia mata reputación.
🔴 **Backup post-recuperación**: ALWAYS recomendar al cliente que configure backup automático tras esto. Es la mejor lección.
🔴 **NO hacer N2 yo mismo en taller**. Sin sala limpia + PC-3000 = matas datos definitivamente. La derivación honesta es nuestra fortaleza.
