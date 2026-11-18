# Introducción paso a paso al framework web NestJS

📖 **Lea el tutorial: [https://stahe.github.io/ales-nestjs-html-sept-2026/](https://stahe.github.io/ales-nestjs-html-sept-2026/)**

Este curso enseña a construir una aplicación web **MVC** con el framework [NestJS](https://nestjs.com): una aplicación cuyas páginas HTML son generadas **por el servidor** mediante el motor de vistas Handlebars, sin un framework JavaScript del lado del cliente.

Sigue la progresión del curso [Introducción a ASP.NET MVC mediante ejemplos](https://stahe.github.io/ales-aspnetmvc-nov-2013/) (2013), adaptada al ecosistema Node.js/TypeScript:

| ASP.NET MVC (2013) | NestJS (2026) |
|---|---|
| C#, controladores, acciones | TypeScript, `@Controller`, `@Get`, `@Post` |
| vistas Razor, `_Layout.cshtml` | vistas Handlebars, `layout.hbs` |
| `[Required]`, `ModelState.IsValid` | class-validator, validación de formularios |
| sesión, `TempData` | cookies, token JWT, mensajes flash |
| filtros, `[Authorize]` | middleware, guardias, interceptores, `@Roles` |
| Entity Framework | TypeORM + MySQL |

## El enfoque: muchos ejemplos breves y luego un caso de estudio

El curso se basa en **28 proyectos breves**, cada uno centrado en un único concepto. Es posible ejecutarlos y modificarlos. Todos los ejemplos comparten un único `npm install`.

| Capítulo | Contenido | Ejemplos |
|---|---|---|
| Controladores, acciones, enrutamiento | rutas, respuestas, redirecciones, módulos, inyección de dependencias | 01–06 |
| El modelo de la acción | parámetros, conversión, validación, formularios POST, pipes | 07–12 |
| La vista y su plantilla | Handlebars, plantillas, partials, helpers, formularios, validación, Post/Redirect/Get, cuadro de diálogo de confirmación | 13–21 |
| Internacionalización | Una aplicación en francés e inglés | 22 |
| Ámbitos de datos | Aplicación, solicitud, cliente | 23 |
| El ciclo de vida de la solicitud | middleware, guardia, interceptor, pipe, filtro de excepciones | 24 |
| Autenticación y autorización | JWT en una cookie, roles, CAPTCHA, limitación de tasa | 25 a 27 |
| Arquitectura en capas | web / lógica de negocio / DAO con TypeORM, transacciones, bloqueo optimista | 28 |

Cada ejemplo se presenta con su código completo y comentarios línea por línea. El curso también muestra los resultados en tiempo de ejecución: capturas de pantalla del navegador, respuestas HTTP sin procesar obtenidas con `curl` y registros del servidor.

## El caso de estudio: RdvMedecins

El caso de estudio es una aplicación completa para **agendar citas en un consultorio médico**. Consta de unos sesenta archivos, y **todos** están listados y comentados. Reúne todos los conceptos tratados en los capítulos anteriores.

- **Tres roles:**
  - `ADMIN` gestiona médicos y clientes;
  - `DOCTOR` reserva y cancela citas;
  - `USER` es el paciente: reserva citas para sí mismo y gestiona su cuenta.
- **Reglas de negocio:**
  - no se permiten citas en el pasado;
  - solo una cita próxima por paciente;
  - sin nombres duplicados, gracias a restricciones de unicidad con nombre;
  - un bloqueo optimista impide sobrescribir un registro que otro usuario modificó entretanto.
- **Confidencialidad:** un paciente nunca ve los nombres de otros pacientes. Ese nombre ni siquiera se envía a su navegador.
- **Seguridad:**
  - token JWT en una cookie `httpOnly` / `sameSite`;
  - contraseñas con hash mediante bcrypt;
  - CAPTCHA y bloqueo temporal tras varios intentos fallidos de inicio de sesión;
  - creación de cuentas protegida por un «código de acceso» de un solo uso.
- **Una interfaz bilingüe** (francés/inglés), construida con Bootstrap 5.
- **Mejora progresiva:** la aplicación funciona por completo sin JavaScript. Un pequeño script se limita a añadir un cuadro de diálogo de confirmación navegable con el teclado.

## Tecnologías

NestJS 10 · TypeScript 5 · Express · Handlebars (hbs) · class-validator / class-transformer · TypeORM · MySQL 8 / MariaDB · Passport JWT · bcrypt · svg-captcha · Bootstrap 5

## Requisitos previos

- Conocimientos básicos de TypeScript (o JavaScript), HTML y el protocolo HTTP.
- Node.js 20 o posterior, Visual Studio Code y un servidor MySQL (p. ej., Laragon en Windows). Las instrucciones de instalación se proporcionan en los apéndices del curso.

## Autor

Este curso, sus ejemplos y su caso de estudio fueron escritos por **Claude**, la IA de [Anthropic](https://www.anthropic.com) (septiembre de 2026).
