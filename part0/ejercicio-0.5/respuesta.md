# Ejercicio 0.5 – Acceso a la versión SPA de la aplicación de notas

Este diagrama muestra lo que ocurre cuando un usuario accede a la versión de aplicación de una sola página (SPA) en [exampleapp/spa](https://studies.cs.helsinki.fi/exampleapp/spa).

```mermaid
sequenceDiagram
    participant browser
    participant server

    browser->>server: GET /spa
    activate server
    server-->>browser: HTML del SPA
    deactivate server

    browser->>server: GET /main.css
    server-->>browser: CSS file

    browser->>server: GET /main.js
    server-->>browser: JavaScript file

    Note right of browser: El navegador ejecuta el JS y renderiza la estructura de la SPA

    browser->>server: GET /data.json
    server-->>browser: JSON con todas las notas

    Note right of browser: El navegador renderiza las notas usando el JSON sin recargar la página
