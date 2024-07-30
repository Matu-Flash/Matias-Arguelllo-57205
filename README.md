# Matias-Arguelllo-57205
-- Crear la base de datos
CREATE DATABASE PedidosYaDB;

-- Usar la base de datos
USE PedidosYaDB;

-- Tabla Clientes
CREATE TABLE Clientes (
    ID_Cliente INT PRIMARY KEY,
    Nombre VARCHAR(100),
    Telefono VARCHAR(15),
    Edad INT,
    Localidad VARCHAR(100)
);

-- Tabla Proveedores
CREATE TABLE Proveedores (
    ID_Supplier INT PRIMARY KEY,
    Nombre VARCHAR(100),
    Localidad VARCHAR(100)
);

-- Tabla Productos
CREATE TABLE Productos (
    ID_SKU INT PRIMARY KEY,
    Nombre VARCHAR(100),
    Costo DECIMAL(10,2),
    Stock INT,
    Categoria VARCHAR(50),
    ID_Proveedor INT,
    Precio DECIMAL(10,2),
    FOREIGN KEY (ID_Proveedor) REFERENCES Proveedores(ID_Supplier)
);

-- Tabla Ventas
CREATE TABLE Ventas (
    ID_Order INT PRIMARY KEY,
    Monto_Total DECIMAL(10,2),
    Localidad VARCHAR(100),
    ID_Cliente INT,
    Cantidad INT,
    FOREIGN KEY (ID_Cliente) REFERENCES Clientes(ID_Cliente)
);

-- Tabla Detalle_Venta para manejar la relación muchos-a-muchos
CREATE TABLE Detalle_Venta (
    ID_Order INT,
    ID_SKU INT,
    Cantidad INT,
    PRIMARY KEY (ID_Order, ID_SKU),
    FOREIGN KEY (ID_Order) REFERENCES Ventas(ID_Order),
    FOREIGN KEY (ID_SKU) REFERENCES Productos(ID_SKU)
);
