# LENGUAE-PRO-2-COPPEL-DAMARIS
 Crear base de datos
CREATE DATABASE IF NOT EXISTS COPPEL_MOD;
USE COPPEL_MOD;

-- Tabla centroTrabajo
CREATE TABLE centroTrabajo (
    noCentro VARCHAR(6) PRIMARY KEY,
    nombreCentro VARCHAR(100) NOT NULL,
    ciudad VARCHAR(100) NOT NULL
);

-- Tabla puestos
CREATE TABLE puestos (
    noPuesto INT PRIMARY KEY,
    puesto VARCHAR(50),
    descripcion TEXT
);

-- Tabla Empleado
CREATE TABLE Empleado (
    noEmpleado INT AUTO_INCREMENT PRIMARY KEY,
    nombre VARCHAR(50),
    apellidoP VARCHAR(50),
    apellidoM VARCHAR(50),
    fechaNacimiento DATE,
    RFC VARCHAR(20),
    centroTrabajo VARCHAR(6),
    puesto INT,
    descripcionPuesto TEXT,
    directivo TINYINT(1),
    FOREIGN KEY (centroTrabajo) REFERENCES centroTrabajo(noCentro),
    FOREIGN KEY (puesto) REFERENCES puestos(noPuesto)
);

-- Tabla Directivos
CREATE TABLE Directivos (
    noEmpleado INT PRIMARY KEY,
    numeroCentroSupervisa VARCHAR(6),
    prestaciones TINYINT(1),
    FOREIGN KEY (noEmpleado) REFERENCES Empleado(noEmpleado),
    FOREIGN KEY (numeroCentroSupervisa) REFERENCES centroTrabajo(noCentro)
);

-- Insert centroTrabajo
INSERT INTO centroTrabajo VALUES
('000201', 'Tiendas Angel Flores Ropa', 'Culiacan'),
('000202', 'Tiendas Angel Flores Muebles', 'Culiacan'),
('000203', 'Tiendas Angel Flores Cajas', 'Culiacan'),
('049001', 'La Primavera Ropa', 'Culiacan'),
('049002', 'La Primavera Muebles', 'Culiacan'),
('049003', 'La Primavera Cajas', 'Culiacan');

-- Insert puestos
INSERT INTO puestos VALUES
(1, 'Coordinador', 'coordinador etc etc etc'),
(2, 'Coordinador de piso', 'etc etc etc'),
(3, 'Director', 'etc etc etc');

-- Insert empleados
INSERT INTO Empleado (noEmpleado, nombre, apellidoP, apellidoM, fechaNacimiento, RFC, centroTrabajo, puesto, descripcionPuesto, directivo) VALUES
(2, 'Daniel', 'Diaz', 'Rossell', '2000-11-03', 'DDR001103', '000201', 1, '', 0),
(3, 'Juan', 'Perez', 'Perez', '1993-10-03', 'DDR931083', '000201', 3, '', 1),
(4, 'Marcos', 'Gomez', 'Arce', '1997-02-13', 'MGA12345', '000202', 1, '', 0),
(5, 'Armando', 'Gomez', 'Santiago', '1996-01-23', 'AGM12345', '000203', 1, '', 0),
(6, 'Andres', 'Blancas', 'Palacios', '1995-07-11', 'ABP12345', '049001', 1, '', 0),
(7, 'Angel', 'Montes', 'Reyes', '1983-06-30', 'AMR12345', '049002', 2, '', 1),
(8, 'Raul', 'Peredo', 'Estudillo', '1999-06-27', 'RPE12345', '049003', 2, '', 0),
(9, 'Diana', 'Aburto', 'Martinez', '2003-12-11', 'DAM12345', '000202', 2, '', 0),
(10, 'Carlos', 'Hernandez', 'Lopez', '2001-03-03', 'CHL12345', '000201', 3, '', 1),
(11, 'Martin', 'Suarez', 'Colins', '1999-04-09', 'MSC12345', '000203', 3, '', 1);

-- Insert directivos
INSERT INTO Directivos VALUES
(3, '000201', 1),sys_configsys_config
(7, '000202', 1),
(10, '000203', 1),
(11, '049003', 1);
