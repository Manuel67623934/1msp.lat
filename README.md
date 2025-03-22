# MSSQL

# Creación y Población de la Base de Datos "acme-company"

Este documento resume las instrucciones SQL utilizadas para crear y poblar la base de datos "acme-company".

```
CREATE DATABASE "acme-company";

USE "acme-company";

CREATE TABLE Clientes (
    ClienteID INT PRIMARY KEY,
    Nombre VARCHAR(50) NOT NULL,
    Apellido VARCHAR(50) NOT NULL,
    Email VARCHAR(100) UNIQUE,
    Telefono VARCHAR(20),
    Direccion VARCHAR(255)
);

INSERT INTO Clientes (ClienteID, Nombre, Apellido, Email, Telefono, Direccion)
VALUES
    (1, 'Juan', 'Pérez', 'juan.perez@ejemplo.com', '555-1234', 'Calle 1, Ciudad'),
    (2, 'María', 'Gómez', 'maria.gomez@ejemplo.com', '555-5678', 'Avenida 2, Ciudad'),
    (3, 'Carlos', 'Rodríguez', 'carlos.rodriguez@ejemplo.com', '555-9012', 'Calle 3, Ciudad'),
    (4, 'Laura', 'López', 'laura.lopez@ejemplo.com', '555-3456', 'Avenida 4, Ciudad'),
    (5, 'Pedro', 'Martínez', 'pedro.martinez@ejemplo.com', '555-7890', 'Calle 5, Ciudad'),
    (6, 'Ana', 'Sánchez', 'ana.sanchez@ejemplo.com', '555-2345', 'Avenida 6, Ciudad'),
    (7, 'Luis', 'Ramírez', 'luis.ramirez@ejemplo.com', '555-6789', 'Calle 7, Ciudad'),
    (8, 'Sofía', 'Torres', 'sofia.torres@ejemplo.com', '555-0123', 'Avenida 8, Ciudad'),
    (9, 'Diego', 'Díaz', 'diego.diaz@ejemplo.com', '555-4567', 'Calle 9, Ciudad'),
    (10, 'Isabel', 'Ruiz', 'isabel.ruiz@ejemplo.com', '555-8901', 'Avenida 10, Ciudad');

CREATE TABLE Facturas (
    FacturaID INT PRIMARY KEY,
    ClienteID INT FOREIGN KEY REFERENCES Clientes(ClienteID),
    FechaFactura DATE NOT NULL,
    Monto DECIMAL(10, 2) NOT NULL,
    Descripcion VARCHAR(255)
);

CREATE TABLE Pagos (
    PagoID INT PRIMARY KEY,
    FacturaID INT FOREIGN KEY REFERENCES Facturas(FacturaID),
    FechaPago DATE NOT NULL,
    Monto DECIMAL(10, 2) NOT NULL,
    MetodoPago VARCHAR(50)
);

CREATE TABLE Empleados (
    EmpleadoID INT PRIMARY KEY,
    Nombre VARCHAR(50) NOT NULL,
    Apellido VARCHAR(50) NOT NULL,
    Email VARCHAR(100) UNIQUE,
    Telefono VARCHAR(20),
    Departamento VARCHAR(50),
    FechaContratacion DATE
);

CREATE TABLE Salarios (
    SalarioID INT PRIMARY KEY,
    EmpleadoID INT FOREIGN KEY REFERENCES Empleados(EmpleadoID),
    SalarioBase DECIMAL(10, 2),
    FechaInicio DATE,
    FechaFin DATE
);

INSERT INTO Empleados (EmpleadoID, Nombre, Apellido, Email, Telefono, Departamento, FechaContratacion)
VALUES
    (1, 'Ana', 'García', 'ana.garcia@acme.com', '555-1111', 'RRHH', '2020-01-15'),
    (2, 'Carlos', 'Pérez', 'carlos.perez@acme.com', '555-2222', 'Contabilidad', '2019-05-20'),
    (3, 'Laura', 'Martínez', 'laura.martinez@acme.com', '555-3333', 'Ventas', '2021-03-01'),
    (4, 'Javier', 'Sánchez', 'javier.sanchez@acme.com', '555-4444', 'Marketing', '2022-08-10'),
    (5, 'Sofía', 'López', 'sofia.lopez@acme.com', '555-5555', 'RRHH', '2023-01-05'),
    (6, 'Miguel', 'Ramírez', 'miguel.ramirez@acme.com', '555-6666', 'Contabilidad', '2020-11-12'),
    (7, 'Isabel', 'Torres', 'isabel.torres@acme.com', '555-7777', 'Ventas', '2021-07-22'),
    (8, 'David', 'Díaz', 'david.diaz@acme.com', '555-8888', 'Marketing', '2022-04-01'),
    (9, 'Elena', 'Ruiz', 'elena.ruiz@acme.com', '555-9999', 'RRHH', '2023-09-18'),
    (10, 'Fernando', 'Álvarez', 'fernando.alvarez@acme.com', '555-0000', 'Contabilidad', '2019-12-03');

INSERT INTO Facturas (FacturaID, ClienteID, FechaFactura, Monto, Descripcion)
VALUES
    (1, 1, '2023-10-26', 150.00, 'Servicios de consultoría'),
    (2, 2, '2023-10-27', 220.50, 'Venta de productos'),
    (3, 3, '2023-10-28', 80.75, 'Mantenimiento de software'),
    (4, 4, '2023-10-29', 350.25, 'Publicidad en línea'),
    (5, 5, '2023-10-30', 120.00, 'Servicios de diseño'),
    (6, 6, '2023-10-31', 280.90, 'Venta de productos'),
    (7, 7, '2023-11-01', 95.50, 'Mantenimiento de hardware'),
    (8, 8, '2023-11-02', 400.00, 'Marketing digital'),
    (9, 9, '2023-11-03', 180.20, 'Servicios de traducción'),
    (10, 10, '2023-11-04', 250.75, 'Venta de productos');

INSERT INTO Pagos (PagoID, FacturaID, FechaPago, Monto, MetodoPago)
VALUES
    (1, 1, '2023-11-01', 150.00, 'Tarjeta de crédito'),
    (2, 2, '2023-11-02', 220.50, 'Transferencia bancaria'),
    (3, 3, '2023-11-03', 80.75, 'Efectivo'),
    (4, 4, '2023-11-04', 350.25, 'Tarjeta de débito'),
    (5, 5, '2023-11-05', 120.00, 'PayPal'),
    (6, 6, '2023-11-06', 280.90, 'Tarjeta de crédito'),
    (7, 7, '2023-11-07', 95.50, 'Transferencia bancaria'),
    (8, 8, '2023-11-08', 400.00, 'Efectivo'),
    (9, 9, '2023-11-09', 180.20, 'Tarjeta de débito'),
    (10, 10, '2023-11-10', 250.75, 'PayPal');
```

