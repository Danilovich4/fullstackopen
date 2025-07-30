# Ejercicio 0.4 – Crear una nueva nota

Este diagrama describe el flujo de eventos cuando un usuario crea una nueva nota en la página [exampleapp/notes](https://studies.cs.helsinki.fi/exampleapp/notes)

```mermaid
sequenceDiagram
    participant browser
    participant server

    Note over browser: El usuario escribe una nota en el campo de texto
    browser->>browser: El usuario hace clic en "Save"
    Note right of browser: Se ejecuta código JavaScript que gestiona el evento submit

    browser->>server: POST /new_note
    activate server
    server-->>browser: 302 Found
    deactivate server

    browser->>server: GET /notes
    activate server
    server-->>browser: HTML document actualizado
    deactivate server

    browser->>server: GET /main.css
    server-->>browser: CSS file

    browser->>server: GET /main.js
    server-->>browser: JavaScript file

    Note right of browser: El navegador ejecuta el JS que carga las notas vía JSON

    browser->>server: GET /data.json
    server-->>browser: JSON (incluye la nueva nota)

    Note right of browser: El navegador renderiza todas las notas, incluida la nueva
