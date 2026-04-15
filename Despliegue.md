# Proceso Técnico de Despliegue PokeDex

## Información General
- **Servicio:**  Azure Static Web Apps
- **Método:** Despliegue de archivos estáticos compilados desde GitHub
- **Fecha de despliegue:** 15/04/2026
- **URL pública:** https://lemon-meadow-025a28c0f7.azurestaticapps.net

---

##  Paso 1: Preparar código fuente en repositorio

### Compilación de Angular
La aplicación PokeDex fue desarrollada en Angular por Keiler Mora. 
Requiere compilación previa para generar archivos estáticos.

**Comandos utilizados:**
```bash
# Instalar dependencias
npm install

# Compilar para producción
npm run build

# Estructura 
dist/pokedex-angular/
├── index.html              (página principal)
├── main.*.js              (código JavaScript compilado)
├── polyfills.*.js         (compatibilidad de navegadores)
├── runtime.*.js             (runtime de Angular)
├── styles.*.css             (estilos compilados)
├── assets/                  (imágenes, fuentes, íconos)
│   ├── icons/
│   └── img/
└── 3rdpartylicenses.txt   (licencias de terceros)
<!--stackedit_data:
eyJoaXN0b3J5IjpbODQ0ODk1MDM1LC0xNzM1NDAyODU3LC0zMz
I0NTUzNjNdfQ==
-->