# Taller de Funciones Definidas por el Usuario (UDFs) en MySQL 🚀

## 📌 Introducción

En este taller, desarrollarás varias funciones definidas por el usuario (UDFs) en MySQL para resolver problemas comunes en bases de datos. Aprenderás a crear funciones, utilizarlas en consultas y comprender en qué casos son útiles.

---

## 🔹 Caso 1: Cálculo de Bonificaciones de Empleados

### 🧩 Escenario:
La empresa **TechCorp** otorga bonificaciones a sus empleados según su salario base. La bonificación se calcula así:

- Si el salario es **menor a 2,000 USD** → Bonificación del **10%**.  
- Si el salario está entre **2,000 y 5,000 USD** → Bonificación del **7%**.  
- Si el salario es **mayor a 5,000 USD** → Bonificación del **5%**.

### ✅ Tarea:
1. Crea una función llamada `calcular_bonificacion` que reciba un `DECIMAL(10,2)` con el salario y devuelva la bonificación correspondiente.  
2. Usa la función en un `SELECT` sobre la tabla `empleados`.

```sql
CREATE TABLE empleados (
    id INT PRIMARY KEY AUTO_INCREMENT,
    nombre VARCHAR(50),
    salario DECIMAL(10,2)
);

INSERT INTO empleados (nombre, salario) VALUES
('Juan Pérez', 1500.00),
('Ana Gómez', 3000.00),
('Carlos Ruiz', 6000.00);
🔹 Caso 2: Cálculo de Edad de Clientes
🧩 Escenario:
En la empresa MarketShop, se necesita calcular la edad de los clientes a partir de su fecha de nacimiento para determinar estrategias de marketing.

✅ Tarea:
Crea una función llamada calcular_edad que reciba un DATE y devuelva la edad del cliente.

Usa la función en un SELECT sobre la tabla clientes.

sql
Copiar
Editar
CREATE TABLE clientes (
    id INT PRIMARY KEY AUTO_INCREMENT,
    nombre VARCHAR(50),
    fecha_nacimiento DATE
);

INSERT INTO clientes (nombre, fecha_nacimiento) VALUES
('Luis Martínez', '1990-06-15'),
('María López', '1985-09-20'),
('Pedro Gómez', '2000-03-10');
🔹 Caso 3: Formatear Números de Teléfono
🧩 Escenario:
En CallCenter Solutions, los números de teléfono están almacenados sin formato y se necesita presentarlos en el formato (XXX) XXX-XXXX.

✅ Tarea:
Crea una función llamada formatear_telefono que reciba un número de teléfono en formato XXXXXXXXXX y lo devuelva en formato (XXX) XXX-XXXX.

Usa la función en un SELECT sobre la tabla contactos.

🔹 Caso 4: Clasificación de Productos por Precio
🧩 Escenario:
En la tienda E-Shop, los productos se categorizan en tres niveles según su precio:

Bajo: Menos de 50 USD.

Medio: Entre 50 y 200 USD.

Alto: Más de 200 USD.

✅ Tarea:
Crea una función llamada clasificar_precio que reciba un DECIMAL(10,2) y devuelva un VARCHAR(10) con la clasificación del producto (Bajo, Medio, Alto).

Usa la función en un SELECT sobre la tabla productos.