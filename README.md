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

![image](https://github.com/user-attachments/assets/27bfe806-761c-4ca4-8aeb-13afc4ce76e7)


El modelo relacional de Glow Facial está diseñado para organizar los datos de manera eficiente y garantizar una gestión clara de los usuarios, productos, categorías, opiniones y detalles de productos relacionados.

### *Tablas Principales y Relaciones*

**1. Usuario**

PK: idUsuario (INT)

Atributos: Nombre, Apellido, Correo, Teléfono, Dirección, TipoCliente

**Relaciones:**

Se relaciona con Facturación (idUsuario como FK) → Un usuario puede tener múltiples facturas.

**3. Empleado**

PK: idEmpleado (INT)

Atributos: Nombre, Apellido, TiempoServicio, Rol

**Relaciones:**

Se relaciona con Facturación (idEmpleado como FK) → Un empleado puede gestionar múltiples facturas.

**4. Servicio**

PK: idServicio (INT)

Atributos: Detalle, Precio

**Relaciones:**

Se relaciona con Facturación (idServicio como FK) → Un servicio puede estar asociado a múltiples facturas.

**5. Producto**

PK: idProducto (INT)

Atributos: Nombre, Marca, Descripción, Precio

**Relaciones:**

Se relaciona con Facturación (idProducto como FK) → Un producto puede estar asociado a múltiples facturas.

**6. Facturación**

PK: idFacturacion (INT)

Atributos: Subtotal, Descuento, Total, Comentarios

**FK:**

idUsuario (Referencia a Usuario)

idEmpleado (Referencia a Empleado)

idServicio (Referencia a Servicio)

idProducto (Referencia a Producto)

**Descripción:**

Es la tabla central donde se registran las facturas, asociando a cada transacción un usuario, un empleado que la gestionó, y los productos o servicios adquiridos.

### *Script*
CREATE DATABASE  IF NOT EXISTS `spa`;
USE `spa`;

DROP TABLE IF EXISTS `facturacion`;
CREATE TABLE `facturacion` (
  `idfacturacion` int NOT NULL,
  `idUsuario` int NOT NULL,
  `idEmpleado` int NOT NULL,
  `idServicio` int NOT NULL,
  `idProducto` int NOT NULL,
  `Subtotal` double DEFAULT NULL,
  `Descuento` double DEFAULT NULL,
  `Total` double DEFAULT NULL,
  PRIMARY KEY (`idfacturacion`,`idUsuario`,`idEmpleado`,`idServicio`,`idProducto`),
  KEY `fkUsuario_idx` (`idUsuario`),
  KEY `fk_producto` (`idProducto`),
  CONSTRAINT `fk_producto` FOREIGN KEY (`idProducto`) REFERENCES `producto` (`idproducto`) ON DELETE RESTRICT ON UPDATE CASCADE,
  CONSTRAINT `fkUsuario` FOREIGN KEY (`idUsuario`) REFERENCES `usuario` (`idUsuario`) ON UPDATE CASCADE
) ENGINE=InnoDB DEFAULT CHARSET=utf8mb4 COLLATE=utf8mb4_0900_ai_ci;

DROP TABLE IF EXISTS `producto`;
CREATE TABLE `producto` (
  `idproducto` int NOT NULL,
  `Nombre` varchar(45) DEFAULT NULL,
  `Marca` varchar(45) DEFAULT NULL,
  `Descripcion` varchar(200) DEFAULT NULL,
  `Precio` double DEFAULT NULL,
  PRIMARY KEY (`idproducto`),
  CONSTRAINT `fkprod` FOREIGN KEY (`idproducto`) REFERENCES `facturacion` (`idProducto`)
) ENGINE=InnoDB DEFAULT CHARSET=utf8mb4 COLLATE=utf8mb4_0900_ai_ci;

DROP TABLE IF EXISTS `usuario`;
CREATE TABLE `usuario` (
  `idUsuario` int NOT NULL,
  `Nombre` varchar(45) DEFAULT NULL,
  `Apellido` varchar(45) DEFAULT NULL,
  `Pass` varchar(45) DEFAULT NULL,
  `Correo` varchar(90) DEFAULT NULL,
  `Telf` varchar(45) DEFAULT NULL,
  `Direccion` varchar(200) DEFAULT NULL,
  PRIMARY KEY (`idUsuario`)
) ENGINE=InnoDB DEFAULT CHARSET=utf8mb4 COLLATE=utf8mb4_0900_ai_ci;


Glow Facial tiene el potencial de transformar el cuidado facial, ofreciendo productos personalizados y una experiencia única.

Sigamos trabajando para convertir esta app en una solución innovadora y accesible para todos.

¡Hagámoslo realidad! 🌟
