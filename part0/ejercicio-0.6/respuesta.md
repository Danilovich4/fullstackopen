# Ejercicio 0.6 – Crear una nueva nota en la SPA

Este diagrama representa el flujo de eventos cuando un usuario crea una nueva nota en la versión SPA de la aplicación en [exampleapp/spa](https://studies.cs.helsinki.fi/exampleapp/spa).

```mermaid
sequenceDiagram
    participant browser
    participant server

    Note over browser: El usuario escribe una nota y hace clic en "Save"
    browser->>browser: JS captura el evento submit
    browser->>browser: JS crea un objeto nota (content + date)

    browser->>server: POST /new_note_spa
    activate server
    server-->>browser: 201 Created (o 200 OK)
    deactivate server

    Note right of browser: El navegador actualiza la UI agregando la nueva nota localmente
