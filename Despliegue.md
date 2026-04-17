# 📦 Despliegue de PokeDex en Azure Static Web Apps

---

## 📋 Prerequisitos
- Cuenta en Azure for Students activa
- Git instalado en el computador
- Node.js y npm instalados
- Repositorio en GitHub

---

## 🚀 Proceso de Despliegue

### Paso 1 — Clonar el repositorio del profesor
```bash
git clone https://github.com/rcuello/ac4dem1a.git
cd ac4dem1a/sistemas-distribuidos/poke-dex-lab/source/pokedex-angular
```

### Paso 2 — Instalar dependencias y compilar
```bash
npm install --ignore-scripts
npm run build
```

### Paso 3 — Crear repositorio propio en GitHub
Crear un repositorio llamado `pokedex` en GitHub y subir el código:
```bash
git clone https://github.com/Salcedo02/pokedex.git
xcopy /E /I /Y "ruta-origen" "ruta-destino"
git add .
git commit -m "Agregar codigo PokeDex"
git push origin master
```

### Paso 4 — Crear Azure Static Web App
1. Ingresar a [portal.azure.com](https://portal.azure.com)
2. Buscar **"Static Web Apps"** y hacer clic en **"Crear"**
3. Configurar:
   - **Suscripción:** Azure for Students
   - **Grupo de recursos:** pokedex-app_group
   - **Nombre:** pokedex-app
   - **Plan:** Free
   - **Origen:** GitHub → Salcedo02/pokedex → master
   - **App location:** `poke-dex-lab/source/pokedex-angular/dist/pokedex-angular`
   - **Output location:** (vacío)

### Paso 5 — Configurar el token de despliegue
1. En Azure, copiar el **token de implementación**
2. En GitHub → Settings → Secrets → Actions → New secret:
   - **Name:** `AZURE_STATIC_WEB_APPS_API_TOKEN_CALM_MUD_0C3CC6210`
   - **Value:** (pegar el token)

### Paso 6 — Configurar encabezados de seguridad
Crear el archivo `staticwebapp.config.json` en la carpeta raíz del deploy:
```json
{
  "globalHeaders": {
    "Content-Security-Policy": "default-src 'self' 'unsafe-inline' 'unsafe-eval' data: https: blob:;",
    "Strict-Transport-Security": "max-age=31536000; includeSubDomains",
    "X-Content-Type-Options": "nosniff",
    "X-Frame-Options": "SAMEORIGIN",
    "Referrer-Policy": "no-referrer",
    "Permissions-Policy": "camera=(), microphone=(), geolocation=()"
  }
}
```

---

## ⚠️ Errores encontrados y soluciones

| Error | Causa | Solución |
|---|---|---|
| `deployment_token was not provided` | Token incorrecto en el secret | Actualizar el secret con el token correcto de Azure |
| `Could not detect any platform` | Azure no encontraba el código compilado | Subir el directorio `dist` al repositorio |
| `No matching Static Web App was found` | Token del app anterior | Crear nuevo secret con token del app correcto |
| Imágenes no cargaban | Carpeta `dist` en `.gitignore` | Eliminar `/dist` del `.gitignore` y subir el build |
| Interfaz dañada con CSP | Policy muy restrictiva | Relajar el Content-Security-Policy |

---

## ✅ Resultado final
- **URL:** [https://calm-mud-0c3cc6210.7.azurestaticapps.net](https://calm-mud-0c3cc6210.7.azurestaticapps.net)
- **Calificación de seguridad:** A en securityheaders.com
- **HTTPS:** Activo por defecto en Azure Static Web Apps
- **CI/CD:** Automático con GitHub Actions

---

## 🔐 Escaneo de seguridad
![Security Headers](https://img.shields.io/badge/Security-A-brightgreen)

Resultado obtenido en [securityheaders.com](https://securityheaders.com):
- ✅ Strict-Transport-Security
- ✅ Referrer-Policy  
- ✅ X-Content-Type-Options
- ✅ Content-Security-Policy
- ✅ X-Frame-Options
- ✅ Permissions-Policy
