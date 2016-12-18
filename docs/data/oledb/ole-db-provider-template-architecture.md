---
title: "Arquitectura de plantillas de proveedores OLE DB | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "arquitectura [C++], proveedor OLE DB"
  - "OLE DB [C++], modelo de objetos"
  - "plantillas del proveedor OLE DB, modelo de objetos"
ms.assetid: 639304a3-f9e0-44dc-8d0c-0ebd2455b363
caps.latest.revision: 7
caps.handback.revision: 7
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# Arquitectura de plantillas de proveedores OLE DB
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

## Orígenes de datos y sesiones  
 La arquitectura de proveedor OLE DB incluye un objeto de origen de datos y una o más sesiones.  El objeto de origen de datos es el objeto de inicio del que todo proveedor debe crear una instancia.  Cuando una aplicación de consumidor necesita datos, participa en la creación del objeto de origen de datos para iniciar el proveedor.  El objeto de origen de datos crea un objeto de sesión \(mediante la interfaz **IDBCreateSession**\) a través del cuál el consumidor se conecta al objeto de origen de datos.  Los programadores de ODBC pueden considerar que el objeto de origen de datos es equivalente a **HENV** y el objeto de sesión, equivalente a **HDBC**.  
  
 ![Arquitectura de proveedor](../../data/oledb/media/vc4twb1.png "vc4TWB1")  
  
 Junto con los archivos de código fuente creados por el Asistente para proveedores OLE DB, las plantillas OLE DB implementan un objeto de origen de datos.  Una sesión es un objeto que corresponde al **TSession** de OLE DB.  
  
## Interfaces obligatorias e interfaces opcionales  
 Las plantillas de proveedor OLE DB proporcionan implementaciones ya preparadas para todas las interfaces necesarias.  OLE DB define interfaces obligatorias e interfaces opcionales para varios tipos de objetos:  
  
-   [Origen de datos](../../data/oledb/data-source-object-interfaces.md)  
  
-   [Session](../../data/oledb/session-object-interfaces.md)  
  
-   [Conjunto de filas](../../data/oledb/rowset-object-interfaces.md)  
  
-   [Command](../../data/oledb/command-object-interfaces.md)  
  
-   [Transacción](../../data/oledb/transaction-object-interfaces.md)  
  
 Tenga en cuenta que las plantillas de proveedor OLE DB no implementan los objetos de fila y de almacenamiento.  
  
 En la tabla siguiente se muestran las interfaces obligatorias y opcionales para los objetos anteriores, según la [Documentación del SDK de OLE DB 2.6](https://msdn.microsoft.com/en-us/library/ms722784.aspx).  
  
|Componente|Interfaz|Comment|  
|----------------|--------------|-------------|  
|[Origen de datos](../../data/oledb/data-source-object-interfaces.md) \([CDataSource](../../data/oledb/cdatasource-class.md)\)|\[obligatoria\] **IDBCreateSession**<br /><br /> \[obligatoria\] **IDBInitialize**<br /><br /> \[obligatoria\] `IDBProperties`<br /><br /> \[obligatoria\] `IPersist`<br /><br /> \[opcional\] **IConnectionPointContainer**<br /><br /> \[opcional\] **IDBAsynchStatus**<br /><br /> \[opcional\] **IDBDataSourceAdmin**<br /><br /> \[opcional\] **IDBInfo**<br /><br /> \[opcional\] `IPersistFile`<br /><br /> \[opcional\] **ISupportErrorInfo**|Conexión desde el consumidor al proveedor.  El objeto se utiliza para especificar propiedades en la conexión, como el identificador de usuario, la contraseña y el nombre del origen de datos.  También se puede utilizar el objeto para administrar un origen de datos \(crear, actualizar, eliminar, tablas, etc.\).|  
|[Sesión](../../data/oledb/session-object-interfaces.md) \([CSession](../../data/oledb/cdataconnection-operator-csession-amp.md)\)|\[obligatoria\] **IGetDataSource**<br /><br /> \[obligatoria\] `IOpenRowset`<br /><br /> \[obligatoria\] **ISessionProperties**<br /><br /> \[opcional\] **IAlterIndex**<br /><br /> \[opcional\] **IAlterTable**<br /><br /> \[opcional\] **IBindResource**<br /><br /> \[opcional\] **ICreateRow**<br /><br /> \[opcional\] **IDBCreateCommand**<br /><br /> \[opcional\] **IDBSchemaRowset**<br /><br /> \[opcional\] **IIndexDefinition**<br /><br /> \[opcional\] **ISupportErrorInfo**<br /><br /> \[opcional\] **ITableCreation**<br /><br /> \[opcional\] **ITableDefinition**<br /><br /> \[opcional\] **ITableDefinitionWithConstraints**<br /><br /> \[opcional\] **ITransaction**<br /><br /> \[opcional\] **ITransactionJoin**<br /><br /> \[opcional\] **ITransactionLocal**<br /><br /> \[opcional\] **ITransactionObject**|El objeto de sesión representa una sola conversación entre un consumidor y un proveedor.  Se parece en cierto modo al **HSTMT** de ODBC en el que puede haber muchas sesiones activas simultáneamente.<br /><br /> El objeto de sesión es el vínculo principal para obtener la funcionalidad de OLE DB.  Para obtener un objeto de comando, de transacción o de conjunto de filas, debe utilizar el objeto de sesión.|  
|[Conjunto de filas](../../data/oledb/rowset-object-interfaces.md) \([CRowset](../../data/oledb/crowset-class.md)\)|\[obligatoria\] `IAccessor`<br /><br /> \[obligatoria\] `IColumnsInfo`<br /><br /> \[obligatoria\] **IConvertType**<br /><br /> \[obligatoria\] `IRowset`<br /><br /> \[obligatoria\] `IRowsetInfo`<br /><br /> \[opcional\] **IChapteredRowset**<br /><br /> \[opcional\] **IColumnsInfo2**<br /><br /> \[opcional\] **IColumnsRowset**<br /><br /> \[opcional\] **IConnectionPointContainer**<br /><br /> \[opcional\] **IDBAsynchStatus**<br /><br /> \[opcional\] **IGetRow**<br /><br /> \[opcional\] `IRowsetChange`<br /><br /> \[opcional\] **IRowsetChapterMember**<br /><br /> \[opcional\] **IRowsetCurrentIndex**<br /><br /> \[opcional\] **IRowsetFind**<br /><br /> \[opcional\] **IRowsetIdentity**<br /><br /> \[opcional\] **IRowsetIndex**<br /><br /> \[opcional\] `IRowsetLocate`<br /><br /> \[opcional\] **IRowsetRefresh**<br /><br /> \[opcional\] `IRowsetScroll`<br /><br /> \[opcional\] `IRowsetUpdate`<br /><br /> \[opcional\] **IRowsetView**<br /><br /> \[opcional\] **ISupportErrorInfo**<br /><br /> \[opcional\] **IRowsetBookmark**|El objeto de conjunto de filas representa los datos del origen de datos.  Este objeto se encarga de los enlaces de esos datos y de las operaciones básicas \(actualización, búsqueda, transferencia, entre otras\) realizadas con los datos.  Siempre tiene un objeto de conjunto de filas para contener y manipular datos.|  
|[Comando](../../data/oledb/command-object-interfaces.md) \([CCommand](http://msdn.microsoft.com/es-es/52bef5da-c1a0-4223-b4e6-9e464b6db409)\)|\[obligatoria\] `IAccessor`<br /><br /> \[obligatoria\] `IColumnsInfo`<br /><br /> \[obligatoria\] `ICommand`<br /><br /> \[obligatoria\] **ICommandProperties**<br /><br /> \[obligatoria\] `ICommandText`<br /><br /> \[obligatoria\] **IConvertType**<br /><br /> \[opcional\] **IColumnsRowset**<br /><br /> \[opcional\] **ICommandPersist**<br /><br /> \[opcional\] **ICommandPrepare**<br /><br /> \[opcional\] `ICommandWithParameters`<br /><br /> \[opcional\] **ISupportErrorInfo**<br /><br /> \[opcional\] **ICommandStream**|El objeto de comando controla operaciones realizadas con los datos, tales como consultas.  Puede controlar instrucciones parametrizadas e instrucciones no parametrizadas.<br /><br /> El objeto de comando también se encarga de controlar los enlaces para parámetros y columnas de resultados.  Un enlace es una estructura que contiene información sobre cómo recuperar una columna de un conjunto de filas.  Contiene información como, por ejemplo, el ordinal, el tipo de datos, la longitud y el estado.|  
|[Transacción](../../data/oledb/transaction-object-interfaces.md) \(opcional\)|\[obligatoria\] **IConnectionPointContainer**<br /><br /> \[obligatoria\] **ITransaction**<br /><br /> \[opcional\] **ISupportErrorInfo**|El objeto de transacción define una unidad atómica de trabajo en un origen de datos y determina la relación entre las unidades de trabajo.  Las plantillas de proveedor OLE DB no ofrecen directamente compatibilidad con este objeto \(es decir, el programador debe crear su propio objeto\).|  
  
 Para obtener más información, vea los temas siguientes:  
  
-   [Mapas de propiedades](../../data/oledb/property-maps.md)  
  
-   [El registro de usuario](../../data/oledb/user-record.md)  
  
## Vea también  
 [Plantillas de proveedores OLE DB](../../data/oledb/ole-db-provider-templates-cpp.md)   
 [OLE DB Interfaces](https://msdn.microsoft.com/en-us/library/ms709709.aspx)