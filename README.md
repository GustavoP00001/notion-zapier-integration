# notion-zapier-integration

##  Tech Stack & Herramientas

* **Orquestador:** Zapier
* **Origen de Datos (Trigger):** Notion API (*New Data Source Item*)
* **Canales de Salida (Actions):** Gmail API (*Send Email*) & Slack API (*Send Channel Message*)
* **Control de Versiones:** JSON Export (`notion-gmail-slack-zap.json`)

---

##  Características Técnicas

* **Payload Mapping Dinámico:** Mapeo automático de propiedades de Notion (ej. `{{Title}}`, `{{URL}}`) hacia la estructura del correo en Gmail y los mensajes de canal en Slack.
* **Orquestación Multi-Canal:** Disparo secuencial de notificaciones por email y mensajes en tiempo real ante la creación de un nuevo registro.
* **Monitoreo Continuo (Polling):** Polling automático sobre la base de datos de Notion para la detección de nuevos eventos.
* **Ejecución y Depuración Manual:** Soporte para ejecuciones on-demand mediante el motor de pruebas (*Run*) para diagnóstico y validación inmediata.


## Cómo Importar y Reproducir este Proyecto

### Requisitos previos

- Una cuenta de **Zapier**, otra de **Notion**, **Gmail** y un workspace de **Slack** (todas con tus propios datos).
- Una base de datos de Notion con una propiedad de tipo **Persona** (*Person*) que tenga un mail asociado. De ahí sale el destinatario del correo.

### Pasos

1. **Descargar el archivo de configuración**
   - Descargá o cloná el archivo `notion-gmail-slack-zap.json` de este repositorio.

2. **Importar el workflow en Zapier**
   - Iniciá sesión en tu cuenta de [Zapier](https://zapier.com).
   - En el panel principal (**Zaps**), buscá la opción **Import / Upload Zap** y cargá el archivo `notion-gmail-slack-zap.json`.
   - Si no ves esa opción, puede depender de tu plan o de la interfaz de Zapier en ese momento.

3. **Conectar tus cuentas y configurar cada paso**
   - **Notion (Trigger):** conectá tu cuenta de Notion y elegí tu base de datos (la que tiene la propiedad *Persona* con mail).
   - **Gmail (Action 1):** conectá tu cuenta de Gmail y poné tu casilla en el campo **From**. El destinatario (**To**) se toma automáticamente de la propiedad *Persona* del registro de Notion, así que no hace falta escribirlo.
   - **Slack (Action 2):** conectá tu workspace y elegí un canal de prueba (por ejemplo `#general`).

4. **Activar el Zap**
   - Los pasos de Gmail y Slack pueden venir **pausados** en el archivo importado.
   - Probá cada paso con **Test step** y, cuando todos funcionen, **publicá / activá** el Zap.

5. **Probar de punta a punta**
   - Con el Zap activado, creá un registro nuevo en tu base de Notion y asignale una persona con mail.
   - Verificá que llegue el correo a esa casilla y que aparezca el mensaje automático en el canal de Slack.

### Si algo no funciona
- **No llega el mail:** revisá que el registro de Notion tenga una persona asignada con mail y que el Zap esté activado.
- **Zapier pide reconectar una cuenta:** es lo esperado. Las conexiones no se incluyen en el archivo y cada persona usa las suyas.
- **No aparece tu base de Notion:** verificá que hayas dado acceso a esa base a la integración de Notion durante la conexión.
- **No llega el mail:** revisá que el registro de Notion tenga una persona asignada con mail y que el Zap esté activado.
- **Zapier pide reconectar una cuenta:** es lo esperado. Las conexiones no se incluyen en el archivo y cada persona usa las suyas.
- **No aparece tu base de Notion:** verificá que hayas dado acceso a esa base a la integración de Notion durante la conexión.
