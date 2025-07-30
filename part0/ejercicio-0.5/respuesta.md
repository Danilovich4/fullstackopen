# Ejercicio 0.5 – Acceso a la versión SPA de la aplicación de notas

Este diagrama describe lo que ocurre cuando el usuario accede a la versión SPA (Single Page Application) en [exampleapp/spa](https://studies.cs.helsinki.fi/exampleapp/spa).

```mermaid
sequenceDiagram
    participant browser
    participant server

    browser->>server: GET /spa
    activate server
    server-->>browser: HTML del SPA
    deactivate server

    browser->>server: GET /main.css
    activate server
    server-->>browser: CSS file
    deactivate server

    browser->>server: GET /main.js
    activate server
    server-->>browser: JavaScript file
    deactivate server

    Note right of browser: El navegador ejecuta el JS que inicializa la SPA

    browser->>server: GET /data.json
    activate server
    server-->>browser: JSON con todas las notas
    deactivate server

    Note right of browser: El navegador renderiza las notas usando el JSON (sin recarga de página)
