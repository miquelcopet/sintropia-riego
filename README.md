# Sintropia Riego

PWA local para gestionar riegos por árbol e hilera. No usa backend, base de datos remota, analítica ni cuentas.

## Ejecutar en tu ordenador

Necesitas Python 3 instalado. Descomprime la carpeta y ejecuta:

- Windows: doble clic en `iniciar-windows.bat`
- macOS/Linux: `./iniciar-mac-linux.sh`

Después abre `http://localhost:8000` en el navegador.

También puedes ejecutar manualmente:

```bash
python -m http.server 8000
```

## Instalar como PWA

Con la app abierta en `http://localhost:8000`, utiliza la opción "Instalar app" del navegador (si aparece) o "Añadir a pantalla de inicio". El service worker permite abrirla sin conexión después de la primera carga.

Nota: la instalación PWA requiere un contexto seguro (localhost cuenta como seguro). Abrir `index.html` directamente como archivo no activa el service worker.

## Datos y copias

- El guardado automático usa `localStorage` del navegador.
- "Descargar copia JSON" genera un archivo `.json` portable.
- "Importar archivo JSON" restaura una copia.
- "Vincular archivo JSON" usa la File System Access API en navegadores compatibles (principalmente Chromium). La autorización al archivo la concede el usuario.
- Haz copias periódicas. Si borras los datos del navegador, puedes perder el almacenamiento local.

## Modelo de datos

El JSON contiene `species`, `rows`, `trees` y `events`. Cada riego se registra como evento por árbol. La fecha `lastWatered` facilita calcular el semáforo; el historial conserva los eventos anteriores.

## Funcionalidades

- Dashboard con árboles verdes, en atención y urgentes.
- Especies con umbrales amarillo/rojo.
- Parcelas e hileras.
- Árboles individuales con estado y fecha de último riego.
- Registro de intervalos, riego completo de hilera y árboles sueltos.
- Importación/exportación JSON.

## Limitaciones de esta primera versión

- Los datos se guardan en el navegador y no se sincronizan entre dispositivos.
- No hay notificaciones push.
- El prototipo usa fechas locales de calendario para el cálculo de días.
- La opción de vincular JSON depende del soporte del navegador.
