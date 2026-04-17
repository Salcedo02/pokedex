# 🎮 PokeDex — Despliegue en la Nube con Azure

> Aplicación web que permite explorar las 386 especies de Pokémon de la primera y segunda generación, con información detallada sobre sus características, tipos y habilidades.

---

## 🌐 URL Pública
🔗 [https://calm-mud-0c3cc6210.7.azurestaticapps.net](https://calm-mud-0c3cc6210.7.azurestaticapps.net)

---

## ☁️ Creación de cuenta en Azure for Students

### 1️⃣ Ingresar al portal de Azure for Students
Visitar [azure.microsoft.com/es-es/free/students](https://azure.microsoft.com/es-es/free/students) y hacer clic en **"Activar ahora"**.

### 2️⃣ Autenticación institucional
Iniciar sesión con el correo institucional de la universidad. Azure verifica automáticamente el estatus de estudiante a través del dominio del correo.

### 3️⃣ Verificación de elegibilidad
Completar el formulario de verificación estudiantil. No se requiere tarjeta de crédito.

### 4️⃣ Activación de beneficios
Una vez verificado, Azure for Students otorga:
- **$100 USD** en créditos gratuitos
- Acceso a más de 25 servicios gratuitos
- Validez de 12 meses

### 5️⃣ Acceso al portal
Ingresar a [portal.azure.com](https://portal.azure.com) con las credenciales institucionales para comenzar a usar los servicios.

---

## 🛠️ Tecnologías utilizadas
- **Frontend:** Angular 14
- **Hosting:** Azure Static Web Apps
- **CI/CD:** GitHub Actions
- **Seguridad:** HTTP Security Headers (calificación A en securityheaders.com)

---

## 🔒 Seguridad
La aplicación implementa los siguientes encabezados HTTP de seguridad:

| Encabezado | Propósito |
|---|---|
| Content-Security-Policy | Previene ataques XSS |
| Strict-Transport-Security | Obliga el uso de HTTPS |
| X-Content-Type-Options | Evita detección automática de tipos |
| X-Frame-Options | Previene clickjacking |
| Referrer-Policy | Minimiza fuga de información |
| Permissions-Policy | Controla acceso a APIs del navegador |

---

## 👨‍💻 Autor
**Camilo Salcedo** — Ingeniería en Sistemas
