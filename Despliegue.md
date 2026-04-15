
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


npm install
npm run build
<!--stackedit_data:
eyJoaXN0b3J5IjpbMTg5ODc4MDg0MCwtMTczNTQwMjg1NywtMz
MyNDU1MzYzXX0=
-->