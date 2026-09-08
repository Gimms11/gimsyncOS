# Contratos y Especificación de APIs

Directorio reservado para los contratos de interfaz de programación (API) entre el backend (Spring Boot), microservicios (FastAPI) y clientes (Next.js / React Native).

## Estándares

- **Protocolo:** RESTful sobre HTTPS / JSON.
- **Autenticación:** Bearer Tokens JWT (`Authorization: Bearer <token>`).
- **Especificación:** OpenAPI 3.0 (Swagger) autogenerado con `springdoc-openapi` en `/swagger-ui.html`.

## Convención de Códigos HTTP

- `200 OK`: Consulta o actualización exitosa.
- `201 Created`: Recurso creado satisfactoriamente.
- `400 Bad Request`: Error de validación en los datos enviados.
- `401 Unauthorized`: Token faltante o expirado.
- `403 Forbidden`: Rol o permisos insuficientes para la acción.
- `404 Not Found`: Recurso no encontrado.
- `409 Conflict`: Conflicto de estado (ej. documento duplicado, stock insuficiente).
- `500 Internal Server Error`: Excepción no controlada del servidor.
