# SocialAI - Sistema de Gestión de Pedidos 🤖

## Instrucciones de Entrega

### 1. Archivo JSON
El archivo `SocialAI.json` contiene el flujo de trabajo completo de n8n. Este archivo incluye:
- Configuración de todos los nodos
- Conexiones entre nodos
- Credenciales (referencias)
- Flujo de trabajo completo

### 2. Configuración de Parámetros

#### Credenciales Necesarias
1. **Telegram Bot**
   - Crear un bot en @BotFather
   - Obtener el token del bot
   - Configurar en n8n como "BotSocialAI"

2. **Google Sheets**
   - Crear una hoja de cálculo en Google Drive
   - Compartir con el email del servicio
   - ID de la hoja: `1s4AZR6pYoBqnKDtHVvSoDWo79e-slanGcws5szlZlGo`
   - Nombre de la hoja: "Hoja 1"

3. **Gmail**
   - Configurar cuenta de Gmail
   - Habilitar acceso de aplicaciones menos seguras
   - Configurar en n8n como "Gmail account"

4. **OpenAI**
   - Obtener API key de OpenAI
   - Configurar en n8n como "OpenAi account"
   - Modelo: gpt-4o-mini

5. **Pinecone**
   - Crear cuenta en Pinecone
   - Obtener API key
   - Configurar en n8n como "PineconeApi account"
   - Índice: "catalogo"
   - Namespace: "namespacecatalogo"

### 3. Pasos para Probar

1. **Importar el Flujo**
   - Abrir n8n
   - Ir a Workflows
   - Importar el archivo `SocialAI.json`

2. **Configurar Credenciales**
   - Configurar cada credencial mencionada arriba
   - Verificar que todas las conexiones estén activas

3. **Activar el Flujo**
   - Activar el workflow
   - Verificar que el webhook de Telegram esté activo

4. **Probar el Bot**
   - Abrir Telegram
   - Buscar el bot creado
   - Enviar un mensaje de prueba como:
     ```
     Hola, quiero ordenar:
     - 2 pizzas margarita
     - 1 coca cola
     ```

5. **Verificar Resultados**
   - Revisar la respuesta del bot
   - Verificar la hoja de Google Sheets
   - Comprobar el email de confirmación

### 4. Estructura de la Hoja de Google Sheets

La hoja debe tener las siguientes columnas:
- Producto
- Cantidad
- Horario
- Dirección
- Subtotal
- Cliente
- PrecioUnitario
- Total

### 5. Formato de Respuesta del Bot

El bot responderá con:
1. Confirmación de productos
2. Solicitud de dirección
3. Solicitud de horario
4. Resumen del pedido
5. Confirmación final

### 6. Solución de Problemas

Si el bot no responde:
1. Verificar que el workflow esté activo
2. Comprobar las credenciales
3. Revisar los logs de n8n
4. Verificar la conexión con Telegram

### 7. Notas Importantes

- El bot procesa un pedido a la vez
- Los precios se obtienen del catálogo en Pinecone
- Las confirmaciones se envían por email
- Los pedidos se registran en Google Sheets

---

Para cualquier problema o duda, contactar al desarrollador. 