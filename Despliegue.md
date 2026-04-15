
# Proceso Técnico de Despliegue PokeDex Angular

## 📋 Información General
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

| Campo          | Valor              |
| :------------- | :----------------- |
| Subscription   | Azure for Students |
| Resource Group | arp-group          |
| Name           | pokedex            |
| Region         | westeurope         |
| Plan           | Free               |

<!--stackedit_data:
eyJoaXN0b3J5IjpbMTI3MDQ5NDc5NywtMTczNTQwMjg1NywtMz
MyNDU1MzYzXX0=
-->