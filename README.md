```sql
CREATE TABLE pais (
    id_pais INT PRIMARY KEY,
    nombre VARCHAR(100)
);

CREATE TABLE region (
    id_region INT PRIMARY KEY,
    nombre VARCHAR(100),
    id_pais INT,
    FOREIGN KEY (id_pais) REFERENCES pais(id_pais)
);

CREATE TABLE ciudad (
    id_ciudad INT PRIMARY KEY,
    nombre VARCHAR(100),
    id_region INT,
    FOREIGN KEY (id_region) REFERENCES region(id_region)
);

CREATE TABLE proveedores (
    id_proveedor INT PRIMARY KEY,
    nombre VARCHAR(100),
    telefono VARCHAR(15),
    email VARCHAR(100),
    id_repuesto INT,
    FOREIGN KEY (id_repuesto) REFERENCES repuestos(id_repuesto)
);

CREATE TABLE repuestos (
    id_repuesto INT PRIMARY KEY,
    nombre VARCHAR(100),
    precio DECIMAL(10, 2)
);

CREATE TABLE clientes (
    id_cliente INT PRIMARY KEY,
    nombre VARCHAR(100),
    direccion VARCHAR(200),
    telefono VARCHAR(15),
    email VARCHAR(100),
    id_ciudad INT,
    FOREIGN KEY (id_ciudad) REFERENCES ciudad(id_ciudad)
);

CREATE TABLE empleados (
    id_empleado INT PRIMARY KEY,
    nombre VARCHAR(100),
    rol ENUM('vendedor', 'mecanico', 'servicio_cliente'),
    id_sucursal INT,
    FOREIGN KEY (id_sucursal) REFERENCES sucursales(id_sucursal)
);

CREATE TABLE sucursales (
    id_sucursal INT PRIMARY KEY,
    nombre VARCHAR(100),
    id_ciudad INT,
    FOREIGN KEY (id_ciudad) REFERENCES ciudad(id_ciudad)
);

CREATE TABLE productos (
    id_producto INT PRIMARY KEY,
    nombre VARCHAR(100),
    tipo_producto ENUM('bicicleta', 'repuesto'),
    precio DECIMAL(10, 2),
    stock INT
);

CREATE TABLE stock (
    id_stock INT PRIMARY KEY,
    id_producto INT,
    id_proveedor INT,
    cantidad INT,
    FOREIGN KEY (id_producto) REFERENCES productos(id_producto),
    FOREIGN KEY (id_proveedor) REFERENCES proveedores(id_proveedor)
);

CREATE TABLE compras (
    id_compra INT PRIMARY KEY,
    id_proveedor INT,
    id_producto INT,
    cantidad INT,
    precio_unitario DECIMAL(10, 2),
    total DECIMAL(10, 2),
    fecha_compra DATE,
    FOREIGN KEY (id_proveedor) REFERENCES proveedores(id_proveedor),
    FOREIGN KEY (id_producto) REFERENCES productos(id_producto)
);

CREATE TABLE ventas (
    id_venta INT PRIMARY KEY,
    id_cliente INT,
    id_empleado INT,
    id_sucursal INT,
    fecha_venta DATE,
    total DECIMAL(10, 2),
    FOREIGN KEY (id_cliente) REFERENCES clientes(id_cliente),
    FOREIGN KEY (id_empleado) REFERENCES empleados(id_empleado),
    FOREIGN KEY (id_sucursal) REFERENCES sucursales(id_sucursal)
);

CREATE TABLE facturacion (
    id_factura INT PRIMARY KEY,
    id_venta INT,
    id_fecha DATE,
    monto DECIMAL(10, 2),
    FOREIGN KEY (id_venta) REFERENCES ventas(id_venta)
);

CREATE TABLE pagos (
    id_pago INT PRIMARY KEY,
    id_venta INT,
    metodo_pago ENUM('tarjeta', 'contado'),
    monto_pago DECIMAL(10, 2),
    date DATE,
    FOREIGN KEY (id_venta) REFERENCES ventas(id_venta)
);

CREATE TABLE cuentas_por_saldar (
    id_cuenta_por_saldar INT PRIMARY KEY,
    id_proveedor INT,
    monto_pendiente DECIMAL(10, 2),
    fecha_vencimiento DATE,
    FOREIGN KEY (id_proveedor) REFERENCES proveedores(id_proveedor)
);

```
Hecho por (jhorman jesus castellanos morales )

> [!NOTE]
> complicaciones 

> [!TIP]
> 

> [!IMPORTANT]  
> se encuntra culminado 

> [!WARNING]  
> 

> [!CAUTION]
>
