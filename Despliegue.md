
# Proceso Técnico de Despliegue PokeDex Angular

## Información General
- **Servicio:** Azure Static Web Apps
- **Método:** Despliegue con compilación automática (GitHub Actions)
- **Fecha de despliegue:** 15/04/2026
- **URL pública:** https://lemon-meadow-025a28c0f7.azurestaticapps.net

---

## Paso 1: Preparar código fuente en repositorio

### Estructura del proyecto subido
Se subió el código fuente completo de la aplicación Angular desarrollada por Keiler Mora:

# Estructura 

Pokedex/  
├── .github/workflows/ (Workflow de GitHub Actions)   
├── src/ (Código fuente Angular)   
│ ├── app/   
│ ├── assets/   
│ └── environments/   
├── angular.json (Configuración de Angular)   
├── package.json (Dependencias del proyecto)   
├── package-lock.json   
├── tsconfig.json (Configuración TypeScript)   
├── .gitignore   
├── staticwebapp.config.json (Configuración Azure)   
├── README.md   
└── Despliegue.md  

### Compilación automática
Azure Static Web Apps detectó automáticamente que es un proyecto Angular y ejecutó:

```bashs
npm install
npm run build
Nota: Esto generó la carpeta dist/pokedex-angular/ con los archivos estáticos compilados.
```
## Paso 2: Crear Static Web App en Azure Portal

### 2.1 Acceso al portal

-   URL: [https://portal.azure.com](https://portal.azure.com/)
    
-   Iniciar sesión con cuenta verificada de Azure for Students
    

### 2.2 Crear recurso

1.  Click en **"Create a resource"** (+)
    
2.  Buscar: **"Static Web Apps"**
    
3.  Seleccionar **"Static Web App"** de Microsoft
    
4.  Click en **"Create"**
    

### 2.3 Configuración básica:

|  Campo         | Valor              |
| :------------- | :----------------- |
| Subscription   | Azure for Students |
| Resource Group | arp-group          |
| Name           | pokedex            |
| Region         | westeurope         |
| Plan           | Free               |

### 2.4 Configuración de GitHub:

| Campo        | Valor   |
| :----------- | :------ |
| Source       | GitHub  |
| Organization | DEUXMO  |
| Repository   | Pokedex |
| Branch       | main    |

### 2.5 Configuración de build (detectada automáticamente):
| Campo           | Valor                  |
| :-------------- | :--------------------- |
| App location    | `/`                    |
| Api location    | (vacío)                |
| Output location | `dist/pokedex-angular` |

## Paso 3: Configuración de routing y seguridad

### 3.1 Archivo  `staticwebapp.config.json`

Creado en la raíz del repositorio para habilitar routing SPA y headers de seguridad:  
`
{  
  "navigationFallback": {  
    "rewrite": "/index.html",  
    "exclude": [  
      "/assets/*",  
      "/*.css",  
      "/*.js",  
      "/*.png",  
      "/*.jpg",  
      "/*.jpeg",  
      "/*.gif",  
      "/*.svg",  
      "/*.ico",  
      "/*.woff",  
      "/*.woff2",  
      "/*.ttf"  
    ]  
  },  
  "globalHeaders": {  
    "X-Content-Type-Options": "nosniff",  
    "X-Frame-Options": "DENY",  
    "Referrer-Policy": "no-referrer",  
    "Strict-Transport-Security": "max-age=31536000;   includeSubDomains; preload",  
    "Permissions-Policy": "camera=(), microphone=(), geolocation=  ()",  
    "Content-Security-Policy": "default-src 'self' https:; script-  src 'self' 'unsafe-inline' https:; style-src 'self' 'unsafe-inline'   https:; img-src 'self' https: data:; font-src 'self' https: data:;   connect-src 'self' https://pokeapi.co https://*.pokeapi.co; object-  src 'none'; frame-ancestors 'none'; base-uri 'self'; form-action   'self'; upgrade-insecure-requests"  
  }  
}  
`

### 3.2 Propósito de cada header:
| Header                          | Propósito                                                |
| :------------------------------ | :------------------------------------------------------- |
| Content-Security-Policy         | Controla qué recursos puede cargar la app (previene XSS) |
| Strict-Transport-Security       | Obliga el uso de HTTPS                                   |
| X-Content-Type-Options: nosniff | Evita la detección automática de tipos de archivo        |
| X-Frame-Options: DENY           | Evita que la app se muestre en iframes externos          |
| Referrer-Policy: no-referrer    | Minimiza la fuga de información en cabeceras HTTP        |
| Permissions-Policy              | Desactiva acceso a geolocalización, micrófono y cámara   |

### 3.3 GitHub Actions Workflow

Azure creó automáticamente el archivo `.github/workflows/azure-static-web-apps-*.yml` que:

-   Se ejecuta en cada push a la rama main
    
-   Compila la aplicación Angular
    
-   Despliega los archivos estáticos generados
    

----------

## Paso 4: Obtener URL pública

### 4.1 Despliegue exitoso

-   Tiempo de despliegue inicial: ~5 minutos
    
-   Compilación automática: ~3 minutos
    
-   Workflow de GitHub Actions: Activo y funcionando
    

### 4.2 URL generada

**[https://lemon-meadow-025a28c0f7.azurestaticapps.net](https://lemon-meadow-025a28c0f7.azurestaticapps.net/)**

### 4.3 Validación de funcionamiento

-   ✅ Aplicación accesible desde URL pública
    
-   ✅ Sin errores 404/500
    
-   ✅ Sin errores en consola del navegador
    
-   ✅ HTTPS activo
    
-   ✅ Navegación SPA funcional (Home ↔ Detalles de Pokémon)
    
-   ✅ Búsqueda y filtros operativos
    
-   ✅ Imágenes de Pokémon cargando correctamente
    

----------

## Paso 5: Verificación de seguridad

### Escaneo en securityheaders.com

-   **URL escaneada:** [https://lemon-meadow-025a28c0f7.azurestaticapps.net](https://lemon-meadow-025a28c0f7.azurestaticapps.net/)
    
-   **Calificación obtenida:** A
    
-   **Headers implementados:**
    
    -   ✅ Strict-Transport-Security
        
    -   ✅ X-Frame-Options
        
    -   ✅ X-Content-Type-Options
        
    -   ✅ Referrer-Policy
        
    -   ✅ Content-Security-Policy
        
    -   ✅ Permissions-Policy
        
## Posibles errores y soluciones
| Error                         | Causa                    | Solución                                                           |
| :---------------------------- | :----------------------- | :----------------------------------------------------------------- |
| 404 en rutas de Angular       | Falta navigationFallback | Agregar `staticwebapp.config.json` con rewrite a index.html        |
| Recursos no cargan            | CSP restrictivo          | Ajustar CSP para permitir fuentes de imágenes y APIs externas      |
| Imágenes de Pokémon no cargan | img-src restrictivo      | Agregar <https://raw.githubusercontent.com> y <https://pokeapi.co> |
| Build falla en GitHub Actions | Error en package.json    | Verificar que todas las dependencias estén en package.json         |
| Despliegue no se actualiza    | Workflow fallando        | Revisar logs en GitHub → Actions                                   |


<!--stackedit_data:
eyJoaXN0b3J5IjpbMTEzMjQ5MTAyMiwxNjE0ODIwNjg2LDIwMz
g3Mjg5NjIsMjAzODcyODk2MiwtODI5MDM4NTg0LC0xNzM1NDAy
ODU3LC0zMzI0NTUzNjNdfQ==
-->