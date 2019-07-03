---
title: Asistente para consumidores OLE DB ATL
ms.date: 07/02/2019
helpviewer_keywords:
- ATL projects, adding ATL OLE DB consumers
ms.assetid: dcb68ed1-2224-422f-9f7b-108a74864204
ms.openlocfilehash: 7195d712474765258ac0319539697b3517cb91b3
ms.sourcegitcommit: 9b904e490b1e262293a602bd1291a8f3045e755b
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 07/03/2019
ms.locfileid: "67552224"
---
# <a name="atl-ole-db-consumer-wizard"></a>Asistente para consumidores OLE DB ATL

::: moniker range="vs-2019"

Este asistente no está disponible en Visual Studio 2019 ni en versiones posteriores.

::: moniker-end

::: moniker range="<=vs-2017"

Este asistente configura una clase de consumidor OLE DB con los enlaces de datos necesario para tener acceso al origen de datos especificado a través del proveedor OLE DB determinado.

> [!NOTE]
> Este asistente requiere que haga clic en el botón **Origen de datos** para seleccionar un origen de datos antes de escribir los nombres en los campos de `Class` y del archivo **.h**.

## <a name="uielement-list"></a>Lista de UIElement

- **Origen de datos**

   El botón **Origen de datos** permite configurar el origen de datos especificado mediante el proveedor OLE DB determinado. Al hacer clic en este botón, el cuadro de diálogo **Propiedades de vínculo de datos** aparece. Para obtener más información sobre la creación de cadenas de conexión y el cuadro de diálogo **Propiedades de vínculo de datos**, vea [Información general sobre la API de vínculo de datos](/previous-versions/windows/desktop/ms718102(v=vs.85)) en la documentación de Windows SDK.

   La siguiente información adicional describe las pestañas en el cuadro de diálogo **Propiedades de vínculo de datos**.

   - Pestaña **Proveedor**

      Seleccione el proveedor apropiado para administrar la conexión al origen de datos. El tipo de proveedor normalmente viene determinado por el tipo de base de datos al que se está conectando. Haga clic en el botón **Siguiente** o haga clic en la pestaña **Conexión**.

   - Pestaña **Conexión**

      El contenido de esta pestaña depende del proveedor seleccionado. Aunque hay muchos tipos de proveedores, en esta sección se tratan las conexiones de los dos más comunes: Datos de SQL y ODBC. Los demás son variaciones similares de los campos que se describen aquí.

      Para datos de SQL:

      1. **Seleccionar o especificar un nombre de servidor:** Haga clic en el menú de lista desplegable para mostrar todos los servidores de datos registrados en la red y seleccionar uno.

      1. **Especificar información para iniciar sesión en el servidor:** Escriba un nombre de usuario y una contraseña para acceder al servidor de datos.

         > [!NOTE]
         > Hay un problema de seguridad con la característica de permitir la guardar contraseña del cuadro de diálogo Propiedades de vínculo de datos. En "Especificar información para iniciar sesión en el servidor", hay dos botones de radio:
         >
         > - **Usar seguridad integrada de Windows NT**
         > - **Usar un nombre de usuario y contraseña específicos**
         >
         > Si selecciona **Usar un nombre de usuario y contraseña específicos**, tiene la opción de guardar la contraseña (mediante la casilla de verificación para "Permitir guardar contraseña"); sin embargo, esta opción no es segura. Se recomienda que seleccione **Usar seguridad integrada de Windows NT**; esta opción es segura porque cifra la contraseña.
         > Puede haber situaciones en las que desea seleccionar "Permitir guardar contraseña". Por ejemplo, si está lanzando una biblioteca con una solución de base de datos privada, no debe tener acceso directamente a la base de datos, pero en su lugar, use una aplicación de nivel intermedio para comprobar el usuario (a través de cualquier esquema de autenticación que elija) y, a continuación, limite el tipo de datos disponible para el usuario.

      1. **Crear una base de datos en el servidor:** Haga clic en el menú de lista desplegable para mostrar todas las bases de datos registradas en el servidor de datos y seleccione una.

         \- o -

         **Adjuntar archivo de base de datos como nombre:** Especifique un archivo que se usará como la base de datos. Escriba la ruta de acceso explícita.

      Para datos de ODBC:

      1. **Especificar el origen de los datos:** Puede usar un nombre de origen de los datos o una cadena de conexión.

         **Usar el nombre del origen de los datos:** Esta lista desplegable muestra los orígenes de datos registrados en su máquina. Puede configurar los orígenes de datos antes de tiempo mediante el Administrador de orígenes de datos ODBC.

         \- o -

         **Usar cadena de conexión:** Escriba una cadena de conexión que ya ha obtenido o haga clic en el botón **Compilar**. Se muestra el cuadro de diálogo **Seleccionar origen de datos**. Seleccione un origen de datos de máquina y haga clic en **Aceptar**.

         > [!NOTE]
         > Puede obtener una cadena de conexión visualizando las propiedades de una conexión existente en el **Explorador de servidores**, o bien puede crear una conexión haciendo doble clic en **Agregar conexión** en **Explorador de servidores**.

      1. **Especificar información para iniciar sesión en el servidor:** Escriba un nombre de usuario y una contraseña para acceder al servidor de datos.

      1. Escriba el catálogo inicial que se usará.

      1. Haga clic en **Probar conexión**; si la prueba se realiza correctamente, haga clic en **Aceptar**. Si no es así, compruebe la información de inicio de sesión, pruebe con otra base de datos o con otro servidor de datos.

   - Pestaña **Opciones avanzadas**

      **Configuración de red:** Especifique el **nivel de suplantación** (el nivel de suplantación que el servidor está autorizado para usar al suplantar al cliente; se corresponde directamente con los niveles de suplantación de RPC) y el **nivel de protección** (el nivel de protección de datos enviados entre cliente y servidor; se corresponde directamente con los niveles de protección de RPC).

      **Otros**: En **Tiempo de espera de conexión**, especifique el número de segundos de tiempo de inactividad permitido antes de que se produzca un tiempo de espera. En **Permisos de acceso**, especifique los permisos de acceso en la conexión de datos.

      Para obtener más información sobre las propiedades de inicialización avanzadas, consulte la documentación suministrada con cada proveedor OLE DB.

   - Pestaña **Todo**

      Esta pestaña muestra un resumen de las propiedades de inicialización para el origen de datos y la conexión que ha especificado. Puede editar estos valores.

      Haga clic en **Aceptar** para terminar. Se muestra el cuadro de diálogo **Seleccionar objeto de base de datos**. En este cuadro de diálogo, seleccione la tabla, la vista o el procedimiento almacenado que va a usar el consumidor.

- **Clase**

   Después de seleccionar un origen de datos, este cuadro se rellena con un nombre de clase predeterminado basado en la tabla o el procedimiento almacenado que seleccionó (vea **Seleccionar un origen de datos** a continuación). Puede editar el nombre de la clase.

- **Archivo .h**

   Después de seleccionar un origen de datos, este cuadro se rellena con un nombre de clase de encabezado predeterminado basado en la tabla o el procedimiento almacenado que seleccionó (vea **Seleccionar un origen de datos** a continuación). Puede editar este nombre de archivo de encabezado o seleccionar un archivo de encabezado existente.

- **Con atributos**

   Esta opción especifica si el asistente creará clases de consumidor mediante atributos o declaraciones de plantilla. Al seleccionar esta opción, el asistente usa atributos en lugar de declaraciones de plantilla (esta es la opción predeterminada). Cuando se desactiva esta opción, el asistente utiliza las declaraciones de plantilla en lugar de atributos.

   - Si selecciona un **tipo** de consumidor de **Tabla**, el asistente usa los atributos `db_source` y `db_table` para crear la tabla y las declaraciones de clase del descriptor de acceso, y usa `db_column` para crear la asignación de columna. Por ejemplo, crea esta asignación:

        ```cpp
        // Inject table class and table accessor class declarations
        [db_source("<initialization_string>"), db_table("dbo.Orders")]
        ...
        // Column map
        [ db_column(1, status=m_dwOrderIDStatus, length=m_dwOrderIDLength) ] LONG m_OrderID;
        [ db_column(2, status=m_dwCustomerIDStatus, length=m_dwCustomerIDLength) ] TCHAR m_CustomerID[6];
        ...
        ```

      en lugar de usar la clase de plantilla `CTable` para declarar la tabla y la clase de descriptor de acceso de tabla, y las macros BEGIN_COLUMN_MAP y END_COLUMN_MAP para crear el mapa de columnas, como en este ejemplo:

        ```cpp
        // Table accessor class
            class COrdersAccessor; // Table class
            class COrders : public CTable<CAccessor<COrdersAccessor>>;
        // ...
        // Column map
            BEGIN_COLUMN_MAP(COrderDetailsAccessor)
                COLUMN_ENTRY_LENGTH_STATUS(1, m_OrderID, m_dwOrderIDLength, m_dwOrderIDStatus)
                COLUMN_ENTRY_LENGTH_STATUS(2, m_CustomerID, m_dwCustomerIDLength, m_dwCustomerIDStatus)
                // ...
            END_COLUMN_MAP()
        ```

   - Si selecciona un **tipo** de consumidor de **Comando**, el asistente usa los atributos `db_source` y `db_command`, y usa `db_column` para crear la asignación de columna. Por ejemplo, crea esta asignación:

        ```cpp
        [db_source("<initialization_string>"), db_command("SQL_command")]
        ...
        // Column map using db_column is the same as for consumer type of 'table'
        ```

      en lugar de usar el comando y las declaraciones de clase de descriptor de acceso de comando en el archivo .h de la clase de comando, por ejemplo:

        ```cpp
        // Command accessor class:
            class CListOrdersAccessor;
        // Command class:
            class CListOrders : public CCommand<CAccessor<CListOrdersAccessor>>;
        // ...
        // Column map using BEGIN_COLUMN_MAP ... END_COLUMN_MAP is the same as
        // for consumer type of 'table'
        ```

      Consulte [Mecanismos básicos de los atributos](../../windows/basic-mechanics-of-attributes.md) para obtener más información.

- **Type**

   Seleccione uno de estos botones de radio para especificar si la clase de consumidor se derivará de `CTable` o `CCommand` (valor predeterminado).

   - **Table**

      Seleccione esta opción si desea usar `CTable` o `db_table` para crear la tabla y las declaraciones de clase de descriptor de acceso de tabla.

   - **Comando**

      Seleccione esta opción si desea usar `CCommand` o `db_command` para crear el comando y las declaraciones de clase de descriptor de acceso de comando. Esta es la selección predeterminada.

- **Soporte técnico**

   Seleccione las casillas de verificación para especificar los tipos de actualizaciones que se aceptan en el consumidor (el valor predeterminado es Ninguna). Cada una de las siguientes acciones establecerá [DBPROP_IRowsetChange](/previous-versions/windows/desktop/ms715892(v=vs.85)) y las entradas adecuadas de [DBPROP_UPDATABILITY](/previous-versions/windows/desktop/ms722676(v=vs.85)) en la asignación de conjunto de propiedades.

   - **Cambio**

      Especifica que el consumidor admite las actualizaciones de datos de fila en el conjunto de filas.

   - **Insertar**

      Especifica que el consumidor acepta la inserción de filas en el conjunto de filas.

   - **Eliminar**

      Especifica que el consumidor admite la eliminación de filas del conjunto de filas.

::: moniker-end

## <a name="see-also"></a>Vea también

[Consumidor OLE DB](../../atl/reference/adding-an-atl-ole-db-consumer.md)<br/>
[Agregar funcionalidad con los Asistentes para código](../../ide/adding-functionality-with-code-wizards-cpp.md)<br/>
[Cadenas de conexión y vínculos de datos (OLE DB)](/previous-versions/windows/desktop/ms718376(v=vs.85))
