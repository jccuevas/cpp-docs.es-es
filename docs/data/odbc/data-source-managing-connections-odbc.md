---
title: 'Origen de datos: Administrar conexiones (ODBC) | Documentos de Microsoft'
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-data
ms.topic: conceptual
dev_langs:
- C++
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
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- data-storage
ms.openlocfilehash: 100c06773a8f0ffa79631339384bd4ec42fa4b52
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 05/04/2018
---
# <a name="data-source-managing-connections-odbc"></a>Origen de datos: Administrar conexiones (ODBC)
Este tema es aplicable a las clases ODBC de MFC.  
  
 En este tema se explica:  
  
-   [Cómo configurar un origen de datos](#_core_configuring_a_data_source).  
  
-   [Cómo afecta a un entorno multiusuario un origen de datos y sus conjuntos de registros](#_core_working_in_a_multiuser_environment).  
  
-   [¿Por qué se generaliza una cadena de conexión a un origen de datos](#_core_generalizing_the_connection_string).  
  
-   [Cómo conectarse a un origen de datos](#_core_connecting_to_a_specific_data_source).  
  
-   [Cómo desconectarse de un origen de datos](#_core_disconnecting_from_a_data_source).  
  
-   [Cómo reutilizar un objeto CDatabase](#_core_reusing_a_cdatabase_object).  
  
 Conectarse a un origen de datos significa establecer comunicaciones con un DBMS para tener acceso a los datos. Cuando se conecta a un origen de datos desde una aplicación a través de un controlador ODBC, el controlador realiza la conexión para usted, ya sea localmente o a través de una red.  
  
 Puede conectarse a cualquier origen de datos para el que tenga un controlador ODBC. Los usuarios de la aplicación también deben tener el mismo controlador ODBC para su origen de datos. Para obtener más información acerca de la redistribución de controladores ODBC, vea [Redistribuir componentes ODBC a los clientes](../../data/odbc/redistributing-odbc-components-to-your-customers.md).  
  
##  <a name="_core_configuring_a_data_source"></a> Configurar un origen de datos  
 El Administrador de ODBC se usa para configurar los orígenes de datos. También puede utilizar el Administrador de ODBC después de la instalación para agregar o quitar orígenes de datos. Al crear aplicaciones, se pueden dirigir a los usuarios para el Administrador de ODBC que les permiten agregar orígenes de datos o puede crear esta funcionalidad en la aplicación mediante la realización de llamadas directas de instalación ODBC. Para obtener más información, consulte [Administrador ODBC](../../data/odbc/odbc-administrator.md).  
  
 Puede usar un archivo de Excel como origen de datos, y debe configurar el archivo de forma que se ha registrado y aparece en el **Seleccionar origen de datos** cuadro de diálogo.  
  
#### <a name="to-use-an-excel-file-as-a-data-source"></a>Para utilizar un archivo de Excel como origen de datos  
  
1.  Configure el archivo con el Administrador de orígenes de datos de ODBC.  
  
2.  En el **DSN de archivo** , haga clic en **agregar**.  
  
3.  En el **Create New Data Source** cuadro de diálogo, seleccione un controlador de Excel y, a continuación, haga clic en **siguiente**.  
  
4.  Haga clic en **examinar**y seleccione el nombre del archivo que se usará como origen de datos.  
  
> [!NOTE]
>  Tendrá que seleccionar **todos los archivos** en el menú desplegable para ver los archivos .xls.  
  
1.  Haga clic en **Siguiente** y después haga clic en **Finalizar**.  
  
2.  En el **el programa de instalación de ODBC Microsoft Excel** cuadro de diálogo, seleccione la versión de la base de datos y el libro.  
  
##  <a name="_core_working_in_a_multiuser_environment"></a> Trabajar en un entorno multiusuario  
 Si varios usuarios están conectados a un origen de datos, pueden cambiar los datos mientras se manipulan en los conjuntos de registros. De forma similar, los cambios podrían afectar a los conjuntos de registros de otros usuarios. Para obtener más información, consulte [conjunto de registros: actualizar los registros (ODBC)](../../data/odbc/recordset-how-recordsets-update-records-odbc.md) y [transacción (ODBC)](../../data/odbc/transaction-odbc.md).  
  
##  <a name="_core_generalizing_the_connection_string"></a> Generalizar la cadena de conexión  
 Los asistentes utilizan una cadena de conexión predeterminada para establecer una conexión con un origen de datos. Utilice esta conexión para ver las tablas y columnas mientras se desarrolla la aplicación. Sin embargo, esta cadena de conexión predeterminada no sería adecuada para las conexiones de los usuarios con el origen de datos a través de la aplicación. Por ejemplo, su origen de datos y la ruta de acceso a su ubicación podrían ser diferentes del que se usa para desarrollar la aplicación. En ese caso, debe volver a implementar el [CRecordset:: GetDefaultConnect](../../mfc/reference/crecordset-class.md#getdefaultconnect) miembro funcione de forma más genérica y descartar la implementación del asistente. Por ejemplo, utilice uno de los métodos siguientes:  
  
-   Registrar y administrar las cadenas de conexión mediante el Administrador de ODBC.  
  
-   Edite la cadena de conexión y quite el nombre de origen de datos. El marco de trabajo proporciona ODBC como origen de datos; en tiempo de ejecución, ODBC muestra un cuadro de diálogo pide información de conexión necesaria de nombre y cualquier otro origen de datos.  
  
-   Proporcione únicamente el nombre del origen de datos. ODBC solicita el Id. de usuario y la contraseña, si es necesario. Por ejemplo, antes de generalizar, la cadena de conexión se ve así:  
  
    ```  
    CString CApp1Set::GetDefaultConnect()  
    {  
       return "ODBC;DSN=afx;Trusted_Connection=Yes;";  
    }  
    ```  
  
     Esta cadena de conexión especifica una conexión de confianza, que utiliza la seguridad integrada de Windows NT. No se deben codificar de forma rígida una contraseña o especificar una contraseña en blanco, ya que si lo hace, crea una vulnerabilidad de seguridad principales. En su lugar, puede asignar a `GetDefaultConnect` una nueva cadena de conexión para que la consulta para un Id. de usuario y una contraseña.  
  
    ```  
    // User must select data source and supply user ID and password:  
        return "ODBC;";  
    // User ID and password required:  
        return "ODBC;DSN=mydb;";  
    // Password required (myuserid must be replaced with a valid user ID):  
        return "ODBC;DSN=mydb;UID=myuserid;";  
    // Hard-coded user ID and password (SECURITY WEAKNESS--AVOID):  
        return "ODBC;DSN=mydb;UID=sa;PWD=777;";  
    ```  
  
##  <a name="_core_connecting_to_a_specific_data_source"></a> Conectarse a un origen de datos específico  
 Para conectarse a un origen de datos específico, el origen de datos debe haber configurado con [Administrador ODBC](../../data/odbc/odbc-administrator.md).  
  
#### <a name="to-connect-to-a-specific-data-source"></a>Para conectarse a un origen de datos específico  
  
1.  Construir un `CDatabase` objeto.  
  
2.  Llame a su `OpenEx` o **abiertos** función miembro.  
  
 Para obtener más información sobre cómo especificar el origen de datos si el problema es distinto del que se especificó con el asistente, consulte [CDatabase:: OpenEx](../../mfc/reference/cdatabase-class.md#openex) o [CDatabase:: Open](../../mfc/reference/cdatabase-class.md#open) en el *MFC Referencia*.  
  
##  <a name="_core_disconnecting_from_a_data_source"></a> Desconectarse de un origen de datos  
 Debe cerrar los conjuntos de registros abiertos antes de llamar a la **cerrar** función miembro de `CDatabase`. En conjuntos de registros asociados con la `CDatabase` objeto que desea las pendientes cerrar, `AddNew` o **editar** instrucciones se cancelan y se revierten todas las transacciones pendientes.  
  
#### <a name="to-disconnect-from-a-data-source"></a>Para desconectarse de un origen de datos  
  
1.  Llame a la `CDatabase` del objeto [cerrar](../../mfc/reference/cdatabase-class.md#close) función miembro.  
  
2.  Destruye el objeto a menos que desee volver a usarla.  
  
##  <a name="_core_reusing_a_cdatabase_object"></a> Reutilizar un objeto CDatabase  
 Puede volver a usar un `CDatabase` objeto después de desconectarse de él, independientemente de si usa para volver a conectarse al mismo origen de datos o para conectarse a un origen de datos diferente.  
  
#### <a name="to-reuse-a-cdatabase-object"></a>Para reutilizar un objeto CDatabase  
  
1.  Cierre la conexión original del objeto.  
  
2.  En lugar de destruir el objeto, llame a su `OpenEx` o **abiertos** volver a la función miembro.  
  
## <a name="see-also"></a>Vea también  
 [Origen de datos (ODBC)](../../data/odbc/data-source-odbc.md)   
 [Origen de datos: Determinar el esquema del origen de datos (ODBC)](../../data/odbc/data-source-determining-the-schema-of-the-data-source-odbc.md)   
 [CRecordset (clase)](../../mfc/reference/crecordset-class.md)