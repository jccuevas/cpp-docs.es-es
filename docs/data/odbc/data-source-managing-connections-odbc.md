---
title: 'Origen de datos: Administrar conexiones (ODBC)'
ms.date: 11/04/2016
helpviewer_keywords:
- ODBC data sources [C++], multiuser environments
- generalizing connection strings
- ODBC [C++], disconnecting from data sources
- connection strings [C++], generalizing
- database connections [C++], creating
- GetDefaultConnect method
- connections [C++], data source
- ODBC connections [C++], configuring
- disconnecting from data sources
- databases [C++], connecting to
- ODBC connections [C++], disconnecting
- data sources [C++], connecting to
- ODBC connections [C++], connecting to data source
- ODBC data sources [C++], connections
- database connections [C++], MFC ODBC classes
ms.assetid: c0adbcdd-c000-40c6-b199-09ffdc7b6ef2
ms.openlocfilehash: 6186199ea51c1fc966783ed3c0a73496c6a307ee
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 03/24/2020
ms.locfileid: "80213303"
---
# <a name="data-source-managing-connections-odbc"></a>Origen de datos: Administrar conexiones (ODBC)

Este tema es aplicable a las clases ODBC de MFC.

En este tema se explica:

- [Cómo configurar un origen de datos](#_core_configuring_a_data_source).

- [Cómo afecta un entorno multiusuario a un origen de datos y sus conjuntos de registros](#_core_working_in_a_multiuser_environment).

- [Por qué se generaliza una cadena de conexión a un origen de datos](#_core_generalizing_the_connection_string).

- [Cómo conectarse a un origen de datos](#_core_connecting_to_a_specific_data_source).

- [Cómo desconectarse de un origen de datos](#_core_disconnecting_from_a_data_source).

- [Cómo reutilizar un objeto CDatabase](#_core_reusing_a_cdatabase_object).

La conexión a un origen de datos significa establecer comunicaciones con un DBMS para tener acceso a los datos. Cuando se conecta a un origen de datos desde una aplicación a través de un controlador ODBC, el controlador realiza la conexión, ya sea localmente o a través de una red.

Puede conectarse a cualquier origen de datos para el que tenga un controlador ODBC. Los usuarios de la aplicación también deben tener el mismo controlador ODBC para su origen de datos. Para obtener más información acerca de cómo redistribuir los controladores ODBC, consulte [redistribuir componentes ODBC a los clientes](../../data/odbc/redistributing-odbc-components-to-your-customers.md).

##  <a name="configuring-a-data-source"></a><a name="_core_configuring_a_data_source"></a>Configuración de un origen de datos

El administrador de ODBC se utiliza para configurar los orígenes de datos. También puede usar el administrador de ODBC después de la instalación para agregar o quitar orígenes de datos. Al crear aplicaciones, puede dirigir a los usuarios al administrador de ODBC para que puedan agregar orígenes de datos o puede crear esta funcionalidad en la aplicación realizando llamadas directas a la instalación de ODBC. Para obtener más información, vea [Administrador de ODBC](../../data/odbc/odbc-administrator.md).

Puede usar un archivo de Excel como origen de datos y debe configurar el archivo para que se registre y aparezca en el cuadro de diálogo **Seleccionar origen de datos** .

#### <a name="to-use-an-excel-file-as-a-data-source"></a>Para usar un archivo de Excel como origen de datos

1. Configure el archivo con el administrador de orígenes de datos ODBC.

1. En la pestaña **DSN de archivo** , haga clic en **Agregar**.

1. En el cuadro de diálogo **crear nuevo origen de datos** , seleccione un controlador de Excel y, a continuación, haga clic en **siguiente**.

1. Haga clic en **examinar**y seleccione el nombre del archivo que se va a usar como origen de fecha.

> [!NOTE]
>  Es posible que tenga que seleccionar **todos los archivos** en el menú desplegable para ver los archivos. xls.

1. Haga clic en **Siguiente**y, a continuación, en **Finalizar**.

1. En el cuadro de diálogo **instalación de ODBC de Microsoft Excel** , seleccione la versión de la base de datos y el libro.

##  <a name="working-in-a-multiuser-environment"></a><a name="_core_working_in_a_multiuser_environment"></a>Trabajar en un entorno multiusuario

Si hay varios usuarios conectados a un origen de datos, pueden cambiar los datos mientras se manipulan en los conjuntos de registros. Del mismo modo, los cambios podrían afectar a los conjuntos de registros de otros usuarios. Para obtener más información, vea conjunto de registros [: actualizar los registros (ODBC) y la](../../data/odbc/recordset-how-recordsets-update-records-odbc.md) [transacción (ODBC)](../../data/odbc/transaction-odbc.md).

##  <a name="generalizing-the-connection-string"></a><a name="_core_generalizing_the_connection_string"></a>Generalizar la cadena de conexión

Los asistentes utilizan una cadena de conexión predeterminada para establecer una conexión a un origen de datos. Esta conexión se utiliza para ver tablas y columnas mientras se está desarrollando la aplicación. Sin embargo, esta cadena de conexión predeterminada podría no ser adecuada para las conexiones de los usuarios con el origen de datos a través de la aplicación. Por ejemplo, su origen de datos y la ruta de acceso a su ubicación pueden ser diferentes de la que se usa en el desarrollo de la aplicación. En ese caso, debe volver a implementar la función miembro [CRecordset:: GetDefaultConnect](../../mfc/reference/crecordset-class.md#getdefaultconnect) de manera más genérica y descartar la implementación del asistente. Por ejemplo, use uno de los métodos siguientes:

- Registre y administre las cadenas de conexión mediante el administrador de ODBC.

- Edite la cadena de conexión y quite el nombre del origen de datos. El marco de trabajo proporciona ODBC como origen de datos; en tiempo de ejecución, ODBC muestra un cuadro de diálogo que solicita el nombre del origen de datos y cualquier otra información de conexión necesaria.

- Proporcione solo el nombre del origen de datos. ODBC solicita el identificador de usuario y la contraseña, si es necesario. Por ejemplo, antes de generalizar, la cadena de conexión tiene el siguiente aspecto:

    ```cpp
    CString CApp1Set::GetDefaultConnect()
    {
       return "ODBC;DSN=afx;Trusted_Connection=Yes;";
    }
    ```

   Esta cadena de conexión especifica una conexión de confianza, que utiliza la seguridad integrada de Windows NT. Debe evitar la codificación de una contraseña o la especificación de una contraseña en blanco, ya que esto crea un punto débil importante en la seguridad. En su lugar, puede dar a `GetDefaultConnect` una nueva cadena de conexión para que consulte un identificador de usuario y una contraseña.

    ```cpp
    // User must select data source and supply user ID and password:
        return "ODBC;";
    // User ID and password required:
        return "ODBC;DSN=mydb;";
    // Password required (myuserid must be replaced with a valid user ID):
        return "ODBC;DSN=mydb;UID=myuserid;";
    // Hard-coded user ID and password (SECURITY WEAKNESS--AVOID):
        return "ODBC;DSN=mydb;UID=sa;PWD=777;";
    ```

##  <a name="connecting-to-a-specific-data-source"></a><a name="_core_connecting_to_a_specific_data_source"></a>Conexión a un origen de datos específico

Para conectarse a un origen de datos específico, el origen de datos ya debe estar configurado con el [Administrador de ODBC](../../data/odbc/odbc-administrator.md).

#### <a name="to-connect-to-a-specific-data-source"></a>Para conectarse a un origen de datos específico

1. Construya un objeto de `CDatabase`.

1. Llame a su función miembro `OpenEx` o `Open`.

Para obtener más información sobre cómo especificar el origen de datos si es distinto del que se especificó con un asistente, vea [CDatabase:: OpenEx](../../mfc/reference/cdatabase-class.md#openex) o [CDatabase:: Open](../../mfc/reference/cdatabase-class.md#open) en la *referencia de MFC*.

##  <a name="disconnecting-from-a-data-source"></a><a name="_core_disconnecting_from_a_data_source"></a>Desconectar de un origen de datos

Debe cerrar todos los conjuntos de registros abiertos antes de llamar a la función miembro `Close` de `CDatabase`. En los conjuntos de registros asociados al `CDatabase` objeto que desea cerrar, se cancelan todas las instrucciones de `AddNew` o `Edit` pendientes y se revierten todas las transacciones pendientes.

#### <a name="to-disconnect-from-a-data-source"></a>Para desconectarse de un origen de datos

1. Llame a la función miembro [Close](../../mfc/reference/cdatabase-class.md#close) del objeto `CDatabase`.

1. Destruya el objeto a menos que desee reutilizarlo.

##  <a name="reusing-a-cdatabase-object"></a><a name="_core_reusing_a_cdatabase_object"></a>Reutilizar un objeto CDatabase

Puede reutilizar un objeto de `CDatabase` después de desconectarse de él, independientemente de si lo utiliza para volver a conectarse al mismo origen de datos o para conectarse a un origen de datos diferente.

#### <a name="to-reuse-a-cdatabase-object"></a>Para reutilizar un objeto CDatabase

1. Cierre la conexión original del objeto.

1. En lugar de destruir el objeto, llame de nuevo a la función miembro `OpenEx` o `Open`.

## <a name="see-also"></a>Consulte también

[Origen de datos (ODBC)](../../data/odbc/data-source-odbc.md)<br/>
[Origen de datos: Determinar el esquema del origen de datos (ODBC)](../../data/odbc/data-source-determining-the-schema-of-the-data-source-odbc.md)<br/>
[CRecordset (clase)](../../mfc/reference/crecordset-class.md)
