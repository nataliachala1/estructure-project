# estructure-project

# Modelo C4

## Modelo c4-Nivel C3, C4

### Nivel c3 Componentes

**¿Como esta organizado el backend internamente??**

Este nivel baría según el enfoque arquitectónico elegido. Las cuatro organizaciones posibles se detallan el la sección 2

Backend API
 - security -> JWt, roles, permisos
 - Horario -> Dominio principal del sistema
 - Ficha -> Fichas de formación
 - Ambiente -> Ambientes / aulas de formación 
 - Instructor -> Gestión de instructores


**Rol de cada componente interno**

Componente | Responsabilidad       

- Entity -> Clase de dominio/modelo de base de datos
- IRepository -> Contrato/interfaz de acceso de datos
- IService -> Contrato/interfaz de lógica de negocio
- Service -> Implementación de la lógica de negocio
- Controller -> Punto de entrada HTTP (endpoints REST)
- DTO -> Objeto de transferencia de datos (request/response)
- IDTO -> Interfaz o contrato del DTO
- Utils / JWT -> Utilidades transversales : tokens, validaciones, helpers

## Las cuatro organizaciones del proyecto

El instructor socializó cuatro formas de estructuras el backend. 

### 1. All project - Todo en un solo paquete

Es el punto de partida más básico. Todos los artefactos del sistema viven en el mismo nivel, sin separación por módulo ni por capa. No hay jerarquía clara. 

- Todos los archivos están al mismo nivel sin ninguna jerarquía.
- Conforme crece el proyecto, se vuelve imposible de navegar y mantener
- No hay separación de responsabilidades.

**Ventajas**

- Rápido de empezar
- Sin curva de aprendizaje
- Útil para prototipos muy pequeños

**Desventajas**

- Imposible de escalar
- Sin separación de responsabilidades
- Caos total en proyectos medianos/grandes

### 2. By Module - Organización por Módulo de Negocio

Cada módulo del negocio agrupa todas sus capas de forma cohesionada. Es el enfoque más natural para proyectos medianos y el más alineado al dominio. 

- Cada módulo es una "mini aplicación" con todas sus capas.
- Fácil de localizar cualquier artefacto: si es de horarios, está en **horario* 
- Preparado para migrar a microservicios extrayendo cada carpeta. 

**Ventajas**

- Alta cohesión por módulo
- Fácil de navegar y mantener
- Natural para microservicios
- Escala bien con el equipo

**Desventajas**

- Puede haber duplicado de lógica transversal
- Requiere disciplina para no mezclar módulos.

### 3. DDD - Domain Driven Design

Organiza el proyecto en torno al dominio del negocio puro, separando explícitamente la lógica de dominio de la infraestructura técnica. Introduce capas: domain, application, infraestructure.

**Ventajas**

- Dominio completamente aislado y testeable
- Perfecto para la lógica de negocio compleja
- Escala muy bien
- TDD natural en la capa de dominio

**Desventajas**

- Alta curva de aprendizaje
- Más archivos y carpetas
- Puede ser excesivo para proyectos simples
- Requieren equipo con experiencia

