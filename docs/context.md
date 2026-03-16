# Compartiendo Espacio

**Optimización de Movilidad Urbana y Gestión Inteligente de Estacionamientos**

"Compartiendo Espacio" es una respuesta tecnológica diseñada para combatir la congestión vehicular y la búsqueda ineficiente de estacionamiento en áreas metropolitanas. Más que una simple aplicación de mapas, es un ecosistema integral creado para reducir emisiones, ahorrar tiempo y garantizar la inclusión a través del monitoreo activo de espacios para personas con discapacidad. 

Al actuar como un puente en tiempo real entre la oferta de espacios y los conductores, la plataforma reduce la fricción en la movilidad urbana y ofrece un panel de control robusto para la administración del ecosistema.

---

## Características Principales

Para destacar como una solución líder, el proyecto se sostiene en los siguientes pilares:

* **Inclusión Real:** Sistema de monitoreo activo y dedicado exclusivamente a las plazas para personas con movilidad reducida (plazas de garantía).
* **Eficiencia y Tiempo Real:** Mapeo interactivo que detecta la ubicación vía GPS y muestra la disponibilidad al instante mediante suscripciones de datos en vivo.
* **Escalabilidad IoT:** Arquitectura base con APIs abiertas, preparada para una futura integración plug-and-play con hardware físico (cámaras de reconocimiento de patentes o sensores de piso).
* **Gestión Basada en Datos:** Implementación de un Dashboard administrativo protegido por roles para la toma de decisiones informadas sobre tarifas, tasas de rotación vehicular y resolución de conflictos.

---

## Arquitectura y Stack Tecnológico

La transición hacia un ecosistema moderno basado en la nube permite un desarrollo ágil y altamente escalable. El flujo de datos y la infraestructura se organizan de la siguiente manera:

* **Framework Full-Stack (Next.js):** Encargado de la renderización del Frontend interactivo y la creación de las API Routes en el Backend. Permite una experiencia de usuario fluida, similar a una aplicación nativa, manejando la lógica de servidor sin necesidad de levantar un servicio backend separado.
* **Base de Datos y Autenticación (Supabase):** Actúa como el núcleo de los datos. Basado en PostgreSQL, permite el uso de la extensión **PostGIS** para ejecutar consultas geoespaciales complejas de forma ultrarrápida. Además, gestiona la validación de identidad (ej. RUT) y las suscripciones en tiempo real (WebSockets).
* **Despliegue y Hosting (Vercel):** Provee el alojamiento optimizado para el ecosistema Next.js, garantizando respuestas de baja latencia a los usuarios mediante despliegues en el "Edge".
* **Control de Versiones (GitHub):** Repositorio central del código vinculado con Vercel para despliegues automáticos mediante integración continua (CI/CD), facilitando la iteración rápida del prototipo.
* **Motor de Predicción (Microservicio Python):** Lógica de negocio separada para analizar el historial de datos y calcular probabilidades de disponibilidad futura según la hora estimada de llegada del usuario.

---

## Experiencia de Usuario: Semáforo de Ocupación

La interfaz utiliza un sistema visual intuitivo, alimentado por la base de datos en tiempo real, para mostrar el estado de las plazas de forma rápida y segura mientras se conduce:

* **Verde (Alta disponibilidad):** Menos del 50% de ocupación en el recinto.
* **Amarillo (Ocupación media):** Entre 50% y 85% de ocupación. Alerta al usuario de que los espacios se están agotando rápidamente.
* **Rojo (Lleno/Sin vacantes):** 86% - 100% de ocupación. Habilita la opción de activar notificaciones push o correos automáticos si se libera un espacio.

---

## Innovaciones y Propuesta de Valor

El verdadero valor diferencial de este sistema radica en su capacidad de evolución:

* **Reservas Inteligentes:** Los usuarios pueden asegurar su cupo hasta 30 minutos antes de llegar, operando bajo un modelo de tarifa dinámica transaccional.
* **Filtros de Electromovilidad y Tamaño:** Integración de filtros en la base de datos para categorizar plazas con cargadores para vehículos eléctricos o dimensiones especiales (motocicletas, camionetas).
* **Modelo Peer-to-Peer (P2P):** Expansión del ecosistema para permitir que particulares ofrezcan sus propios espacios de estacionamiento privados cuando no los estén utilizando, creando una red colaborativa.
* **Sistema de Reportes Comunitarios:** Gamificación mediante la cual los usuarios ganan beneficios dentro de la app por reportar con precisión la liberación de espacios o confirmar el estado actual de ocupación.

---

## Análisis y Determinación de Necesidades

| Fase | Descripción Detallada |
| :--- | :--- |
| **Identificación de Problemas** | Pérdida de tiempo en tráfico, alta huella de carbono por vehículos "vuelteando" y mal uso de espacios preferenciales. |
| **Oportunidades** | Implementar un sistema de geolocalización en tiempo real que actúe como puente directo entre la oferta y la demanda. |
| **Análisis de Recursos** | Necesidad de un framework ágil (Next.js), bases de datos geoespaciales (Supabase/PostGIS) y talento en desarrollo web. |
| **Priorización (SMART)** | Lograr un prototipo funcional con un alto grado de precisión en la disponibilidad de plazas y mapeo en un plazo de 6 meses. |
