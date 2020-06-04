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
ms.openlocfilehash: 107a5e20b70f67be74b6e6f861bd539446e9d4ee
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/14/2020
ms.locfileid: "81374527"
---
# <a name="data-source-managing-connections-odbc"></a>Origen de datos: Administrar conexiones (ODBC)

Este tema es aplicable a las clases ODBC de MFC.

En este tema se explica:

- [Cómo configurar un origen](#_core_configuring_a_data_source)de datos .

- [Cómo afecta un entorno multiusuario a un origen](#_core_working_in_a_multiuser_environment)de datos y a sus conjuntos de registros.

- [Por qué generalizar una cadena](#_core_generalizing_the_connection_string)de conexión a un origen de datos .

- [Cómo conectarse a un origen](#_core_connecting_to_a_specific_data_source)de datos .

- [Cómo desconectarse de un origen de datos.](#_core_disconnecting_from_a_data_source)

- [Cómo reutilizar un objeto CDatabase](#_core_reusing_a_cdatabase_object).

Conectarse a un origen de datos significa establecer comunicaciones con un DBMS para acceder a los datos. Cuando se conecta a un origen de datos desde una aplicación a través de un controlador ODBC, el controlador realiza la conexión por usted, ya sea localmente o a través de una red.

Puede conectarse a cualquier origen de datos para el que tenga un controlador ODBC. Los usuarios de la aplicación también deben tener el mismo controlador ODBC para su origen de datos. Para obtener más información acerca de la redistribución de controladores ODBC, vea [Redistribuir componentes ODBC a los clientes](../../data/odbc/redistributing-odbc-components-to-your-customers.md).

## <a name="configuring-a-data-source"></a><a name="_core_configuring_a_data_source"></a>Configuración de un origen de datos

Administrador ODBC se utiliza para configurar los orígenes de datos. También puede usar el Administrador ODBC después de la instalación para agregar o quitar orígenes de datos. Al crear aplicaciones, puede dirigir a los usuarios al Administrador ODBC para permitirles agregar orígenes de datos o puede compilar esta funcionalidad en la aplicación realizando llamadas directas a la instalación de ODBC. Para obtener más información, consulte [Administrador ODBC](../../data/odbc/odbc-administrator.md).

Puede usar un archivo de Excel como origen de datos y debe configurar el archivo para que se registre y aparezca en el cuadro de diálogo Seleccionar origen de **datos.**

#### <a name="to-use-an-excel-file-as-a-data-source"></a>Para utilizar un archivo de Excel como origen de datos

1. Configure el archivo con el Administrador de orígenes de datos ODBC.

1. En la pestaña **DSN** de archivo, haga clic en **Agregar**.

1. En el cuadro de diálogo Crear nuevo origen de **datos,** seleccione un controlador de Excel y, a continuación, haga clic en **Siguiente**.

1. Haga clic en **Examinar**y seleccione el nombre del archivo que se utilizará como origen de fecha.

> [!NOTE]
> Es posible que deba seleccionar **Todos los archivos** en el menú desplegable para ver los archivos .xls.

1. Haga clic en **Siguiente** y después en **Finalizar**.

1. En el cuadro de diálogo Configuración de **ODBC Microsoft Excel,** seleccione la versión de la base de datos y el libro.

## <a name="working-in-a-multiuser-environment"></a><a name="_core_working_in_a_multiuser_environment"></a>Trabajar en un entorno multiusuario

Si hay varios usuarios conectados a un origen de datos, pueden cambiar los datos mientras los manipula en los conjuntos de registros. Del mismo modo, los cambios pueden afectar a los conjuntos de registros de otros usuarios. Para obtener más información, vea Conjunto de registros: cómo los conjuntos de [registros actualizan registros (ODBC)](../../data/odbc/recordset-how-recordsets-update-records-odbc.md) y [transacción (ODBC)](../../data/odbc/transaction-odbc.md).

## <a name="generalizing-the-connection-string"></a><a name="_core_generalizing_the_connection_string"></a>Generalización de la cadena de conexión

Los asistentes usan una cadena de conexión predeterminada para establecer una conexión a un origen de datos. Utilice esta conexión para ver tablas y columnas mientras desarrolla la aplicación. Sin embargo, esta cadena de conexión predeterminada podría no ser adecuada para las conexiones de los usuarios al origen de datos a través de la aplicación. Por ejemplo, su origen de datos y la ruta de acceso a su ubicación pueden ser diferentes de la utilizada para desarrollar la aplicación. En ese caso, debe volver a implementar el [CRecordset::GetDefaultConnect](../../mfc/reference/crecordset-class.md#getdefaultconnect) función miembro de una manera más genérica y descartar la implementación del asistente. Por ejemplo, utilice uno de los siguientes enfoques:

- Registre y administre las cadenas de conexión mediante el Administrador ODBC.

- Edite la cadena de conexión y quite el nombre del origen de datos. El marco de trabajo proporciona ODBC como origen de datos; en tiempo de ejecución, ODBC muestra un cuadro de diálogo que solicita el nombre del origen de datos y cualquier otra información de conexión necesaria.

- Proporcione solo el nombre del origen de datos. ODBC solicita el ID de usuario y la contraseña, si es necesario. Por ejemplo, antes de generalizar, la cadena de conexión tiene este aspecto:

    ```cpp
    CString CApp1Set::GetDefaultConnect()
    {
       return "ODBC;DSN=afx;Trusted_Connection=Yes;";
    }
    ```

   Esta cadena de conexión especifica una conexión de confianza, que utiliza la seguridad integrada de Windows NT. Debe evitar codificar una contraseña de forma rígida o especificar una contraseña en blanco, ya que al hacerlo se crea una debilidad de seguridad importante. En su lugar, puede proporcionar `GetDefaultConnect` una nueva cadena de conexión para que consulte un ID de usuario y una contraseña.

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

## <a name="connecting-to-a-specific-data-source"></a><a name="_core_connecting_to_a_specific_data_source"></a>Conexión a una fuente de datos específica

Para conectarse a un origen de datos específico, el origen de datos ya debe haberse configurado con [el Administrador ODBC](../../data/odbc/odbc-administrator.md).

#### <a name="to-connect-to-a-specific-data-source"></a>Para conectarse a un origen de datos específico

1. Construir `CDatabase` un objeto.

1. Llame `OpenEx` a `Open` su o función miembro.

Para obtener más información acerca de cómo especificar el origen de datos si es algo distinto del especificado con un asistente, vea [CDatabase::OpenEx](../../mfc/reference/cdatabase-class.md#openex) o [CDatabase::Open](../../mfc/reference/cdatabase-class.md#open) en la *referencia de MFC*.

## <a name="disconnecting-from-a-data-source"></a><a name="_core_disconnecting_from_a_data_source"></a>Desconectarse de un origen de datos

Debe cerrar los conjuntos de `Close` registros `CDatabase`abiertos antes de llamar a la función miembro de . En los conjuntos `CDatabase` de registros asociados `AddNew` `Edit` al objeto que desea cerrar, se cancelan las instrucciones o instrucciones pendientes y se revierten todas las transacciones pendientes.

#### <a name="to-disconnect-from-a-data-source"></a>Para desconectarse de un origen de datos

1. Llame `CDatabase` a la función miembro [Close](../../mfc/reference/cdatabase-class.md#close) del objeto.

1. Destruye el objeto a menos que quieras reutilizarlo.

## <a name="reusing-a-cdatabase-object"></a><a name="_core_reusing_a_cdatabase_object"></a>Reutilizar un objeto CDatabase

Puede reutilizar `CDatabase` un objeto después de desconectarse de él, tanto si lo utiliza para volver a conectarse al mismo origen de datos como para conectarse a un origen de datos diferente.

#### <a name="to-reuse-a-cdatabase-object"></a>Para reutilizar un CDatabase objeto

1. Cierre la conexión original del objeto.

1. En lugar de destruir el `OpenEx` `Open` objeto, llame a su o función miembro de nuevo.

## <a name="see-also"></a>Consulte también

[Origen de datos (ODBC)](../../data/odbc/data-source-odbc.md)<br/>
[Origen de datos: Determinar el esquema del origen de datos (ODBC)](../../data/odbc/data-source-determining-the-schema-of-the-data-source-odbc.md)<br/>
[Clase CRecordset](../../mfc/reference/crecordset-class.md)
