![Logo de la aplicación](/logo_gastAPP.png)
# Documentación del Proyecto: gastAPP Desktop

[Descargar gastAPP Beta Aquí](https://github.com/Clickaton/proyecto-final-gastAPP/releases/download/gastAPP_1.0.0b/gastAPP1.0.0b.zip)

## *1. Introducción al Proyecto*

**gastAPP Desktop** es una aplicación de escritorio diseñada para la **gestión integral de finanzas personales y profesionales**,
permitiendo almacenar, clasificar y analizar de manera clara y organizada los activos, pasivos, ingresos y gastos de los usuarios.  
El objetivo principal es ofrecer una herramienta que **simplifique la administración financiera**, adaptándose tanto a usuarios con
conocimientos financieros básicos como también a aquellos más profesionales que requieren un control más detallado.


![demo1](/demo1.gif)

![demo2](/demo2.gif)


---



## *2. Alcance del Proyecto*

El proyecto cubre las siguientes funcionalidades:

* Registro y gestión de **usuarios**.
* Administración de **cuentas** (Activos y Pasivos) y **movimientos financieros** (Ingresos y Gastos).
* Generación de **estadísticas y reportes** para análisis financiero.
* Alertas automáticas de vencimientos, movimientos pendientes o límites de gasto.
* Registro de pagos y liquidación de pasivos, incluyendo tarjetas de crédito, préstamos u otras deudas.

El sistema se diseñará con **interfaz amigable y sencilla**, para facilitar su uso por todo tipo de usuarios.



---



## *3. Características Principales*

* Gestión de **Usuarios**: Administración de permisos y accesos.
* Gestión de **Cuentas y Movimientos**: Registro de activos, pasivos, ingresos y gastos.
* **Reportes y Estadísticas**: Visualización de resúmenes mensuales, gráficos y alertas.
* **Alertas Automáticas**: Notificaciones sobre vencimientos y movimientos críticos.
* Interfaz **intuitiva** y adaptable a usuarios con distintos niveles de experiencia.
* Base de datos **local** con soporte para SQLite, permitiendo movilidad y facilidad de instalación.



---



## *4. Plataformas y Tecnologías*

* **Lenguaje y entorno de desarrollo:** C# con Visual Studio 2022 o superior.
* **Base de datos:** SQLite (principal) o MySQL (opcional para entornos multiusuario).
* **Interfaz de usuario:** Windows Forms o WPF, con un diseño claro y sencillo.
* **Compatibilidad:** Sistemas Windows (10/11).



---



## *5. Usuarios Objetivo*

* **Usuarios particulares:** Personas que desean controlar sus gastos e ingresos personales o familiares.
* **Profesionales y contadores:** Personas que requieren un control más detallado de activos, pasivos e ingresos/gastos.
* **Pequeñas empresas:** Que necesiten un registro básico de flujo de dinero y control de pagos.



---



## *6. Casos de Uso*



### Caso de Uso 1: Gestión de Usuarios

* **Actor principal:** Usuario (root).
* **Actores secundarios:** Sistema (valida datos).
* **Descripción:** Permite crear, editar, recuperar y eliminar usuarios.
* **Flujo principal:**

  1. El Usuario si no existe, puede registrarse en el panel de inicio.
  2. Usuario inicia sesión con credenciales personales.
  3. Accede a la sección de “Gestión de Usuario”.
  4. Selecciona “Modificar Usuario”, ingresa datos (nombre, email, contraseña).
  5. El sistema valida los datos y confirma modificación exitosa.

* **Flujos Alternativos:**

  * Usuario registrado → sistema muestra mensaje de registro exitoso.
  * Datos incompletos → sistema muestra error y no permite continuar.
  * Usuario ya existe → se muestra mensaje de duplicado.
  * Contraseña débil → sistema solicita contraseña más segura.



---



### Caso de Uso 2: Cargar Cuenta

* **Actor principal:** Usuario.
* **Actores secundarios:** Sistema (valida datos).
* **Precondiciones:** Usuario autenticado.
* **Flujo principal:**

  1. Usuario selecciona “Crear Cuenta”.
  2. Ingresa nombre de la cuenta y tipo (Activo o Pasivo).
  3. Sistema valida que no exista otra cuenta con el mismo nombre.
  4. Registro exitoso y saldo inicial opcional.

* **Flujos alternativos:**

  * Nombre duplicado → mensaje de error.
  * Datos incompletos → error de validación.



---



### Caso de Uso 3: Registrar Movimiento

* **Actor principal:** Usuario.
* **Actores secundarios:** Sistema (valida saldo y actualiza cuentas).
* **Precondiciones:** Usuario autenticado, cuenta y categoría registradas.
* **Flujo principal:**

  1. Usuario selecciona “Registrar Movimiento”.
  2. Elige cuenta y categoría (Ingreso o Gasto).
  3. Ingresa monto, fecha y descripción.
  4. Sistema actualiza saldo de la cuenta automáticamente.
  5. Sistema confirma registro exitoso.

* **Flujos alternativos:**

  * Monto inválido o negativo → error.
  * Cuenta o categoría no seleccionada → error de validación.



---



### Caso de Uso 4: Gestionar Estadísticas y Alertas

* **Actor principal:** Sistema (automático).
* **Actores secundarios:** Usuario (Visualiza en el panel).
* **Descripción:** Genera reportes visuales y notificaciones de movimientos importantes.
* **Flujo principal:**

  1. Sistema analiza movimientos registrados periódicamente.
  2. Genera estadísticas: ingresos, gastos, saldo por cuenta, gráficos mensuales.
  3. Detecta movimientos críticos: vencimientos de pasivos, límites de gasto, deudas próximas.
  4. Envía alertas al usuario mediante notificaciones dentro de la app.

* **Flujos alternativos:**

  * Datos insuficientes → sistema indica falta de información.
  * No hay alertas → sistema muestra mensaje “No hay alertas pendientes”.



---



### Caso de Uso 5: Gestionar Pagos de Pasivos

* **Actor principal:** Usuario.
* **Actores secundarios:** Sistema (actualiza saldo e historial).
* **Precondiciones:** Usuario autenticado, pasivo registrado con saldo pendiente.
* **Flujo principal:**

  1. Usuario selecciona “Registrar Pago de Pasivo”.
  2. Selecciona cuenta a debitar (Activo) y pasivo a pagar.
  3. Ingresa monto y fecha de pago.
  4. Sistema valida saldo disponible en la cuenta.
  5. Si es válido, actualiza saldo de pasivo y cuenta de origen.
  6. Sistema registra movimiento en historial y confirma operación.

* **Flujos alternativos:**

  * Saldo insuficiente → mensaje de error.
  * Pago parcial → sistema permite registrar saldo pendiente.
  * Datos incompletos → error de validación.



---



## 7\. Requisitos Funcionales y No Funcionales



## Requisitos Funcionales (RF)

1. RF1: Permitir creación, edición y eliminación de usuarios.
2. RF2: Registrar y gestionar cuentas (Activo/Pasivo).
3. RF3: Registrar movimientos financieros con categoría, fecha y descripción.
4. RF4: Actualizar automáticamente saldos de cuentas tras cada movimiento.
5. RF5: Generar reportes y estadísticas visuales (gráficos, tablas).
6. RF6: Emitir alertas automáticas sobre vencimientos, límites o movimientos críticos.
7. RF7: Registrar pagos de pasivos, incluyendo pagos parciales y totales.

### Requisitos No Funcionales (RNF)

1. RNF1: Interfaz intuitiva y fácil de usar para usuarios sin experiencia contable.
2. RNF2: Respuesta rápida del sistema, con tiempos de carga menores a 2 segundos por operación.
3. RNF3: Seguridad de datos mediante autenticación de usuarios y encriptación.
4. RNF4: Persistencia de datos confiable usando SQLite/MySQL.
5. RNF5: Compatibilidad con Windows 10 y 11.

RNF6: Mantenimiento sencillo y escalable para futuras mejoras o nuevas funcionalidades.


Diagrama de Clases

    class Usuario {
        -int Id
        -string Nombre
        -string Email
        -string Genero
        -string contrasena
    }
    
    class Cuenta {
        -int Id
        -string NumeroIdentificacion
        -decimal SaldoInicial
        -decimal SaldoActual
        -DateTime FechaCreacion
        -DateTime? FechaVencimiento
        -bool TieneCuotas
        -int CantidadCuotas
        -int CuotaActual
        -CuentaTipo CuentaTipo
        -Usuario Usuario
    }

    class Notificacion {
        -int id
        -string Titulo
        -string Descripcion
        -Usuario Usuario
        -DateTime Fecha
    }
    
    class CuentaTipo {
        -int Id
        -string Nombre
        -string Tipo
    }
    
    class Movimiento {
        -int Id
        -decimal Monto
        -Categoria categoria
        -string descripcion
        -DateTime Fecha
        -Cuenta Cuenta
        -Usuario Usuario
        -string NumeroIdentificacion
    }

    class Categoria {
        -int id
        -string Nombre
        -string Tipo
        -string descripcion
    }
    
    class Conexion {
        +static Conexion getInstancia()
        +SQLiteConnection CrearConexion()
    }

    Servicios:

    class UsuarioDAL {
        +static bool Registrar(...)
        +static Usuario Login(...)
        +static bool ExisteUsuarioPorNombre(...)
        +static bool EliminarUsuarioPorId(int id)
    }

    class CuentaDAL {
        +static List~Cuenta~ ListarCuentas(Usuario)
        +static List~Cuenta~ ListarCuentasPorVencerEnRango(int dias)
        +static bool crearCuenta(Cuenta)
        +static bool EliminarCuenta(...)
        +static Cuenta buscarCuentaPorId(int id)
    }

    class MovimientoDAL {
        +static List~Movimiento~ ListarMovimientosPorCuenta(Cuenta)
        +static bool EliminarMovimiento(int id)
    }

    class NotificacionService {
        +static void crearNotificacion(NotifyIcon, ...)
        +static DialogResult crearMessageBox(...)
    }

    class CuentaService {
        +static void registrarCuenta(...)
        +static void actualizarCuenta(...)
        +static void eliminarCuenta(DataGridView, ...)
        +static void listarCuentas(DataGridView, ...)
        +static bool modificarVerificarSaldoActual(Cuenta, ..., Movimiento)
        +static List~Cuenta~ verificarVencimientoCuentas(int dias)
    }

    class MovimientoService {
        +static void registrarMovimiento(...)
        +static void listarMovimientos(DataGridView, ...)
        +static bool CoordinarTransferencia(Movimiento, ...)
        +static bool EliminarMovimientoYRevertirSaldo(int id)
        +static void eliminarMovimiento(DataGridView, ...)
        +static List~Movimiento~ listarMovimientosPorCuenta(Cuenta)
    }
    
    class UsuarioService {
        +static bool eliminarUsuario(int id)
        +static bool validarUsuarioRegistro(String nombre)
        +static bool validarMailRegistro(String mail)
    }
    
    class CronJob {
        -static Dictionary~int, DateTime~ UltimaNotificacionEnviada
        +static Task tareaAutoprogramadaNotificacion(NotifyIcon, Usuario)
        -static void VerificarYNotificarVencimientos(...)
    }

    %% RELACIONES %%

    %% 1. Relaciones de Agregación/Composición (Entidades)
    Cuenta "1" *-- "1" CuentaTipo : tiene
    Cuenta "1" *-- "1" Usuario : pertenece_a
    Movimiento "N" *-- "1" Cuenta : afecta_a
    Movimiento "N" *-- "1" Usuario : pertenece_a

    %% 2. Relaciones de Dependencia (DAL depende de Entidades y Conexión)
    UsuarioDAL ..> Usuario :  crear /consultar /registrar /listar
    CuentaDAL ..> Cuenta :  crear /consultar /registrar /listar
    CuentaDAL ..> CuentaTipo :  crear /consultar /registrar /listar
    MovimientoDAL ..> Movimiento : crear /consultar /registrar /listar
    UsuarioDAL ..> Conexion : usa
    CuentaDAL ..> Conexion : usa
    MovimientoDAL ..> Conexion : usa
    NotificacionDAL ..> Conexion : usa
    
    %% 3. Relaciones de Uso (Servicios y CronJob)
    CronJob ..> CuentaDAL : consulta vencimientos
    CronJob ..> Usuario : usa sesion
    CronJob ..> NotificacionService : envía notif.
    
    %% 4. Dependencia de servicios (CuentaDAL usa NotificacionService para mensajes de error)
    CuentaDAL ..> NotificacionService : envia notif.
    MovimientoDAL y NotificacionDAL envia notif.



