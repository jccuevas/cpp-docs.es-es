---
title: 'Origen de datos: Administrar conexiones (ODBC) | Microsoft Docs'
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
ms.openlocfilehash: a8f5a57b1ef97b38b6756931038ec18045aea746
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/18/2018
ms.locfileid: "46053731"
---
# <a name="data-source-managing-connections-odbc"></a>Origen de datos: Administrar conexiones (ODBC)

Este tema es aplicable a las clases ODBC de MFC.  
  
En este tema se explica:  
  
- [Cómo configurar un origen de datos](#_core_configuring_a_data_source).  
  
- [Cómo afecta a un entorno multiusuario un origen de datos y sus conjuntos de registros](#_core_working_in_a_multiuser_environment).  
  
- [Por qué se generaliza una cadena de conexión a un origen de datos](#_core_generalizing_the_connection_string).  
  
- [Cómo conectarse a un origen de datos](#_core_connecting_to_a_specific_data_source).  
  
- [Cómo desconectarse de un origen de datos](#_core_disconnecting_from_a_data_source).  
  
- [Cómo se reutiliza un objeto CDatabase](#_core_reusing_a_cdatabase_object).  
  
Conectarse a un origen de datos significa establecer comunicaciones con un DBMS para tener acceso a los datos. Cuando se conecta a un origen de datos desde una aplicación a través de un controlador ODBC, el controlador realiza la conexión, ya sea localmente o a través de una red.  
  
Puede conectarse a cualquier origen de datos para el que tiene un controlador ODBC. Los usuarios de la aplicación también deben tener el mismo controlador ODCB para su origen de datos. Para obtener más información sobre cómo se redistribuyen los controladores ODBC, vea [Redistribuir componentes ODBC a los clientes](../../data/odbc/redistributing-odbc-components-to-your-customers.md).  
  
##  <a name="_core_configuring_a_data_source"></a> Configurar un origen de datos  

El Administrador de ODBC se usa para configurar los orígenes de datos. También puede utilizar el Administrador de ODBC después de la instalación para agregar o quitar orígenes de datos. Al crear aplicaciones, se pueden dirigir a los usuarios para el Administrador de ODBC para que puedan agregar orígenes de datos o puede crear esta funcionalidad en la aplicación haciendo llamadas directas de instalación ODBC. Para obtener más información, consulte [Administrador ODBC](../../data/odbc/odbc-administrator.md).  
  
Puede usar un archivo de Excel como origen de datos, y deberá configurar el archivo para que se ha registrado y aparece en el **Seleccionar origen de datos** cuadro de diálogo.  
  
#### <a name="to-use-an-excel-file-as-a-data-source"></a>Para usar un archivo de Excel como origen de datos  
  
1. Configure el archivo con el Administrador de orígenes de datos ODBC.  
  
1. En el **DSN de archivo** , haga clic **agregar**.  
  
1. En el **crear nuevo origen de datos** cuadro de diálogo, seleccione un controlador de Excel y, a continuación, haga clic en **siguiente**.  
  
1. Haga clic en **examinar**y seleccione el nombre del archivo que se usará como origen de datos.  
  
> [!NOTE]
>  Es posible que deba seleccionar **todos los archivos** en el menú desplegable para ver los archivos .xls.  
  
1. Haga clic en **Siguiente** y después haga clic en **Finalizar**.  
  
1. En el **configuración de ODBC Microsoft Excel** cuadro de diálogo, seleccione la versión de la base de datos y el libro.  
  
##  <a name="_core_working_in_a_multiuser_environment"></a> Trabajar en un entorno multiusuario  

Si varios usuarios están conectados a un origen de datos, pueden cambiar los datos mientras se manipulan en los conjuntos de registros. De forma similar, los cambios pueden afectar a los conjuntos de registros de otros usuarios. Para obtener más información, consulte [conjunto de registros: actualizar los registros (ODBC)](../../data/odbc/recordset-how-recordsets-update-records-odbc.md) y [transacción (ODBC)](../../data/odbc/transaction-odbc.md).  
  
##  <a name="_core_generalizing_the_connection_string"></a> Generalizar la cadena de conexión  

Los asistentes utilizan una cadena de conexión predeterminada para establecer una conexión a un origen de datos. Utilice esta conexión para ver las tablas y columnas mientras está desarrollando una aplicación. Sin embargo, esta cadena de conexión predeterminada podría no ser adecuada para las conexiones de los usuarios con el origen de datos a través de la aplicación. Por ejemplo, su origen de datos y la ruta de acceso a su ubicación pueden diferir de usado en el desarrollo de la aplicación. En ese caso, debe volver a implementar el [CRecordset:: GetDefaultConnect](../../mfc/reference/crecordset-class.md#getdefaultconnect) miembros funcionan de forma más genérica y descartar la implementación del asistente. Por ejemplo, use uno de los enfoques siguientes:  
  
- Registrar y administrar las cadenas de conexión mediante el Administrador ODBC.  
  
- Edite la cadena de conexión y quite el nombre del origen de datos. El marco de trabajo proporciona ODBC como origen de datos; en tiempo de ejecución, ODBC muestra un cuadro de diálogo que solicita información de conexión necesaria de nombre y cualquier otro origen de datos.  
  
- Proporcione únicamente el nombre del origen de datos. ODBC solicita el identificador de usuario y la contraseña, si es necesario. Por ejemplo, antes de generalizar, la cadena de conexión se ve así:  
  
    ```cpp  
    CString CApp1Set::GetDefaultConnect()  
    {  
       return "ODBC;DSN=afx;Trusted_Connection=Yes;";  
    }  
    ```  
  
     Esta cadena de conexión especifica una conexión de confianza, que utiliza seguridad integrada de Windows NT. Debe evitar de forma rígida una contraseña o especificar una contraseña en blanco, porque si lo hace, crea una vulnerabilidad de seguridad de mayor envergadura. En su lugar, puedes usar `GetDefaultConnect` una nueva cadena de conexión para que solicite un Id. de usuario y una contraseña.  
  
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
  
##  <a name="_core_connecting_to_a_specific_data_source"></a> Conectarse a un origen de datos específico  

Para conectarse a un origen de datos específico, el origen de datos debe ya se han configurado con [Administrador ODBC](../../data/odbc/odbc-administrator.md).  
  
#### <a name="to-connect-to-a-specific-data-source"></a>Para conectarse a un origen de datos específico  
  
1. Construir un `CDatabase` objeto.  
  
1. Llame a su `OpenEx` o `Open` función miembro.  
  
Para obtener más información sobre cómo especificar el origen de datos si es algo distinto del especificado con un asistente, consulte [CDatabase:: OpenEx](../../mfc/reference/cdatabase-class.md#openex) o [CDatabase:: Open](../../mfc/reference/cdatabase-class.md#open) en el *MFC Referencia*.  
  
##  <a name="_core_disconnecting_from_a_data_source"></a> Desconexión de un origen de datos  

Debe cerrar los conjuntos de registros abiertos antes de llamar a la `Close` función miembro de `CDatabase`. En conjuntos de registros asociados con la `CDatabase` objeto que desea cerrar, `AddNew` o `Edit` se cancelan las instrucciones y todas las transacciones pendientes se revierten.  
  
#### <a name="to-disconnect-from-a-data-source"></a>Para desconectarse de un origen de datos  
  
1. Llame a la `CDatabase` del objeto [cerrar](../../mfc/reference/cdatabase-class.md#close) función miembro.  
  
1. Destruya el objeto a menos que desee volver a usarla.  
  
##  <a name="_core_reusing_a_cdatabase_object"></a> Reutilizar un objeto CDatabase  

Puede volver a usar un `CDatabase` objeto después de desconectarse del mismo, independientemente de si usa para volver a conectarse al mismo origen de datos o para conectarse a un origen de datos diferente.  
  
#### <a name="to-reuse-a-cdatabase-object"></a>Para reutilizar un objeto CDatabase  
  
1. Cierre la conexión original del objeto.  
  
1. En lugar de destruir el objeto, llame a su `OpenEx` o `Open` volver a la función miembro.  
  
## <a name="see-also"></a>Vea también  

[Origen de datos (ODBC)](../../data/odbc/data-source-odbc.md)<br/>
[Origen de datos: Determinar el esquema del origen de datos (ODBC)](../../data/odbc/data-source-determining-the-schema-of-the-data-source-odbc.md)<br/>
[CRecordset (clase)](../../mfc/reference/crecordset-class.md)