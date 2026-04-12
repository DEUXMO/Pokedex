Proceso Técnico de Despliegue

Información General
- Servicio: Azure Static Web Apps
- Método: Despliegue desde GitHub
- Fecha de despliegue: 12/04/2026}

----

Paso 1: Preparar el código fuente en el repositorio  

pokedex/  
├── index.html -> (página principal)  
├── css/   
│  └── styles.css -> (estilos de la aplicación)  
├── js/  
│ └── app.js -> (lógica de la aplicación)  
└── assets/ -> (imágenes, fuentes, etc.)  


Acciones realizadas:  
  1. Crear archivos HTML, CSS y JS de la aplicación PokeDex  
  2. Subir archivos al repositorio GitHub  
  3. Verificar que `index.html` esté en la raíz del repositorio  

---
Paso 2: Crear recurso en Azure Portal

  2.1 Acceso al portal  
    - URL: https://portal.azure.com  
    - Iniciar sesión con cuenta verificada de Azure for Students  
    
  2.2 Crear Static Web App  
    1. Click en "Create a resource" (+)  
    2. Buscar: "Static Web App"  
    3. Click en "Create"  

  2.3 Configuración básica:
  | Campo | Valor |
  |:---|:---|
  | Subscription | Azure for Students |
  | Resource Group | Crear nuevo: `rg-pokedex` |
  | Name | `pokedex-app` |
  | Region | East US 2 (o la más cercana) |
  | Plan | Free |

  2.4 Configuración de GitHub:
  | Campo | Valor |
  |:---|:---|
  | Source | GitHub |
  | Organization | DEUXMO |
  | Repository | Pokedex |
  | Branch | main |

  2.5 Configuración de build:
  | Campo | Valor |
  |:---|:---|
  | Build Presets | Custom |
  | App location | `/` (raíz del repositorio) |
  | Output location | (dejar vacío para HTML estático) |

---

Paso 3: Desplegar aplicación

  3.1 Revisar y crear  
    1. Click en "Review + create"  
    2. Validar configuración  
    3. Click en "Create"  

  3.2 Esperar despliegue  
    - Tiempo estimado: 2-5 minutos  
    - Azure creará automáticamente:  
      - Static Web App resource  
      - GitHub Actions workflow (archivo `.github/workflows/azure-static-web-apps-*.yml`)

---

Paso 4: Obtener URL pública

  4.1 Verificar despliegue exitoso  
    1. Ir a recurso creado en Azure Portal  
    2. Sección "Overview"  
    3. Copiar URL generada: `https://[nombre-aleatorio].azurestaticapps.net`  
  
  4.2 Validar funcionamiento  
    - Abrir URL en navegador  
    - Verificar que la PokeDex carga correctamente  
    - Revisar consola del navegador (F12) por errores  

---

 Posibles errores y soluciones

| Error | Causa | Solución |
|:---|:---|:---|
| 404 en página principal | `index.html` no está en raíz | Mover archivo a raíz del repo |
| Build falla en GitHub Actions | Estructura incorrecta | Revisar `app_location` en configuración |
| Recursos no cargan (CSS/JS) | Rutas relativas incorrectas | Usar rutas `./css/styles.css` |
| HTTPS no activo | Configuración de dominio | Azure Static Web Apps incluye HTTPS por defecto |

---

Validaciones post-despliegue

- [ ] Aplicación accesible desde URL pública
- [ ] Sin errores 404/500
- [ ] Sin errores en consola del navegador
- [ ] HTTPS activo
- [ ] Escaneo en securityheaders.com realizado
