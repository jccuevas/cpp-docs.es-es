---
title: "Origen de datos: Administrar conexiones (ODBC) | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "cadenas de conexión [C++], generalizar"
  - "conexiones [C++], origen de datos"
  - "orígenes de datos [C++], conectar"
  - "conexiones de bases de datos [C++], crear"
  - "conexiones de bases de datos [C++], clases ODBC de MFC"
  - "bases de datos [C++], conectar"
  - "desconectar de orígenes de datos"
  - "generalizar cadenas de conexión"
  - "GetDefaultConnect (método)"
  - "ODBC [C++], desconectar de orígenes de datos"
  - "conexiones ODBC [C++], configurar"
  - "conexiones ODBC [C++], conectar a orígenes de datos"
  - "conexiones ODBC [C++], desconectar"
  - "orígenes de datos ODBC [C++], conexiones"
  - "orígenes de datos ODBC [C++], entornos multiusuario"
ms.assetid: c0adbcdd-c000-40c6-b199-09ffdc7b6ef2
caps.latest.revision: 10
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 10
---
# Origen de datos: Administrar conexiones (ODBC)
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

Este tema es aplicable a las clases ODBC de MFC.  
  
 En este tema se explica:  
  
-   [Cómo se configura un origen de datos](#_core_configuring_a_data_source).  
  
-   [Cómo afecta un entorno multiusuario a un origen de datos y sus conjuntos de registros](#_core_working_in_a_multiuser_environment).  
  
-   [Por qué se generaliza una cadena de conexión a un origen de datos](#_core_generalizing_the_connection_string).  
  
-   [Cómo conectarse a un origen de datos](#_core_connecting_to_a_specific_data_source).  
  
-   [Cómo desconectarse de un origen de datos](#_core_disconnecting_from_a_data_source).  
  
-   [Cómo se reutiliza un objeto CDatabase](#_core_reusing_a_cdatabase_object).  
  
 La acción de conectarse a un origen de datos significa establecer comunicaciones con un DBMS para tener acceso a los datos.  Cuando se establece conexión con un origen de datos desde una aplicación mediante un controlador ODBC, el controlador efectúa la conexión en lugar del usuario, ya sea localmente o a través de una red.  
  
 La conexión se puede efectuar con cualquier origen de datos para el que se tenga un controlador ODBC.  Los usuarios de la aplicación también deben tener el mismo controlador ODCB para su origen de datos.  Para obtener más información sobre cómo se redistribuyen los controladores ODBC, vea [Redistribuir componentes ODBC a los clientes](../../data/odbc/redistributing-odbc-components-to-your-customers.md).  
  
##  <a name="_core_configuring_a_data_source"></a> Configurar un origen de datos  
 Para configurar los orígenes de datos se utiliza el Administrador de ODBC.  También se puede utilizar el Administrador de ODBC después de la instalación para agregar o quitar orígenes de datos.  Cuando se crean aplicaciones, se puede dirigir a los usuarios al Administrador de ODBC para que puedan agregar orígenes de datos, o compilar esta funcionalidad en la aplicación haciendo llamadas directas de instalación ODBC.  Para obtener más información, vea [Administrador de ODBC](../../data/odbc/odbc-administrator.md).  
  
 Se puede utilizar un archivo de Excel como origen de datos; en este caso, es necesario configurar el archivo de forma que se registre y aparezca en el cuadro de diálogo **Seleccionar origen de datos**.  
  
#### Para utilizar un archivo de Excel como origen de datos  
  
1.  Configure el archivo con el Administrador de ODBC de origen de datos.  
  
2.  En la ficha **DSN de archivo**, haga clic en **Agregar**.  
  
3.  En el cuadro de diálogo **Crear nuevo origen de datos**, seleccione un controlador de Excel y haga clic en **Siguiente**.  
  
4.  Haga clic en **Examinar** y seleccione el nombre del archivo que se va a utilizar como origen de datos.  
  
> [!NOTE]
>  Puede que sea necesario seleccionar **Todos los archivos** en el menú desplegable para ver los archivos .xls.  
  
1.  Haga clic en **Siguiente** y, a continuación, en **Finalizar**.  
  
2.  En el cuadro de diálogo **Configuración de ODBC Microsoft Excel**, seleccione la versión de base de datos y el libro de Excel correspondientes.  
  
##  <a name="_core_working_in_a_multiuser_environment"></a> Trabajar en un entorno multiusuario  
 Si hay varios usuarios conectados a un origen de datos, pueden cambiar los datos mientras se manipulan en los conjuntos de registros personales.  De forma similar, los cambios que se efectúen pueden afectar a los conjuntos de registros de otros usuarios.  Para obtener más información, vea [Conjunto de registros: Actualizar los registros \(ODBC\)](../../data/odbc/recordset-how-recordsets-update-records-odbc.md) y [Transacción \(ODBC\)](../../data/odbc/transaction-odbc.md).  
  
##  <a name="_core_generalizing_the_connection_string"></a> Generalizar la cadena de conexión  
 Los asistentes utilizan una cadena de conexión predeterminada para establecer una conexión con un origen de datos.  Esta conexión se utiliza para ver tablas y columnas mientras se está desarrollando la aplicación.  No obstante, puede que esta cadena de conexión predeterminada no sea apropiada para las conexiones de los usuarios con el origen de datos a través de la aplicación.  Por ejemplo, el origen de datos de los usuarios y la ruta de acceso a su ubicación pueden diferir de los utilizados en el desarrollo de la aplicación.  En este caso, se debe volver a implementar la función miembro [CRecordset::GetDefaultConnect](../Topic/CRecordset::GetDefaultConnect.md) de forma más genérica y descartar la implementación del asistente.  Por ejemplo, utilice uno de los siguientes enfoques:  
  
-   Registre y administre las cadenas de conexión utilizando el Administrador de ODBC.  
  
-   Modifique la cadena de conexión y quite el nombre del origen de datos.  El marco de trabajo proporciona ODBC como origen de datos; en tiempo de ejecución, ODBC muestra un cuadro de diálogo en el que se solicita el nombre del origen de datos y la información necesaria para la conexión.  
  
-   Proporcione únicamente el nombre del origen de datos.  ODBC solicita el identificador y la contraseña del usuario, si procede.  Por ejemplo, antes de generalizar, la cadena de conexión tiene este aspecto:  
  
    ```  
    CString CApp1Set::GetDefaultConnect()  
    {  
       return "ODBC;DSN=afx;Trusted_Connection=Yes;";  
    }  
    ```  
  
     Esta cadena de conexión especifica una conexión de confianza, que utiliza seguridad integrada de Windows NT.  Debe evitar incluir contraseñas en el propio código o especificar una contraseña en blanco, ya que se podría poner en peligro la seguridad.  En lugar de ello, puede proporcionar a `GetDefaultConnect` una nueva cadena de conexión de modo que solicite un identificador de usuario y una contraseña.  
  
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
 Para conectarse a un origen de datos específico, el origen de datos debe estar configurado previamente con el [Administrador de ODBC](../../data/odbc/odbc-administrator.md).  
  
#### Para conectarse a un origen de datos específico  
  
1.  Construya un objeto `CDatabase`.  
  
2.  Llame a su función miembro `OpenEx` u **Open** correspondiente.  
  
 Para obtener más información sobre cómo se especifica el origen de datos si se trata de uno diferente del que se especificó con el asistente, vea [CDatabase::OpenEx](../Topic/CDatabase::OpenEx.md) o [CDatabase::Open](../Topic/CDatabase::Open.md) en la *Referencia de MFC*.  
  
##  <a name="_core_disconnecting_from_a_data_source"></a> Desconectarse de un origen de datos  
 Se deben cerrar los conjuntos de registros abiertos antes de llamar a la función miembro **Close** de `CDatabase`.  En los conjuntos de registros asociados al objeto `CDatabase` que se desee cerrar, se cancelan las instrucciones `AddNew` o **Edit** pendientes y se revierten todas las transacciones pendientes.  
  
#### Para desconectarse de un origen de datos  
  
1.  Llame a la función miembro [Close](../Topic/CDatabase::Close.md) del objeto `CDatabase`.  
  
2.  Destruya el objeto a menos que desee volver a utilizarlo.  
  
##  <a name="_core_reusing_a_cdatabase_object"></a> Reutilizar un objeto CDatabase  
 Se puede reutilizar un objeto `CDatabase` después de desconectarse del mismo, ya sea para volver a conectarse al mismo origen de datos o para conectarse a un origen de datos diferente.  
  
#### Para reutilizar un objeto CDatabase  
  
1.  Cierre la conexión original al objeto.  
  
2.  En lugar de destruir el objeto, llame de nuevo a la función miembro `OpenEx` u **Open** correspondiente.  
  
## Vea también  
 [Origen de datos \(ODBC\)](../../data/odbc/data-source-odbc.md)   
 [Origen de datos: Determinar el esquema del origen de datos \(ODBC\)](../../data/odbc/data-source-determining-the-schema-of-the-data-source-odbc.md)   
 [CRecordset Class](../../mfc/reference/crecordset-class.md)