# Caso 1: Cálculo de Bonificaciones de Empleados

```sql
DELIMITER //

CREATE FUNCTION calcular_bonificacion(salario DECIMAL(10,2)) RETURNS DECIMAL(10,2)
DETERMINISTIC
READS SQL DATA
BEGIN
    DECLARE resultado DECIMAL(10,2);

    IF salario < 2000 THEN

        SET resultado = salario * 0.1;

    ELSEIF salario >= 2000 AND salario<= 5000 THEN

        SET resultado = salario * 0.07; 

    ELSE

        SET resultado = salario * 0.05;
    END IF;


    RETURN resultado;

END;
//
DELIMITER ;
```

## consulta

```sql
SELECT nombre , salario, calcular_bonificacion(salario) AS bonificacion
FROM empleados;
```


#  Caso 2: Cálculo de Edad de Clientes

```sql
DELIMITER //
CREATE FUNCTION calcular_edad(fecha_nacimiento DATE) RETURNS INT
DETERMINISTIC
READS SQL DATA
BEGIN
    DECLARE  edad INT;
    
    SET edad = TIMESTAMPDIFF(YEAR, fecha_nacimiento, CURDATE());

    RETURN edad;
END;

//

DELIMITER ;

```
## CONSULTA

```sql
SELECT nombre, fecha_nacimiento, calcular_edad(fecha_nacimiento) AS edad
FROM clientes;
```

# Caso 3: Formatear Números de Teléfono

## tabla y inser

```sql
CREATE TABLE contactos (
    id INT PRIMARY KEY AUTO_INCREMENT,
    nombre VARCHAR(50),
    telefono VARCHAR(10) -- Guardado sin guiones ni paréntesis
);

INSERT INTO contactos (nombre, telefono) VALUES
('Laura Sánchez', '3124567890'),
('Mario Castro', '3001234567'),
('Paula Rivas', '3159876543');
```

## funcion

```sql
DELIMITER //
 CREATE FUNCTION formatear_telefono(numero VARCHAR(10))  RETURNS VARCHAR(14)
 DETERMINISTIC
 BEGIN 
    RETURN CONCAT('(',
                    SUBSTRING(numero, 1,3),')',
                    SUBSTRING(numero, 4,3),'-',
                    SUBSTRING(numero, 7,4));
END;
//
DELIMITER ;
```

## COSULTA
```sql
SELECT nombre, telefono, formatear_telefono(telefono) AS telefono_formateado
FROM contactos;
```

# Caso 4: Clasificación de Productos por Precio

## tabla y inser

```sql
CREATE TABLE productos (
    id INT PRIMARY KEY AUTO_INCREMENT,
    nombre VARCHAR(50),
    precio DECIMAL(10,2)
);

INSERT INTO productos (nombre, precio) VALUES
('Audífonos', 25.00),
('Teclado mecánico', 120.00),
('Portátil', 850.00),
('Mouse', 45.00),
('Tablet', 200.00);
```

## fuincion

```sql
DELIMITER //

CREATE FUNCTION clasificar_precio(precio DECIMAL(10,2))
RETURNS VARCHAR(10)
DETERMINISTIC
BEGIN
    DECLARE categoria VARCHAR(10);

    IF precio < 50 THEN
        SET categoria = 'Bajo';
    ELSEIF precio <= 200 THEN
        SET categoria = 'Medio';
    ELSE
        SET categoria = 'Alto';
    END IF;

    RETURN categoria;
END;
//

DELIMITER ;
```

## consulta

```sql
SELECT nombre, precio, clasificar_precio(precio) AS categoria
FROM productos;
```