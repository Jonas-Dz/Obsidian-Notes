## Uso

Sirven para consultar o generar los datos
Los índices hago en base a una columna o un campo

```sql
SELECT 
	i.name AS NombreIndice,
	i.type_desc AS TipoIndice,
	OBJECT_NAME(i.object_id) AS Tabla
FROM sys.indexes i
WHERE OBJECT_NAME(i.object_id) = 'Person';
```

Crear índices
```sql
CREATE NONCLUSTERED INDEX IX_Person_LastName
ON Person.Person(LastName);
GO 
```

Ver estadísticas de manera exacta
```sql
SET STATISTICS IO ON
SET STATISTICS TIME ON
```

Índice no agrupado compuesto
```sql
CREATE NONCLUSTERED INDEX IX_Person_Last_First
ON Person.Person(LastName, FirstName);
GO
```

Crear una nueva tabla para un ID único
```sql
CREATE TABLE EmpleadoPrueba(
	IdEmpleado INT IDENTITY(1,1),
	Cedula VARCHAR(10),
	Nombre VARCHAR(100)
);
GO

CREATE UNIQUE INDEX IX_Empleado_Cedula
ON EmpleadoPrueba(Cedula);
GO
```

Crear Tabla Ventas
```sql
CREATE TABLE VentasPrueba(
	IdVenta INT IDENTITY (1,1),
	Cliente VARCHAR(100),
	Estado VARCHAR(20),
	Monto DECIMAL(10,2)
);
GO
```

Insertar valores en Venta
```sql
INSERT INTO VentasPrueba
VALUES
	('Juan Perez', 'Pagado', 1000),
	('Andy Conteron', 'Pagado', 2000),
	('Tefa Pincha', 'Pendiente', 3000),
	('Jonathan Diaz', 'Pendiente', 1000),
	('Juan Gutierrez', 'Pagado', 500);
GO
```


Crear índice
```sql
CREATE NONCLUSTERED INDEX IX_Ventas_Pagadas
ON VentasPrueba(Estado)
WHERE Estado = 'Pagado'
GO 
```

Búsqueda mediante ese estado
```sql
SELECT *
FROM VentasPrueba
WHERE Estado = 'Pagado';
GO
```

Eliminar un índice
```sql
DROP INDEX IX_Person_LastName
ON Person.Person
GO
```