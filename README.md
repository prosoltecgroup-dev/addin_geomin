# PST AutoCAD Tools - Minería y Geología ⛏️🌍

Una suite de complementos (Add-ins) desarrollados en C# y .NET para AutoCAD, diseñados específicamente para agilizar el trabajo de ingenieros de minas y geólogos. Esta herramienta automatiza el diseño de labores subterráneas y la proyección de estructuras geológicas mediante cálculos trigonométricos 3D precisos.

## 🚀 Módulos Principales

### 1. Módulo de Obras Lineales (PST Linear Works)
Herramienta de diseño continuo para rampas, túneles y galerías con control exacto de gradientes.
* **Tramos Rectos:** Cálculo de coordenadas 3D basado en longitud de hipotenusa, azimut y pendiente (% o grados).
* **Tramos Curvos:** Generación de curvas en espiral 3D configurables por radio, ángulo central o longitud de arco, con segmentación inteligente para optimizar el rendimiento de AutoCAD.
* **Continuidad Matemática:** Implementa un caché de precisión interna que elimina los errores de redondeo al empalmar múltiples tramos.
* **Etiquetado Automático:** Genera textos de gradiente en la capa correspondiente automáticamente.

### 2. Módulo de Mapeo Geológico (PST GeoMapper)
Digitalización inteligente de estructuras en planta.
* Interfaz fluida mediante paletas anclables (PaletteSet).
* Inserción de trazas estructurales con control de orientación.
* Almacenamiento de metadatos (Tipo de roca, Potencia, Azimut) directamente en la geometría usando **XData**, permitiendo que el dibujo contenga información de base de datos.

### 3. Módulo de Proyección Geológica (PST GeoProjector)
Motor de proyección estructural 3D basado en la Regla de la Mano Derecha (RHR).
* Toma líneas o polilíneas 2D/3D existentes en un nivel topográfico.
* Calcula el desplazamiento horizontal requerido según el buzamiento, dirección de buzamiento (Dip Direction) y la cota destino (o distancia vertical).
* Clona y transforma la geometría original manteniendo su forma exacta (incluyendo arcos) en la nueva elevación espacial.

## 🛠️ Arquitectura y Tecnologías
* **Lenguaje:** C#
* **Framework:** .NET Framework 4.8 (Compatible de forma implícita con .NET 8 / Core en AutoCAD 2025).
* **UI:** Windows Forms (WinForms) con diseño responsivo usando `FlowLayoutPanel` y ventanas modales de AutoCAD (`ShowModalDialog`) para evitar pérdida de foco.
* **Patrones:** Arquitectura modular separando la Interfaz de Usuario (UI), la Lógica Matemática (Core/GeoCalc) y los Modelos de Negocio.
* **Manejo de Transacciones:** Implementación segura de `DocumentLock` y `TransactionManager` previniendo errores de concurrencia (`eLockViolation`).

## 💻 Instalación y Uso

1. Descarga la última versión compilada (archivo `.dll`) desde la sección de Releases.
2. Abre AutoCAD.
3. Escribe el comando `NETLOAD` en la barra de comandos y selecciona el archivo `.dll`.
4. Utiliza los siguientes comandos para abrir las paletas de herramientas:
   * `AbrirEjesLineales` -> Diseño de Rampas y Labores.
   * `AbrirGeoMapper` -> Mapeo Estructural.
   * `AbrirProyectorGeo` -> Proyección de Vetas/Fallas.

## ⚠️ Notas de Compatibilidad
El plugin ha sido compilado en .NET Framework 4.8 para asegurar compatibilidad con versiones como AutoCAD 2021-2024. Su ejecución en AutoCAD 2025+ (.NET 8) es funcional gracias a la compatibilidad implícita de Windows Desktop, pero se recomienda migrar el `.csproj` a SDK Style para entornos estrictamente modernos.
