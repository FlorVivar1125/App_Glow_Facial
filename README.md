# *App_Glow_Facial*
Glow Facial es una app de venta de productos para el cuidado facial, diseñada para ofrecerte lo mejor en belleza. Con recomendaciones personalizadas y una experiencia de compra fácil y segura, ¡tu piel radiante está a solo un clic!

## *Introducción*
Glow Facial nace con la misión de transformar la rutina de cuidado facial, llevando lo mejor en productos de belleza directamente a la palma de tu mano. Sabemos lo importante que es cuidar la piel, por eso hemos creado una plataforma intuitiva que no solo ofrece productos de calidad, sino también una experiencia única, adaptada a tus necesidades. Desde hidratación hasta protección solar, nuestra app te conecta con los productos perfectos para ti, garantizando que cada compra sea un paso hacia una piel más saludable y luminosa. Con Glow Facial, cuidar tu rostro nunca fue tan fácil y satisfactorio.

![image](https://github.com/user-attachments/assets/de2f64ef-ae66-4399-99e1-665c6c02c629)


## Contexto del problema:
En el mundo actual, el cuidado de la piel es una prioridad creciente, pero muchas personas enfrentan problemas comunes:

**1° Falta de personalización:** Los usuarios no siempre encuentran productos que se adapten a su tipo de piel o necesidades específicas, lo que puede resultar en compras ineficientes y resultados insatisfactorios.

**2° Experiencia de compra complicada:** Buscar productos adecuados en tiendas físicas o sitios web no especializados puede ser tedioso y frustrante.

**3° Acceso limitado a recomendaciones confiables:** Muchos consumidores desconfían de las sugerencias genéricas y desean orientación personalizada basada en sus características únicas.

**4° Dificultades para encontrar opciones seguras y convenientes:** El manejo de pagos y envíos en plataformas no optimizadas puede generar desconfianza y problemas logísticos.

**Glow Facial** busca **solucionar** estos retos mediante una aplicación que combina:

**-** Productos cuidadosamente seleccionados.

**-** Recomendaciones basadas en el perfil del usuario.

**-** Un proceso de compra optimizado, seguro y eficiente.

### Análisis de Requerimientos
Para abordar las necesidades identificadas, Glow Facial debe cumplir con los siguientes requerimientos:

### **Requerimientos Funcionales**

**1° Gestión de usuarios:**

**-** Registro y login de usuarios con datos básicos.

**-** Personalización del perfil según el tipo de piel y objetivos de cuidado.

**2° Catálogo de productos:**

**-** Listado detallado por categorías como hidratación, protección solar, limpieza, entre otros.

**-** Información completa de cada producto: descripción, ingredientes, precio y disponibilidad.

**3° Recomendaciones personalizadas:**

**-** Sistema basado en un cuestionario inicial para ofrecer productos adaptados al usuario.

**-** Módulo que sugiere combinaciones de productos.

**3° Proceso de compra:**

**-** Carrito de compras con cálculo automático de total y costos de envío.

**-** Métodos de pago seguros (tarjetas, transferencias y billeteras digitales).

**-** Opciones de envío personalizables con tiempo estimado.

**4° Soporte al cliente:**

**-** Chat en línea y acceso a preguntas frecuentes.

**-** Historial de solicitudes y respuestas.

### **5° Requerimientos No Funcionales:**

**-** Usabilidad: Interfaz sencilla e intuitiva para todos los usuarios.

**-** Rendimiento: Respuesta rápida al navegar por la app, incluso con muchos usuarios activos.

**-** Seguridad: Protección de datos personales y transacciones cifradas.

**-** Escalabilidad: Capacidad de adaptarse al crecimiento de la base de usuarios y productos.

## *Modelo Relacional*

![image](https://github.com/user-attachments/assets/7e8fac67-c098-49b4-acf6-a6feb9ab0354)

El modelo relacional de Glow Facial está diseñado para organizar los datos de manera eficiente y garantizar una gestión clara de los usuarios, productos, categorías, opiniones y detalles de productos relacionados.

### *Tablas Principales y Relaciones*

**1° Usuarios.**

**-**Campos principales:

idUsuarios (PK): Identificador único del usuario.

Nombre, Apellido, Ciudad, Estado, País, Correo electrónico, Teléfono: Información personal del usuario.

Producto_idProducto (FK): Relación con los productos que el usuario ha adquirido.

**2° Producto.**

**-** Campos principales:

idProducto (PK): Identificador único del producto.

Nombre, Marca, Descripción, Precio: Detalles del producto.

Relacionado con:

Usuarios: A través de Producto_idProducto.

Detalle del producto: Para vincular categorías y opiniones.

**3° Categorías.**

**-** Campos principales:

idCategorias (PK): Identificador único de la categoría.

Nombre, Descripción: Detalles de la categoría.

Productos_idProducto (FK): Relación con los productos en esta categoría.

**4° Opiniones.**

**-** Campos principales:

idOpiniones (PK): Identificador único de la opinión.

Contenido: Texto de la opinión del usuario.

Publicado: Fecha en que se publicó la opinión.

Producto_idProducto (FK): Relación con el producto que se está opinando.

**5° Detalle del Producto.**

**-** Campos principales:

Producto_idProducto (FK): Identificador único del producto.

Usuarios_idUsuarios (FK): Identificador del usuario que interactuó con el producto.

Categorías_idCategorias (FK): Categoría asociada al producto.

Opiniones_idOpiniones (FK): Relación con las opiniones sobre el producto.
