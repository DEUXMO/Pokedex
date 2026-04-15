
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


### 3.2 Propósito de cada header:
| Header                          | Propósito                                                |
| :------------------------------ | :------------------------------------------------------- |
| Content-Security-Policy         | Controla qué recursos puede cargar la app (previene XSS) |
| Strict-Transport-Security       | Obliga el uso de HTTPS                                   |
| X-Content-Type-Options: nosniff | Evita la detección automática de tipos de archivo        |
| X-Frame-Options: DENY           | Evita que la app se muestre en iframes externos          |
| Referrer-Policy: no-referrer    | Minimiza la fuga de información en cabeceras HTTP        |
| Permissions-Policy              | Desactiva acceso a geolocalización, micrófono y cámara   |

<!--stackedit_data:
eyJoaXN0b3J5IjpbMjU3MTk2MzU5LC0xNzM1NDAyODU3LC0zMz
I0NTUzNjNdfQ==
-->