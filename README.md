# 🤖 Bot del Arancel del Profesional del Derecho — Honduras

Bot de Telegram para consultar los honorarios mínimos establecidos por el **Colegio de Abogados de Honduras (CAH)** en su Arancel del Profesional del Derecho, publicado en La Gaceta N° 34,403 el 29 de julio de 2017.

---

## 📋 Funcionalidades

- 🔍 **Búsqueda inteligente** de trámites por palabras clave (ej: "alimentos", "divorcio", "amparo")
- 📂 **Navegación por categorías**: Familia, Civil, Penal, Constitucional, Laboral, Administrativo
- 🔢 **Calculadora de honorarios** con tablas progresivas y porcentajes
- 📥 **Enlace para descargar** el Arancel vigente en PDF
- ✅ Honorarios mínimos según el Arancel CAH 2017

---

## 🚀 GUÍA DE DESPLIEGUE PASO A PASO

### PASO 1 — Crear el Bot con @BotFather

1. Abre Telegram y busca **@BotFather**
2. Envía el comando `/newbot`
3. Escribe el **nombre** del bot (ej: `Arancel Abogados Honduras`)
4. Escribe el **username** del bot (debe terminar en "bot", ej: `ArancelHNbot`)
5. **Copia el TOKEN** que te da BotFather. Tiene el formato: `123456789:ABCDefghIJKlmnopQRSTuvwxyz`
6. Guarda ese token, lo necesitarás en los siguientes pasos.

> ⚙️ **Opcional**: Configura el bot con estos comandos en BotFather:
> - `/setdescription` — Descripción del bot
> - `/setabouttext` — Texto "Acerca de"  
> - `/setcommands` — Para listar los comandos disponibles:
>   ```
>   start - Menú principal
>   buscar - Buscar un trámite (ej: /buscar alimentos)
>   calcular - Calculadora de honorarios
>   pdf - Descargar Arancel vigente
>   menu - Volver al menú
>   help - Ayuda
>   ```

---

### PASO 2 — Subir el código a GitHub

1. **Crea una cuenta** en [github.com](https://github.com) si no tienes una.

2. **Crea un repositorio nuevo**:
   - Click en el botón verde **"New"** o **"+"** > **New repository**
   - Nombre: `arancel-honduras-bot`
   - Descripción: `Bot de Telegram para consultar el Arancel de Abogados de Honduras`
   - Marca como **Público** (necesario para el plan gratuito de Railway)
   - Click en **"Create repository"**

3. **Sube los archivos** al repositorio. Tienes dos opciones:

   **Opción A — GitHub Web (más fácil):**
   - En la página del repositorio, click en **"uploading an existing file"**
   - Arrastra y suelta los archivos: `bot.js`, `package.json`, `railway.toml`, `.gitignore`, `.env.example`
   - Click en **"Commit changes"**

   **Opción B — Terminal (si tienes Git instalado):**
   ```bash
   # Navega a la carpeta del proyecto
   cd arancel-bot
   
   # Inicializa Git
   git init
   
   # Agrega todos los archivos
   git add .
   
   # Primer commit
   git commit -m "🚀 Primer despliegue del bot"
   
   # Conecta con tu repositorio de GitHub (reemplaza TU_USUARIO)
   git remote add origin https://github.com/TU_USUARIO/arancel-honduras-bot.git
   
   # Sube el código
   git push -u origin main
   ```

---

### PASO 3 — Desplegar en Railway

1. **Crea una cuenta** en [railway.app](https://railway.app) usando tu cuenta de GitHub.

2. **Crea un nuevo proyecto**:
   - Click en **"New Project"**
   - Selecciona **"Deploy from GitHub repo"**
   - Autoriza Railway para acceder a tu GitHub
   - Selecciona el repositorio **`arancel-honduras-bot`**

3. **Configura las variables de entorno**:
   - En tu proyecto de Railway, ve a la pestaña **"Variables"**
   - Agrega las siguientes variables:

   | Variable | Valor |
   |----------|-------|
   | `BOT_TOKEN` | El token que te dio @BotFather |
   | `NODE_ENV` | `production` |
   | `WEBHOOK_URL` | Lo agregas DESPUÉS del despliegue (ver paso 4) |

4. **Obtén la URL de Railway** (para el Webhook):
   - Ve a la pestaña **"Settings"** de tu servicio
   - En la sección **"Domains"**, click en **"Generate Domain"**
   - Obtendrás una URL como: `https://arancel-bot-production.up.railway.app`
   - **Cópiala** y regresa a **"Variables"**
   - Agrega la variable `WEBHOOK_URL` con esa URL (sin barra al final)

5. **Haz el despliegue**:
   - Railway lo hace automáticamente cuando detecta el código
   - Si no se inicia solo, ve a **"Deployments"** y click en **"Deploy"**
   - Verifica en los **Logs** que aparezca: `✅ Webhook configurado`

---

### PASO 4 — Verificar que funciona

1. Abre Telegram y busca tu bot por su username
2. Envía `/start`
3. Deberías ver el menú principal del Arancel

---

## 🖥️ Desarrollo Local

Si quieres probar el bot en tu computadora antes de subirlo:

```bash
# 1. Instala las dependencias
npm install

# 2. Copia el archivo de ejemplo de variables
cp .env.example .env

# 3. Edita .env y agrega tu BOT_TOKEN
# (deja WEBHOOK_URL en blanco para usar modo polling)

# 4. Inicia el bot
npm start

# O para desarrollo con reinicio automático:
npm run dev
```

---

## 📁 Estructura del Proyecto

```
arancel-bot/
├── bot.js           # 🤖 Código principal del bot (todo en un archivo)
├── package.json     # 📦 Dependencias del proyecto
├── railway.toml     # 🚂 Configuración de Railway
├── .env.example     # 🔑 Ejemplo de variables de entorno
├── .gitignore       # 🚫 Archivos a ignorar en Git
└── README.md        # 📖 Este archivo
```

---

## 🔧 Actualizar el Bot

Cuando necesites hacer cambios:

1. Modifica los archivos en tu computadora
2. Sube los cambios a GitHub:
   ```bash
   git add .
   git commit -m "Descripción del cambio"
   git push
   ```
3. Railway detectará el cambio automáticamente y redesplegará el bot.

---

## 📋 Materias Cubiertas

| Materia | Artículos |
|---------|-----------|
| ⚖️ Derecho de Familia | Arts. 59–74 |
| 🏛️ Civil y Mercantil | Arts. 38–57 |
| ⚠️ Derecho Penal | Arts. 81–91 |
| 📜 Constitucional | Arts. 30–37 |
| 👷 Derecho Laboral | Arts. 75–80 |
| 🏢 Derecho Administrativo | Arts. 58, 99–100 |
| 📋 Honorarios Generales | Arts. 101–113 |

---

## ⚖️ Aviso Legal

Este bot es una herramienta de referencia. Los honorarios mostrados son los **mínimos establecidos** por el Arancel del CAH (2017). Los valores pueden ajustarse según el Art. 131 (incremento del 10% cada 10 años). Siempre consulta el Arancel oficial publicado en La Gaceta N° 34,403.

---

## 💡 Créditos

**Idea y desarrollo:** Abg. Brayan Fernando Padilla Rodríguez

---

## 📞 Fuente Oficial

- **Colegio de Abogados de Honduras**: [www.cah.hn](https://www.cah.hn)
- **La Gaceta**: [www.gaceta.hn](https://www.gaceta.hn)
- **Publicación**: La Gaceta N° 34,403 — 29 de julio de 2017
