# 📄 Informe Técnico del Taller

## 🔖 Nombre del Taller
_Taller 7 - Integración de Vistas de Arquitectura_

## 👥 Integrantes del equipo
- Camilo Arciniegas Guerrero
- Juan Sebastián Ayala Silva
- Juan Diego Campo Conde

## 🧠 Descripción general del trabajo
El objetivo de este taller fue integrar todas las vistas arquitectónicas desarrolladas a lo largo del curso (negocio, información, aplicaciones, infraestructura y seguridad) en una narrativa visual coherente aplicada al cliente real del equipo: **Ataraxia Parkour**, un gimnasio especializado en parkour.

La actividad consistió en revisar los entregables de los talleres anteriores, identificar las relaciones entre cada vista y consolidarlas en un tablero unificado que permita visualizar cómo los diferentes niveles de la arquitectura se articulan para soportar la operación del negocio.

## 🔧 Proceso de desarrollo
El equipo comenzó revisando los entregables de los talleres 1 al 6 para extraer los elementos relevantes de cada vista. Se identificó que la arquitectura de Ataraxia Parkour es marcadamente simple: el negocio opera con dos únicas herramientas digitales (Excel Online y WhatsApp Business), lo que condicionó fuertemente las capas de aplicaciones, infraestructura y seguridad.

Se tomó la decisión de representar fielmente la realidad del cliente sin añadir sistemas que no existen, señalando en cambio las brechas arquitectónicas que esto genera. El tablero se construyó en draw.io con cinco capas apiladas verticalmente, conectadas mediante flechas que muestran la dirección de soporte entre vistas. Se añadió una nota explícita de brecha en la capa de aplicaciones para documentar la ausencia de integración entre herramientas.

## 🧩 Análisis del modelo propuesto

**Estructura del modelo:**
El tablero integra las cinco vistas como capas jerarquizadas de arriba hacia abajo: negocio → información → aplicaciones → infraestructura → seguridad. Esta disposición refleja la lógica de soporte: cada capa inferior habilita a la superior. La seguridad se trata como una capa transversal que, en el caso de Ataraxia, no fue diseñada intencionalmente sino que proviene de los controles nativos de Microsoft 365.

**Representación de las necesidades del cliente:**
Los tres procesos de negocio identificados (pago de clases, registro de clases y control de asistencia) se materializan en tres entidades de información (Estudiante, Paquete de clases y Asistencia), las cuales son gestionadas íntegramente a través de un único archivo de Excel Online. WhatsApp Business cumple un rol exclusivamente comunicacional y no tiene integración con los datos operativos.

**Supuestos tomados:**
- Se asume que el Excel Online está alojado en Microsoft 365 con licencia básica o educativa.
- Se asume que no existe ningún sistema de reservas, pago digital ni CRM, dado que el cliente no los mencionó.
- Se asume que los profesores tienen acceso de edición al Excel y los estudiantes no tienen acceso directo a ningún sistema.

## 📈 Diagrama final entregado

> Ver archivo adjunto: `ataraxia-vistas.drawio`

El tablero muestra las cinco vistas integradas con sus componentes internos y las relaciones entre capas. Se destaca visualmente la brecha de integración en la capa de aplicaciones y la ausencia de RBAC en la capa de seguridad.

## 📋 Tabla de actores, entidades o componentes

| Nombre del elemento     | Tipo        | Descripción                                                                 | Responsable        |
|-------------------------|-------------|-----------------------------------------------------------------------------|--------------------|
| Estudiante              | Entidad     | Datos personales del alumno: nombre, edad, condición médica                 | Administración     |
| Paquete de clases       | Entidad     | Registro del número de clases compradas y monto pagado                      | Administración     |
| Asistencia              | Entidad     | Saldo de clases restantes por alumno, actualizado tras cada sesión          | Profesor           |
| Pago de clases          | Proceso     | Cobro al estudiante por un paquete de clases (efectivo o transferencia)     | Administración     |
| Registro de clases      | Proceso     | Anotación manual de la sesión dictada en el Excel por parte del profesor    | Profesor           |
| Control de asistencia   | Proceso     | Descuento de una clase del saldo del alumno al asistir a una sesión         | Profesor           |
| Excel Online            | Aplicación  | Herramienta central que concentra registro, asistencia y datos de pagos     | Microsoft 365      |
| WhatsApp Business       | Aplicación  | Canal de comunicación con estudiantes para avisos y coordinación            | Meta               |
| Microsoft 365 (nube)    | Infraestructura | Plataforma en la nube que aloja el Excel Online compartido              | Microsoft          |
| Meta Cloud              | Infraestructura | Infraestructura de WhatsApp Business                                    | Meta               |
| Acceso por invitación   | Control de seguridad | Solo usuarios añadidos pueden ver o editar el Excel              | Microsoft 365      |
| Autenticación M365      | Control de seguridad | Login obligatorio con cuenta Microsoft para acceder al documento     | Microsoft          |
| Sin RBAC                | Brecha de seguridad  | No existen roles diferenciados; cualquier usuario con acceso puede editar cualquier dato | — |

## 📚 Referencias
- [1] The Open Group. *TOGAF Standard, Version 9.2*. 2018. https://www.opengroup.org/togaf
- [2] Microsoft. *Excel Online — Microsoft 365*. https://www.microsoft.com/es-es/microsoft-365/excel
- [3] Meta. *WhatsApp Business Platform*. https://business.whatsapp.com/

---

_Este documento hace parte de la entrega del Taller 7 del curso AREM (Arquitectura Empresarial) - Universidad de La Sabana._
