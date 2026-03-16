# Product Requirements Document (PRD) - Enfoque de Negocio

**Proyecto:** Compartiendo Espacio
**Documento:** Reglas de Negocio y Alcance del Producto Final
**Estado:** Definición de MVP y Escalabilidad Comercial

---

## 1. Visión y Objetivos de Negocio

"Compartiendo Espacio" busca transformar la infraestructura de estacionamientos urbanos en una red conectada, inteligente y colaborativa. El objetivo comercial es captar el mercado de movilidad urbana ofreciendo un ecosistema de doble vía (B2B para recintos comerciales y B2C/P2P para usuarios finales), reduciendo el tiempo de búsqueda de aparcamiento en un 40% y optimizando la tasa de ocupación de los recintos asociados.

---

## 2. Reglas de Negocio (Business Rules)

Para garantizar la viabilidad, seguridad y rentabilidad del ecosistema, el producto final debe regirse por las siguientes normativas internas:

* **Regla de Identidad y Seguridad:** Todo usuario (conductor o administrador) debe validar su identidad mediante un documento oficial (ej. RUT) para operar en la plataforma. Esto previene fraudes en el modelo Peer-to-Peer (P2P) y facilita la resolución de conflictos.
* **Regla de Espacios Inclusivos:** Las plazas de garantía (exclusivas para personas con discapacidad) no pueden ser reservadas bajo el modelo de tarifa dinámica. Su estado se muestra en tiempo real, pero el acceso requiere la exhibición de la credencial oficial en el recinto.
* **Regla de Reservas y Penalizaciones:** * Las reservas anticipadas tienen un tiempo de gracia de 15 minutos posteriores a la hora declarada de llegada.
 * Pasado este tiempo, la reserva se cancela automáticamente (No-Show) y el espacio vuelve a estar disponible. Se aplicará un cobro de penalización al usuario.
* **Regla de Tarifas Dinámicas:** El algoritmo de precios ajustará el costo de la reserva anticipada basándose en la demanda del momento, pero siempre dentro de un límite máximo (cap) definido por el administrador del recinto para evitar precios predatorios.
* **Regla de Reparto de Ingresos (Modelo P2P):** En el modelo de economía colaborativa, la plataforma retendrá una comisión porcentual fija por cada transacción exitosa entre un particular que ofrece su espacio y el conductor que lo arrienda.

---

## 3. Alcance del Producto Final (Qué contiene)

El producto en su fase final de lanzamiento comercial estará compuesto por cuatro módulos interconectados:

### A. Aplicación Cliente (Conductores)
* Mapa interactivo con filtros (electromovilidad, tamaño del vehículo).
* Semáforo de ocupación en tiempo real.
* Billetera virtual o integración de métodos de pago (tarjetas, cobro automático).
* Sistema de reservas anticipadas y notificaciones push.
* Módulo de reportes comunitarios (gamificación).

### B. Dashboard Administrativo (Dueños/Operadores)
* Panel de control SaaS para monitoreo de ingresos y rotación.
* Gestión de inventario (bloqueo y liberación de plazas manual).
* Reportes de analítica predictiva.
* Módulo de atención al cliente y resolución de disputas.

### C. Portal Peer-to-Peer (Anfitriones)
* Interfaz para que usuarios particulares registren, verifiquen y publiquen sus estacionamientos privados.
* Calendario de disponibilidad para definir en qué horarios se puede arrendar el espacio.

### D. API y Motor Predictivo
* **Motor AI (Python):** Microservicio que procesa datos históricos para predecir la disponibilidad.
* **Gateway IoT:** API abierta documentada para recibir datos de sensores de piso, barreras automáticas o cámaras de lectura de patentes.

---

## 4. Brechas para el Producto Final (Lo que falta por desarrollar)

Para llevar este prototipo a un producto comercialmente viable, es necesario abordar las siguientes áreas en las próximas fases del proyecto:

* **Integración de Pasarela de Pagos:** Implementar un proveedor de pagos (ej. Stripe, Transbank/Webpay) para procesar las reservas, las penalizaciones y los pagos a los anfitriones del modelo P2P.
* **Marco Legal y Términos de Servicio:** Redactar y validar legalmente los Términos y Condiciones, Políticas de Privacidad y el tratamiento de datos personales, especialmente la información de geolocalización y documentos de identidad.
* **Estrategia de Hardware (Partnerships):** Aunque la app funciona con reportes comunitarios y administración manual al principio, el producto final requiere alianzas con proveedores de hardware (sensores IoT) para automatizar el estado de ocupación.
* **Estrategia de Onboarding:** Diseñar el flujo de captación de los primeros estacionamientos (B2B) para asegurar que haya oferta disponible antes de lanzar la aplicación a los conductores (B2C).

---

## 5. Métricas de Éxito (KPIs)

El rendimiento del producto final se medirá a través de:
* **Tasa de Conversión de Reservas:** Porcentaje de usuarios que pasan de mirar el mapa a reservar un espacio.
* **Precisión del Motor Predictivo:** Diferencia porcentual entre la disponibilidad estimada por la IA y la disponibilidad real reportada.
* **Usuarios Activos Mensuales (MAU) y Retención:** Frecuencia con la que los conductores vuelven a usar la aplicación.
