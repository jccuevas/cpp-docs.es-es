---
title: Asistente para consumidores ATL OLE DB | Documentos de Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-atl
ms.topic: reference
f1_keywords:
- vc.codewiz.class.atl.consumer.overview
dev_langs:
- C++
helpviewer_keywords:
- ATL projects, adding ATL OLE DB consumers
- connection strings [C++], OLE DB consumers
- ATL OLE DB Consumer Wizard
ms.assetid: dcb68ed1-2224-422f-9f7b-108a74864204
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 0d51569eaece5e3fac59c7cc2ff82a8454a5f959
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 05/03/2018
ms.locfileid: "32364955"
---
# <a name="atl-ole-db-consumer-wizard"></a>Asistente para consumidores OLE DB ATL
Este asistente configura una clase de consumidor OLE DB con los enlaces de datos necesario para tener acceso al origen de datos especificados a través del proveedor OLE DB especificado.  
  
> [!NOTE]
>  Este asistente requiere que haga clic en el **origen de datos** para seleccionar un origen de datos antes de escribir los nombres en el `Class` y **archivo .h** campos.  
  
## <a name="uielement-list"></a>Lista de UIElement  
 **Origen de datos**  
 El **origen de datos** botón permite configurar el origen de datos especificado mediante el proveedor OLE DB especificado. Al hacer clic en este botón, el **propiedades de vínculo de datos** aparece el cuadro de diálogo. Para obtener más información sobre cómo generar cadenas de conexión y la **propiedades de vínculo de datos** cuadro de diálogo, vea [información general sobre la API de vínculos de datos](https://msdn.microsoft.com/library/ms718102.aspx) en la documentación del SDK de Windows.  
  
> [!NOTE]
>  En versiones anteriores, MAYÚS y haciendo clic en el **origen de datos** botón abre un cuadro de diálogo Abrir archivo para que pueda seleccionar un archivo de Data Link (.udl). Ya no se admite esta funcionalidad.  
  
 El cuadro de diálogo tiene cuatro pestañas:  
  
- **Proveedor** ficha  
  
- **Conexión** ficha  
  
- **Advanced** ficha  
  
- **Todos los** ficha  
  
     La siguiente información adicional describe las fichas en el **propiedades de vínculo de datos** cuadro de diálogo.  
  
     Haga clic en **Aceptar** para finalizar. El **seleccionar un objeto de base de datos** aparece el cuadro de diálogo. En este cuadro de diálogo, seleccione la tabla, vista o procedimiento almacenado que se va a usar el consumidor.  
  
 **Proveedor**  
     Seleccione un proveedor adecuado para administrar la conexión al origen de datos. El tipo de proveedor normalmente se determina por el tipo de base de datos al que se está conectando. Haga clic en el `Next` botón o haga clic en el **conexión** ficha.  
  
 **Conexión**  
     El contenido de esta ficha depende del proveedor seleccionado. Aunque hay muchos tipos de proveedores, en esta sección trata las conexiones con los dos más comunes: datos de SQL y ODBC. Los otros son variaciones similares de los campos descritos aquí.  
  
     Para los datos SQL:  
  
    1. **Seleccione o escriba un nombre de servidor:** haga clic en el menú de lista desplegable para mostrar todos los servidores de datos registrado en la red y seleccionar uno.  
  
    2. **Especificar información para iniciar sesión en el servidor:** escriba un nombre de usuario y una contraseña para iniciar sesión en el servidor de datos.  
  
    3. **Seleccione la base de datos en el servidor:** haga clic en el menú de lista desplegable para mostrar registrados todas las bases de datos en el servidor de datos y seleccionar uno.  
  
         -o bien-  
  
 **Adjuntar un archivo de base de datos como un nombre de base de datos:** especificar un archivo que se usará como la base de datos; escriba la ruta de acceso explícita.  
  
        > [!NOTE]
        >  There is a security problem with the "Allow saving of password" feature of the Data Link Properties dialog box. In "Enter information to log on to the server," there are two radio buttons:  
  
 **Usar seguridad integrada de Windows NT**  
  
 **Usar un nombre de usuario específico y una contraseña**  
  
         If you select **Use a specific user name and password**, you have the option of saving the password (using the check box for "Allow saving password"); however, this option is not secure. It is recommended that you select **Use Windows NT integrated security**; this option is secure because it encrypts the password.  
  
         There might be situations in which you want to select "Allow saving password." For example, if you are releasing a library with a private database solution, you should not access the database directly but instead use a middle-tier application to verify the user (through whatever authentication scheme you choose) and then limit the sort of data available to the user.  
  
         For ODBC data:  
  
         1. **Specify the source of data:** You can use a data source name or a connection string.  
  
 **Usar el nombre de origen de datos:** esta lista desplegable muestra los orígenes de datos registrados en el equipo. Puede configurar los orígenes de datos antes de tiempo mediante el Administrador de orígenes de datos ODBC- o -**Usar cadena de conexión:** escriba una cadena de conexión que ya ha obtenido o haga clic en el **generar** botón; el **Seleccionar origen de datos** aparece el cuadro de diálogo. Seleccione un origen de datos de archivo o equipo y haga clic en **Aceptar**.  
  
        > [!NOTE]
        >  You can obtain a connection string by viewing the properties of an existing connection in Server Explorer, or you can create a connection by double-clicking **Add Connection** in Server Explorer.  
  
         2. **Enter information to log on to the server:** Enter a user name and password to log on to the data server.  
  
         3. Enter the initial catalog to use.  
  
         4. Click **Test Connection**; if the test succeeds, click **OK**. If not, check your logon information, try another database, or try another data server.  
  
 **Avanzadas**  
 **Configuración de red:** especificar el **nivel de suplantación** (el nivel de suplantación que el servidor está autorizado para usar cuando suplanta al cliente; se corresponde directamente con los niveles de suplantación de RPC) y  **Nivel de protección** (el nivel de protección de datos enviados entre cliente y servidor; se corresponde directamente con los niveles de protección de RPC).  
  
 **Otro:** en **Connect timeout**, especifique el número de segundos de tiempo de inactividad permitido antes de que se produce un tiempo de espera. En **permisos de acceso**, especifique los permisos de acceso en la conexión de datos.  
  
     Para obtener más información acerca de las propiedades de inicialización avanzadas, consulte la documentación suministrada con cada proveedor OLE DB concreto.  
  
 **All**  
     Esta pestaña muestra un resumen de las propiedades de inicialización para el origen de datos y la conexión que ha especificado. Puede modificar estos valores.  
  
     Haga clic en **Aceptar** para finalizar. El **seleccionar un objeto de base de datos** aparece el cuadro de diálogo. En este cuadro de diálogo, seleccione la tabla, vista o procedimiento almacenado que se va a usar el consumidor.  
  
 `Class`  
 Después de seleccionar un origen de datos, este cuadro se rellena con un nombre de clase predeterminado basado en la tabla o el procedimiento almacenado que seleccionó (vea **seleccionar un origen de datos** a continuación). Puede modificar el nombre de clase.  
  
 **archivo .h**  
 Después de seleccionar un origen de datos, este cuadro se rellena con un nombre de clase de encabezado predeterminada basado en la tabla o procedimiento almacenado que seleccionó (vea **seleccionar un origen de datos** a continuación). Puede editar el nombre del archivo de encabezado o seleccionar un archivo de encabezado existente.  
  
 **El atributo**  
 Esta opción especifica si el asistente creará clases de consumidor con atributos o declaraciones de plantilla. Cuando se selecciona esta opción, el asistente usa atributos en lugar de declaraciones de plantilla (es decir, la opción predeterminada). Cuando se desactiva esta opción, el asistente usa declaraciones de plantilla en lugar de atributos.  
  
-   Si selecciona un consumidor **tipo** de tabla, se utiliza el Asistente para la `db_source` y **db_table** atributos para crear la tabla y el descriptor de acceso de tabla declaraciones de clase y utiliza **db_column**  para crear el mapa de columnas, por ejemplo:  
  
 ``` 
 // Inject table class and table accessor class declarations  
 [db_source("<initialization_string>"), db_table("dbo.Orders")]  
 ... 
 // Column map  
 [ db_column(1, status=m_dwOrderIDStatus, length=m_dwOrderIDLength) ] LONG m_OrderID;  
 [ db_column(2, status=m_dwCustomerIDStatus, length=m_dwCustomerIDLength) ] TCHAR m_CustomerID[6];  
 ...  
 ```  
  
     en lugar de usar la `CTable` clase de plantilla para declarar la tabla y clase de descriptor de acceso de la tabla y las macros BEGIN_COLUMN_MAP y END_COLUMN_MAP para crear el mapa de columnas, por ejemplo:  
  
 ``` 
 // Table accessor class  
    class COrdersAccessor; *// Table class  
    class COrders : public CTable<CAccessor<COrdersAccessor>>;  
 ... 
 // Column map  
    BEGIN_COLUMN_MAP(COrderDetailsAccessor) 
    COLUMN_ENTRY_LENGTH_STATUS(1, m_OrderID, m_dwOrderIDLength, m_dwOrderIDStatus)  
    COLUMN_ENTRY_LENGTH_STATUS(2, m_CustomerID, m_dwCustomerIDLength, m_dwCustomerIDStatus)  
 ...  
    END_COLUMN_MAP() 
 ```  
  
-   Si selecciona un consumidor **tipo** del comando, el asistente utiliza el `db_source` y **db_command** atributos y usa **db_column** para crear el mapa de columnas, por ejemplo :  
  
 ```  
 [db_source("<initialization_string>"), db_command("SQL_command")]  
 ... 
 // Column map using db_column is the same as for consumer type of 'table'  
 ```  
  
     en lugar de usar el comando y declaraciones de clase de descriptor de acceso de comandos en el archivo .h de la clase de comando, por ejemplo:  
  
 ```  
    Command accessor class:  
    class CListOrdersAccessor;  
    Command class:  
    class CListOrders : public CCommand<CAccessor<CListOrdersAccessor>>;  
 ... 
 // Column map using BEGIN_COLUMN_MAP ... END_COLUMN_MAP is the same as
 // for consumer type of 'table'  
 ```  
  
 Vea [mecanismos básicos de los atributos](../../windows/basic-mechanics-of-attributes.md) para obtener más información.  
  
 **Type**  
 Seleccione uno de estos botones de radio para especificar si se derivará de la clase de consumidor `CTable` o `CCommand` (valor predeterminado).  
  
 **Table**  
 Seleccione esta opción si desea usar `CTable` o **db_table** para crear la tabla y el descriptor de acceso de tabla declaraciones de clase.  
  
 **Comando**  
 Seleccione esta opción si desea usar `CCommand` o **db_command** para crear el comando y el descriptor de acceso de comando declaraciones de clase. Esta es la selección predeterminada.  
  
 **Soporte técnico**  
 Seleccione las casillas de verificación para especificar los tipos de actualizaciones que se aceptan en el consumidor (el valor predeterminado es none). Cada una de las siguientes acciones establecerá [DBPROP_IRowsetChange](https://msdn.microsoft.com/library/ms715892.aspx) y las entradas adecuadas para [DBPROP_UPDATABILITY](https://msdn.microsoft.com/library/ms722676.aspx) en el conjunto de propiedades mapa.  
  
 **Cambio**  
 Especifica que el consumidor acepta actualizaciones de datos de las filas del conjunto de filas.  
  
 **Insertar**  
 Especifica que el consumidor acepta la inserción de filas en el conjunto de filas.  
  
 **Eliminar**  
 Especifica que el consumidor acepta la eliminación de filas del conjunto de filas.  
  
## <a name="see-also"></a>Vea también  
 [Consumidor OLE DB ATL](../../atl/reference/adding-an-atl-ole-db-consumer.md)   
 [Agregar funcionalidad con los asistentes para código](../../ide/adding-functionality-with-code-wizards-cpp.md)   
 [Cadenas de conexión y vínculos de datos (OLE DB)](https://msdn.microsoft.com/library/ms718376.aspx)
