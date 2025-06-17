# SocialAI - Sistema de Gestión de Pedidos Inteligente 🤖

## Descripción
SocialAI es un sistema avanzado de gestión de pedidos que automatiza el proceso de recepción, procesamiento y confirmación de pedidos a través de Telegram. Utiliza inteligencia artificial para interactuar con los clientes de forma natural y eficiente, procesando pedidos y gestionando la información de manera automatizada.

## Características Principales 🚀

### 1. Interfaz Conversacional
- Bot de Telegram para interacción con clientes
- Procesamiento de lenguaje natural con GPT-4
- Interfaz amigable y natural
- Soporte para múltiples productos por pedido

### 2. Gestión de Pedidos
- Extracción automática de detalles del pedido
- Validación de productos y cantidades
- Cálculo automático de subtotales y totales
- Gestión de direcciones y horarios de entrega

### 3. Integración con Google Sheets
- Registro automático de pedidos
- Actualización en tiempo real
- Estructura de datos organizada
- Fácil acceso a historial de pedidos

### 4. Notificaciones Automáticas
- Confirmación de pedidos por email
- Formato profesional y detallado
- Inclusión de todos los detalles del pedido
- Notificaciones instantáneas

## Tecnologías Utilizadas 💻

- **n8n**: Automatización de flujos de trabajo
- **OpenAI GPT-4**: Procesamiento de lenguaje natural
- **Google Sheets API**: Gestión de datos
- **Telegram Bot API**: Interfaz de usuario
- **Gmail API**: Envío de notificaciones
- **Pinecone**: Almacenamiento vectorial para catálogo

## Instrucciones de Entrega y Configuración

### 1. Archivos del Proyecto
- `SocialAI.json`: Flujo de trabajo principal de n8n
- `SocialAIRAG.json`: Flujo de trabajo para RAG (Retrieval Augmented Generation)
- `README.md`: Este archivo de documentación

### 2. Configuración de Credenciales

#### 2.1 Telegram Bot
1. Abrir Telegram y buscar @BotFather
2. Crear nuevo bot con el comando `/newbot`
3. Guardar el token proporcionado
4. En n8n:
   - Ir a Credentials
   - Crear nueva credencial "BotSocialAI"
   - Pegar el token del bot

#### 2.2 Google Sheets
1. Crear nueva hoja de cálculo en Google Drive
2. Compartir con el email del servicio de n8n
3. Copiar el ID de la hoja de la URL
4. En n8n:
   - Configurar credencial de Google Sheets
   - ID de la hoja: `1s4AZR6pYoBqnKDtHVvSoDWo79e-slanGcws5szlZlGo`
   - Nombre: "Hoja 1"

#### 2.3 Gmail
1. Configurar cuenta de Gmail
2. Habilitar acceso de aplicaciones menos seguras
3. En n8n:
   - Crear credencial "Gmail account"
   - Configurar OAuth2

#### 2.4 OpenAI
1. Crear cuenta en OpenAI
2. Generar API key
3. En n8n:
   - Crear credencial "OpenAi account"
   - Configurar API key
   - Modelo: gpt-4o-mini

#### 2.5 Pinecone
1. Crear cuenta en Pinecone
2. Crear índice "catalogo"
3. En n8n:
   - Crear credencial "PineconeApi account"
   - Configurar API key
   - Índice: "catalogo"
   - Namespace: "namespacecatalogo"

### 3. Pasos para Implementar

#### 3.1 Importar Flujos de Trabajo
1. Abrir n8n
2. Ir a Workflows
3. Importar `SocialAI.json`
4. Importar `SocialAIRAG.json`

#### 3.2 Configurar Nodos
1. **Telegram Trigger**
   - Verificar webhook
   - Activar el nodo

2. **AI Agent**
   - Verificar conexión con OpenAI
   - Comprobar prompt

3. **Extraer pedido_json**
   - Verificar funciones JavaScript
   - Comprobar regex

4. **Hoja Pedidos**
   - Verificar ID de hoja
   - Comprobar mapeo de columnas

5. **Formatear Email**
   - Verificar plantilla HTML
   - Comprobar variables

#### 3.3 Activar el Sistema
1. Activar ambos workflows
2. Verificar webhooks
3. Probar conexiones

### 4. Estructura de Datos

#### 4.1 Google Sheets
Columnas requeridas:
```
A: Producto
B: Cantidad
C: Horario
D: Dirección
E: Subtotal
F: Cliente
G: PrecioUnitario
H: Total
```

#### 4.2 Formato de Mensajes
1. **Mensaje de Cliente**:
```
Hola, quiero ordenar:
- 2 Hodlmoser x 700ml
- 1 Agua BLOCK 500cc
```

2. **Respuesta del Bot**:
```
📋 Resumen del pedido
• Hodlmoser x 700ml
  - Cantidad: 2
  - Precio unitario: $19.575,00
  - Subtotal: $39.150,00

• Coca Cola
  - Cantidad: 1
  - Precio unitario: $570.00
  - Subtotal: $570.00

💰 Total del pedido: $39.720,00
📍 Dirección: [dirección]
⏰ Horario: [horario]
```

### 5. Solución de Problemas

#### 5.1 Verificación de Errores
1. **Bot no responde**:
   - Verificar webhook de Telegram
   - Comprobar credenciales
   - Revisar logs de n8n

2. **Error en extracción**:
   - Verificar formato del mensaje
   - Comprobar regex
   - Revisar logs de JavaScript

3. **Error en Google Sheets**:
   - Verificar permisos
   - Comprobar ID de hoja
   - Revisar formato de datos

#### 5.2 Logs y Monitoreo
1. Revisar logs de n8n
2. Monitorear webhooks
3. Verificar conexiones
4. Revisar errores en consola

### 6. Mantenimiento

#### 6.1 Actualizaciones
- Revisar APIs mensualmente
- Actualizar tokens trimestralmente
- Mantener dependencias actualizadas

#### 6.2 Backups
- Exportar workflows regularmente
- Guardar configuraciones
- Mantener copias de credenciales

### 7. Notas Importantes
- El bot procesa un pedido a la vez
- Los precios se obtienen del catálogo en Pinecone
- Las confirmaciones se envían por email
- Los pedidos se registran en Google Sheets
- Mantener el catálogo actualizado en Pinecone
