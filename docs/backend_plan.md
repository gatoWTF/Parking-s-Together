# Plan de Backend y Arquitectura: Compartiendo Espacio

"Compartiendo Espacio" se presenta como una solución tecnológica orientada a optimizar la movilidad urbana y la gestión de estacionamientos. Actuando como un puente en tiempo real entre la oferta de espacios y los conductores, la plataforma reduce la fricción en la búsqueda de aparcamiento, garantiza la accesibilidad (con un enfoque en la inclusión) y ofrece un panel de control robusto para la administración del ecosistema.

---

## 1. Stack Tecnológico y Arquitectura Base

La transición hacia un ecosistema moderno basado en la nube permite un desarrollo ágil y altamente escalable. El flujo de datos y la infraestructura se organizan de la siguiente manera:

* **Framework Full-Stack (Next.js):** Se encargará tanto de la renderización del Frontend (React) como de la creación de las API Routes en el Backend. Su integración nativa permite manejar la lógica de servidor sin necesidad de levantar un servicio backend separado para las funciones estándar.
* **Base de Datos, Autenticación y Tiempo Real (Supabase):** Actuará como el núcleo de los datos. Al estar basado en PostgreSQL, permite el uso de la extensión **PostGIS** (esencial para las consultas geoespaciales y de mapas). Además, gestionará la autenticación de usuarios y las suscripciones en tiempo real (WebSockets) para actualizar la disponibilidad de estacionamientos al instante.
* **Despliegue y Hosting (Vercel):** Proveerá el alojamiento optimizado para Next.js, desplegando automáticamente la aplicación en el "Edge" para garantizar respuestas de baja latencia a los usuarios.
* **Control de Versiones y CI/CD (GitHub):** Actuará como el repositorio central del código. Al estar vinculado con Vercel, cada "push" a la rama principal generará un despliegue automático, facilitando la iteración rápida del prototipo.

---

## 2. Desarrollo y Estructuración de Módulos

### 2.1. Módulo de Geolocalización y Disponibilidad
* **Mapeo en Tiempo Real:** Las consultas geoespaciales se ejecutarán a través de las funciones de Supabase (PostGIS) para filtrar los estacionamientos más cercanos a las coordenadas GPS del usuario.
* **Sistema de Semáforo de Ocupación (Realtime):** Utilizando las suscripciones de Supabase, el cliente de Next.js escuchará los cambios en la tabla de inventario para actualizar los estados visuales sin necesidad de recargar la página:
 * **Verde (Alta disponibilidad):** Menos del 50% de ocupación.
 * **Amarillo (Media/En preparación):** Entre 50% y 85% de ocupación.
 * **Rojo (Lleno/Sin vacantes):** 86% - 100% de ocupación. Incluye lógica para disparar notificaciones si se libera un espacio.
* **Detalle de Plaza:** Consultas específicas que desglosan la capacidad total, los espacios reservados y un contador en vivo de las plazas de garantía (uso exclusivo para personas con movilidad reducida).

### 2.2. Gestión de Identidad y Autenticación (Supabase Auth)
* **Perfil de Usuario/Cliente:** Registro e inicio de sesión integrados. Las tablas relacionales en Supabase vincularán el UID del usuario con su historial de uso, la gestión de su vehículo (patente, modelo) y la validación de su RUT para asegurar un registro único y facilitar la resolución de incidentes.
* **Perfil de Administrador (Dashboard):** Un panel de control protegido mediante roles (RLS - Row Level Security en Supabase) que consume las API Routes de Next.js para mostrar métricas clave:
 * Ingresos y transacciones.
 * Tasas de rotación (tiempo promedio por vehículo).
 * Módulo de resolución de conflictos y denuncias.

---

## 3. Innovaciones y Escalabilidad a Futuro

Para que el proyecto destaque, la arquitectura mediante Supabase y Next.js deja la puerta abierta a las siguientes implementaciones técnicas:

* **Algoritmo de Predicción de Disponibilidad (Microservicio Python):** Aunque el core es Next.js, se puede desplegar un microservicio o función serverless en Python que analice el historial de datos de PostgreSQL para calcular probabilidades de disponibilidad futura según la hora estimada de llegada del usuario.
* **Integración IoT (Internet de las Cosas):** La API de Next.js estará preparada para recibir webhooks o peticiones POST desde hardware externo (cámaras de reconocimiento de patentes o sensores de piso), actualizando el estado de la base de datos automáticamente sin intervención humana.
* **Tarifas Dinámicas y Reservas Inteligentes:** Lógica transaccional que permita bloquear temporalmente un registro en la base de datos (reserva por 30 minutos) asociada a una pasarela de pago.
* **Filtros Avanzados:** Columnas específicas en la base de datos (booleanos) para categorizar plazas con cargadores de electromovilidad o dimensiones especiales (motocicletas, camionetas).
