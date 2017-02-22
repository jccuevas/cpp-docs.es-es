---
title: "Asistente para consumidores OLE DB ATL | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "reference"
f1_keywords: 
  - "vc.codewiz.class.atl.consumer.overview"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "Asistente para consumidores OLE DB ATL"
  - "ATL projects, agregar consumidores OLE DB ATL"
  - "cadenas de conexión [C++], consumidores OLE DB"
ms.assetid: dcb68ed1-2224-422f-9f7b-108a74864204
caps.latest.revision: 13
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 13
---
# Asistente para consumidores OLE DB ATL
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

Este asistente configura una clase de consumidores OLE DB junto con los enlaces de datos necesarios para el acceso al origen de datos especificado a través del proveedor OLE DB especificado.  
  
> [!NOTE]
>  El asistente exige, para poder escribir nombres en los campos `Class` y **Archivo .h**, hacer clic en el botón **Origen de datos** y seleccionar un origen.  
  
## Lista de UIElement  
 **Origen de datos**  
 El botón **Origen de datos** le permite configurar el origen de datos especificado mediante el proveedor OLE DB especificado.  Cuando haga clic en este botón aparecerá el cuadro de diálogo **Propiedades de vínculo de datos**.  Para obtener más información acerca de cómo compilar cadenas de conexión y del cuadro de diálogo **Propiedades de vínculo de datos**, vea [Información general sobre la API de vínculos de datos](https://msdn.microsoft.com/en-us/library/ms718102.aspx) en la documentación de [!INCLUDE[winsdkshort](../../atl/reference/includes/winsdkshort_md.md)].  
  
> [!NOTE]
>  En versiones anteriores, al presionar la tecla MAYÚS y hacer clic en el botón **Origen de datos** se abría un cuadro de diálogo Abrir archivo en el que podía seleccionar un archivo de vínculo de datos \(.udl\).  Esta funcionalidad ya no se admite.  
  
 El cuadro de diálogo tiene cuatro fichas:  
  
-   Ficha **Proveedor**  
  
-   Ficha **Conexión**  
  
-   Ficha **Avanzadas**  
  
-   Ficha **Todo**  
  
     La siguiente información adicional describe las pestañas del cuadro de diálogo **Propiedades de vínculo de datos**.  
  
     Para terminar, haga clic en **Aceptar**.  Se abrirá el cuadro de diálogo **Seleccionar objeto de base de datos**.  En este cuadro de diálogo, seleccione la tabla, la vista o el procedimiento almacenado que deba usar el consumidor.  
  
     **Proveedor**  
     Seleccione un proveedor adecuado para administrar la conexión al origen de datos.  El tipo de proveedor suele estar determinado por el tipo de base de datos al que se conecta.  Haga clic en el botón `Next` o haga clic en la pestaña **Conexión**.  
  
     **Conexión**  
     El contenido de esta pestaña depende del proveedor seleccionado.  Aunque hay muchos tipos de proveedores, esta sección cubre las conexiones de los dos más habituales: datos de SQL y ODBC.  El resto son variaciones similares en los campos que aquí se describen.  
  
     Para datos de SQL:  
  
    1.  **Seleccione o escriba un nombre de servidor:** haga clic en el menú de lista desplegable para mostrar todos los servidores de datos registrados en la red y seleccione uno.  
  
    2.  **Escriba la información para iniciar sesión en el servidor:** escriba un nombre de usuario y una contraseña para iniciar sesión en el servidor de datos.  
  
    3.  **Seleccione la base de datos del servidor:** haga clic en el menú de lista desplegable para mostrar todas las bases de datos registradas en el servidor de datos y seleccione una.  
  
         O bien  
  
         **Adjuntar archivo de base de datos como nombre:** Especifica un archivo que se va a utilizar como base de datos; escriba el nombre de la ruta de acceso explícito.  
  
        > [!NOTE]
        >  Existe un problema de seguridad con la característica "Permitir guardar contraseña" del cuadro de diálogo Propiedades de vínculo de datos.  En “Especificar información para iniciar sesión en el servidor” hay dos botones de radio:  
  
         **Usar seguridad integrada de Windows NT**  
  
         **Usar un nombre de usuario y una contraseña específicos**  
  
         Si selecciona **Usar un nombre de usuario y una contraseña específicos**, tiene la opción de guardar la contraseña \(por medio de la casilla "Permitir guardar contraseña"\); no obstante, ésta es una opción poco segura.  Se recomienda seleccionar **Usar seguridad integrada de Windows NT**; esta opción es segura porque cifra la contraseña.  
  
         Puede que haya situaciones en las que desee seleccionar “Permitir guardar contraseña”. Por ejemplo, si se publica una biblioteca con una solución de bases de datos privada, no debe tener acceso a la base de datos directamente; en su lugar, debe utilizar una aplicación de nivel medio para comprobar el usuario \(a través de cualquier esquema de autenticación elegido\) y, a continuación, limitar la ordenación de los datos disponibles para el usuario.  
  
         Para datos de ODBC:  
  
         1.  **Especifique el origen de datos:** puede usar un nombre de origen de datos o una cadena de conexión.  
  
         **Usar el nombre del origen de datos:** esta lista desplegable muestra los orígenes de datos registrados en el equipo.  Puede configurar los orígenes de datos antes de tiempo mediante [ODBC Data Source Administrator](!Alink("dasdkODBCDataSourceAdmin")). o bien **Usar cadena de conexión:** Escriba una cadena de conexión que ya haya obtenido, o haga clic en el botón **Compilación**; aparecerá el cuadro de diálogo  **Seleccionar origen de datos**.  Seleccione un origen de datos de archivo o equipo y haga clic **Aceptar**.  
  
        > [!NOTE]
        >  Puede obtener una cadena de conexión viendo las propiedades de una conexión existente en el Explorador de servidores, o bien puede crear una conexión haciendo doble clic en **Agregar conexión** en el Explorador de servidores.  
  
         2.  **Escriba la información para iniciar sesión en el servidor:** escriba un nombre de usuario y una contraseña para iniciar sesión en el servidor de datos.  
  
         3.  Escriba el catálogo inicial para usar.  
  
         4.  Haga clic en **Probar conexión**; si la prueba se ejecuta correctamente, haga clic en **Aceptar**.  De lo contrario, compruebe la información de inicio de sesión, pruebe otra base de datos o pruebe otro servidor de datos.  
  
     **Avanzado**  
     **Configuración de red:** especifique el [Impersonation level](!Alink("_com_Impersonation_Levels")) \(el nivel de suplantación que se permite usar al servidos al suplantar al cliente; corresponde directamente a los niveles de suplantación RPC\) y **Nivel de protección** \(el nivel de protección de los datos enviados entre cliente y servidor; corresponde directamente a los niveles de protección RPC\).  
  
     **Otros:** en **Tiempo de espera de conexión**, especifique el número de segundos permitidos de tiempo de inactividad antes de que se agote el tiempo de espera.  En **Permisos de acceso**, especifique los permisos de acceso para la conexión de datos.  
  
     Para obtener más información sobre las propiedades de inicialización avanzadas, consulte la documentación de cada proveedor OLE DB concreto.  
  
     **Todos**  
     Esta pestaña muestra un resumen de las propiedades de inicialización para la conexión y el origen de datos especificados.  Estos valores se pueden editar.  
  
     Para terminar, haga clic en **Aceptar**.  Se abrirá el cuadro de diálogo **Seleccionar objeto de base de datos**.  En este cuadro de diálogo, seleccione la tabla, la vista o el procedimiento almacenado que deba usar el consumidor.  
  
 `Class`  
 Tras seleccionar un origen de datos, este cuadro se rellena con un nombre de clase predeterminado, basado en la tabla o el procedimiento almacenado que esté seleccionado \(vea **Seleccionar un origen de datos**, más abajo\).  Puede cambiar el nombre de la clase.  
  
 **Archivo .H**  
 Tras seleccionar un origen de datos, este cuadro se rellena con un nombre de la clase de encabezado predeterminada, basado en la tabla o el procedimiento almacenado que esté seleccionado \(vea **Seleccionar un origen de datos**, más abajo\).  Puede cambiar el nombre del archivo de encabezado o seleccionar un archivo ya existente.  
  
 **Con atributos**  
 Esta opción especifica si el asistente crea clases de consumidores mediante declaraciones de plantilla o mediante atributos.  Si selecciona esta opción, el asistente usa atributos en lugar de declaraciones de plantilla \(el valor predeterminado\).  Cuando se anula la selección de dicha opción, el asistente utiliza las declaraciones de plantilla en lugar de los atributos.  
  
-   Si selecciona un **Tipo** consumidor de Tabla, el asistente usa los atributos `db_source` y **db\_table** para crear las declaraciones de la tabla y los descriptores de acceso de la tabla, y utiliza **db\_column** para crear el mapa de columnas, por ejemplo:  
  
    ```  
    // Inject table class and table accessor class declarations  
    [  
        db_source("<initialization_string>"),  
        db_table("dbo.Orders")  
    ]  
    ...  
    // Column map  
        [ db_column(1, status=m_dwOrderIDStatus,         length=m_dwOrderIDLength) ] LONG m_OrderID;  
        [ db_column(2, status=m_dwCustomerIDStatus,         length=m_dwCustomerIDLength) ] TCHAR m_CustomerID[6];  
        ...  
    ```  
  
     en lugar de utilizar la clase de plantilla `CTable` para declarar la clase de la tabla y los descriptores de acceso a la tabla, y las macros BEGIN\_COLUMN\_MAP y END\_COLUMN\_MAP para crear el mapa de columnas, por ejemplo:  
  
    ```  
    // Table accessor class  
    class COrdersAccessor;  
    // Table class  
    class COrders : public CTable<CAccessor<COrdersAccessor> >;  
    ...  
    // Column map  
    BEGIN_COLUMN_MAP(COrderDetailsAccessor)  
        COLUMN_ENTRY_LENGTH_STATUS(1, m_OrderID,         m_dwOrderIDLength, m_dwOrderIDStatus)  
        COLUMN_ENTRY_LENGTH_STATUS(2, m_CustomerID,         m_dwCustomerIDLength, m_dwCustomerIDStatus)  
        ...  
    END_COLUMN_MAP()  
    ```  
  
-   Si selecciona un **Tipo** de consumidor de Comando, el asistente utiliza los atributos `db_source` y **db\_command**, y utiliza **db\_column** para crear el mapa de columnas, por ejemplo:  
  
    ```  
    [  
        db_source("<initialization_string>"),  
        db_command("SQL_command")  
    ]  
    ...  
    // Column map using db_column is the same as for consumer type of 'table'  
    ```  
  
     en lugar de utilizar las declaraciones de clase de comando y descriptores de acceso para comando en el archivo .h de la clase comando, por ejemplo:  
  
    ```  
    Command accessor class:  
    class CListOrdersAccessor;  
    Command class:  
    class CListOrders : public CCommand<CAccessor<CListOrdersAccessor> >;  
    ...  
    // Column map using BEGIN_COLUMN_MAP ... END_COLUMN_MAP is the same as  
    // for consumer type of 'table'  
    ```  
  
 Para obtener más información, consulte [Basic Mechanics of Attributes](../../windows/basic-mechanics-of-attributes.md).  
  
 **Tipo**  
 Seleccione uno de los botones de radio siguientes para especificar si la clase de consumidores se deriva de `CTable` o de `CCommand` \(predeterminado\).  
  
 **Tabla**  
 Seleccione esta opción si desea usar `CTable` o **db\_table** para crear las declaraciones de la tabla y la clase de descriptor de acceso de la tabla.  
  
 **Command**  
 Seleccione esta opción si desea usar `CCommand` o **db\_command** para crear las declaraciones del comando y la clase de descriptor de acceso del comando.  Éste es el valor predeterminado.  
  
 **Compatibilidad**  
 Active las casillas para especificar las clases de actualizaciones que se aceptan en el consumidor \(el valor predeterminado es ninguna\).  Cada una de las siguientes define [DBPROP\_IRowsetChange](https://msdn.microsoft.com/en-us/library/ms715892.aspx) y las entradas apropiadas de [DBPROP\_UPDATABILITY](https://msdn.microsoft.com/en-us/library/ms722676.aspx) en el mapa de definición de propiedades.  
  
 **Change**  
 Especifica que el consumidor acepta actualizaciones de datos de fila en el conjunto de filas.  
  
 **Insert**  
 Especifica que el consumidor acepta la inserción de filas en el conjunto de filas.  
  
 **Eliminar**  
 Especifica que el consumidor acepta la eliminación de filas del conjunto de filas.  
  
## Vea también  
 [ATL OLE DB Consumer](../../atl/reference/adding-an-atl-ole-db-consumer.md)   
 [Agregar funcionalidad con los Asistentes para código](../../ide/adding-functionality-with-code-wizards-cpp.md)   
 [Cadenas de conexión y vínculos de datos \(OLE DB\)](https://msdn.microsoft.com/en-us/library/ms718376.aspx)