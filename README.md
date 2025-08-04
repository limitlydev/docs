# Limitly Documentation

Documentación completa de la API de Limitly con soporte para OpenAPI 3.0.3.

## Características

- **Documentación Interactiva**: Prueba los endpoints directamente desde el navegador
- **Especificación OpenAPI**: Compatible con herramientas estándar de la industria
- **Generación de Código**: Genera clientes en múltiples lenguajes de programación
- **Validación de Esquemas**: Validación automática de requests/responses
- **Tipos Seguros**: Definiciones de tipos completas para todas las estructuras de datos

## Estructura del Proyecto

```
docs/
├── api-reference/
│   └── openapi.json        # Especificación OpenAPI completa
├── sdk/                    # Documentación del SDK
├── essentials/             # Guías esenciales
├── api/                    # Documentación detallada de la API
├── ai-tools/              # Herramientas de IA
├── docs.json              # Configuración de Mintlify
└── README.md              # Este archivo
```

## Configuración OpenAPI

La documentación está configurada para usar OpenAPI 3.0.3 con las siguientes características:

### Endpoints Documentados

- **Gestión de Usuarios**: CRUD completo para usuarios
- **Gestión de API Keys**: Crear, leer, actualizar y eliminar claves API
- **Gestión de Planes**: Administrar planes de rate limiting
- **Validación**: Validar requests contra límites de uso

### Esquemas de Datos

- **User**: Información de usuarios
- **ApiKey**: Claves API y su estado
- **Plan**: Planes de rate limiting
- **Usage**: Estadísticas de uso
- **Request**: Historial de requests
- **Validation**: Requests de validación

### Autenticación

Todas las requests requieren autenticación mediante Bearer token:

```bash
curl -H "Authorization: Bearer YOUR_API_KEY" \
  https://api.limitly.dev/v1/users
```

## Herramientas Compatibles

### Generación de Código

- **OpenAPI Generator**: `openapi-generator-cli generate`
- **Swagger Codegen**: `swagger-codegen generate`
- **NSwag**: Para aplicaciones .NET

### Validación

- **Ajv**: Validación de JSON Schema
- **OpenAPI Validator**: Validación de especificaciones
- **Postman**: Importación directa de la especificación

### Documentación

- **Mintlify**: Hosting y visualización
- **Swagger UI**: Interfaz interactiva
- **Redoc**: Documentación alternativa

## Desarrollo

### Agregar Nuevos Endpoints

1. Actualiza `api-reference/openapi.json` con el nuevo endpoint
2. Crea documentación MDX en `api-reference/endpoints/`
3. Actualiza la navegación en `docs.json`

### Ejemplo de Endpoint

```json
{
  "/v1/new-endpoint": {
    "get": {
      "summary": "Get new data",
      "description": "Retrieve new data from the API",
      "parameters": [
        {
          "name": "id",
          "in": "path",
          "required": true,
          "schema": {
            "type": "string"
          }
        }
      ],
      "responses": {
        "200": {
          "description": "Success",
          "content": {
            "application/json": {
              "schema": {
                "$ref": "#/components/schemas/NewData"
              }
            }
          }
        }
      }
    }
  }
}
```

### Agregar Nuevos Esquemas

```json
{
  "components": {
    "schemas": {
      "NewData": {
        "type": "object",
        "properties": {
          "id": {
            "type": "string",
            "description": "Unique identifier"
          },
          "name": {
            "type": "string",
            "description": "Name of the data"
          }
        },
        "required": ["id", "name"]
      }
    }
  }
}
```

## Despliegue

### Mintlify

La documentación está configurada para desplegarse en Mintlify:

1. Conecta tu repositorio a Mintlify
2. La configuración se lee automáticamente desde `docs.json`
3. La especificación OpenAPI se carga desde `api-reference/openapi.json`

### Otros Proveedores

- **GitHub Pages**: Despliega la documentación estática
- **Netlify**: Hosting gratuito con CI/CD
- **Vercel**: Despliegue automático desde Git

## Contribución

1. Fork el repositorio
2. Crea una rama para tu feature
3. Actualiza la documentación y especificación OpenAPI
4. Envía un pull request

## Recursos

- [OpenAPI Specification](https://spec.openapis.org/oas/v3.1.0)
- [Mintlify Documentation](https://mintlify.com/docs)
- [Swagger UI](https://swagger.io/tools/swagger-ui/)
- [OpenAPI Generator](https://openapi-generator.tech/)

## Soporte

- **Email**: hi@limitly.dev
- **GitHub**: Reporta issues en el repositorio
- **Documentación**: Consulta la documentación completa
