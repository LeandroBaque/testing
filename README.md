# testing

## Base de datos configurada

Este proyecto está configurado para usar MySQL a través de JPA/Hibernate.

### Configuración

En [apirest/src/main/resources/application.properties](g9-latam-team08-testing/apirest/src/main/resources/application.properties) se define:

- URL de conexión MySQL: `jdbc:mysql://tokaido.proxy.rlwy.net:3306/railway`
- usuario: `root`
- driver: `com.mysql.cj.jdbc.Driver`
- `spring.jpa.hibernate.ddl-auto=update`

Esto significa que Hibernate intentará crear o actualizar tablas automáticamente en la base de datos conectada.

### Tablas mapeadas

#### 1. clientes_financiero

Se define en [apirest/src/main/java/team08/apirest/models/UsuarioModel.java](g9-latam-team08-testing/apirest/src/main/java/team08/apirest/models/UsuarioModel.java) con `@Table(name = "clientes_financiero")`.

Campos principales:

- `id_cliente` (PK)
- `nombre`
- `password`
- `email`
- `ingreso_mensual_fijo`
- `ingreso_mensual_variable`
- `ingreso_mensual`
- `gastos_esenciales_mensuales`
- `gastos_no_esenciales_mensuales`
- `gastos_totales_del_mes`
- `cuotas_mensuales_deuda`
- `ahorro_mensual`
- `ahorro_total`
- `ratio_ahorro_neto`
- `ratio_endeudamiento_dti`
- `gastos_esenciales_ratio`
- `gastos_estilo_vida_ratio`
- `meses_supervivencia`
- `frecuencia_transacciones_ocio`
- `perfil_financiero`
- `modalidad_pago_tarjeta`
- `ahorro_previo`

La entidad también tiene una relación `@OneToMany` con los gastos del cliente.

#### 2. gastos

Se define en [apirest/src/main/java/team08/apirest/models/GastoModel.java](g9-latam-team08-testing/apirest/src/main/java/team08/apirest/models/GastoModel.java).

Campos principales:

- `id_gasto` (PK)
- `nombre_tienda`
- `subcategoria`
- `monto`
- `metodo_pago`
- `esencial`
- `categoria_principal`
- `id_cliente` (FK hacia `clientes_financiero`)

### Resumen

Hay una base de datos MySQL configurada y el proyecto usa JPA para mapear entidades a tablas. La estructura principal es:

- `clientes_financiero`
- una tabla de gastos relacionada con dicho cliente por `id_cliente`

No hay scripts SQL manuales en el repositorio; las tablas se crean/actualizan automáticamente con Hibernate.
