---
title: Arquitectura de la plantilla de proveedores OLE DB | Documentos de Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: C++
helpviewer_keywords:
- OLE DB [C++], object model
- architecture [C++], OLE DB Provider
- OLE DB provider templates, object model
ms.assetid: 639304a3-f9e0-44dc-8d0c-0ebd2455b363
caps.latest.revision: "7"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
- data-storage
ms.openlocfilehash: 8c1baa921f4a12aae40a01995cfd0b638cf614d8
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 12/21/2017
---
# <a name="ole-db-provider-template-architecture"></a>Arquitectura de plantillas de proveedores OLE DB
## <a name="data-sources-and-sessions"></a>Orígenes de datos y sesiones  
 La arquitectura del proveedor OLE DB incluye un objeto de origen de datos y una o varias sesiones. El objeto de origen de datos es el objeto inicial que debe crear una instancia de cada proveedor. Cuando una aplicación de consumidor necesita datos, compartir crea el objeto de origen de datos para iniciar el proveedor. El objeto de origen de datos crea un objeto de sesión (mediante el **IDBCreateSession** interfaz) a través de que el consumidor se conecta al objeto de origen de datos. Los programadores ODBC pueden considerar del objeto de origen de datos es equivalente a la **HENV** y el objeto de sesión como equivalente a la **HDBC**.  
  
 ![Arquitectura de proveedor](../../data/oledb/media/vc4twb1.gif "vc4twb1")  
  
 Junto con los archivos de origen creados por el Asistente para proveedores OLE DB, las plantillas OLE DB implementan un objeto de origen de datos. Una sesión es un objeto que corresponde a OLE DB **TSession**.  
  
## <a name="mandatory-and-optional-interfaces"></a>Interfaces obligatorias y opcionales  
 Las plantillas de proveedor OLE DB proporcionan implementaciones ya preparadas para todas las interfaces requeridas. Interfaces obligatorias y opcionales se definen por OLE DB para varios tipos de objetos:  
  
-   [Origen de datos](../../data/oledb/data-source-object-interfaces.md)  
  
-   [Sesión](../../data/oledb/session-object-interfaces.md)  
  
-   [Conjunto de filas](../../data/oledb/rowset-object-interfaces.md)  
  
-   [Comando](../../data/oledb/command-object-interfaces.md)  
  
-   [Transacción](../../data/oledb/transaction-object-interfaces.md)  
  
 Tenga en cuenta que las plantillas de proveedor OLE DB no implementan los objetos de fila y de almacenamiento.  
  
 En la tabla siguiente se enumera las interfaces obligatorias y opcionales para los objetos enumerados anteriormente, según la [documentación del SDK de OLE DB 2.6](https://msdn.microsoft.com/en-us/library/ms722784.aspx).  
  
|Componente|Interfaz|Comentario|  
|---------------|---------------|-------------|  
|[Origen de datos](../../data/oledb/data-source-object-interfaces.md) ([CDataSource](../../data/oledb/cdatasource-class.md))|[obligatorio] **IDBCreateSession**<br /><br /> [obligatorio] **IDBInitialize**<br /><br /> [obligatorio]`IDBProperties`<br /><br /> [obligatorio]`IPersist`<br /><br /> [opcional] **IConnectionPointContainer**<br /><br /> [opcional] **IDBAsynchStatus**<br /><br /> [opcional] **IDBDataSourceAdmin**<br /><br /> [opcional] **IDBInfo**<br /><br /> [opcional]`IPersistFile`<br /><br /> [opcional] **ISupportErrorInfo**|Conexión del consumidor al proveedor. El objeto se usa para especificar las propiedades de la conexión como nombre de origen de datos, la contraseña y el Id. de usuario. El objeto también puede utilizarse para administrar un origen de datos (crear, actualizar, eliminar, tablas y así sucesivamente).|  
|[Sesión](../../data/oledb/session-object-interfaces.md) ([CSession](../../data/oledb/cdataconnection-operator-csession-amp.md))|[obligatorio] **IGetDataSource**<br /><br /> [obligatorio]`IOpenRowset`<br /><br /> [obligatorio] **ISessionProperties**<br /><br /> [opcional] **IAlterIndex**<br /><br /> [opcional] **IAlterTable**<br /><br /> [opcional] **IBindResource**<br /><br /> [opcional] **ICreateRow**<br /><br /> [opcional] **IDBCreateCommand**<br /><br /> [opcional] **IDBSchemaRowset**<br /><br /> [opcional] **IIndexDefinition**<br /><br /> [opcional] **ISupportErrorInfo**<br /><br /> [opcional] **ITableCreation**<br /><br /> [opcional] **ITableDefinition**<br /><br /> [opcional] **ITableDefinitionWithConstraints**<br /><br /> [opcional] **ITransaction**<br /><br /> [opcional] **ITransactionJoin**<br /><br /> [opcional] **ITransactionLocal**<br /><br /> [opcional] **ITransactionObject**|El objeto de sesión representa una sola conversación entre un consumidor y proveedor. Es similar a ODBC **HSTMT** en que puede haber muchas sesiones simultáneas activas.<br /><br /> El objeto de sesión es el vínculo principal para llegar a la funcionalidad de OLE DB. Para llegar a un comando, la transacción o el objeto de conjunto de filas, vaya a través del objeto de sesión.|  
|[Conjunto de filas](../../data/oledb/rowset-object-interfaces.md) ([CRowset](../../data/oledb/crowset-class.md))|[obligatorio]`IAccessor`<br /><br /> [obligatorio]`IColumnsInfo`<br /><br /> [obligatorio] **IConvertType**<br /><br /> [obligatorio]`IRowset`<br /><br /> [obligatorio]`IRowsetInfo`<br /><br /> [opcional] **IChapteredRowset**<br /><br /> [opcional] **IColumnsInfo2**<br /><br /> [opcional] **IColumnsRowset**<br /><br /> [opcional] **IConnectionPointContainer**<br /><br /> [opcional] **IDBAsynchStatus**<br /><br /> [opcional] **IGetRow**<br /><br /> [opcional]`IRowsetChange`<br /><br /> [opcional] **IRowsetChapterMember**<br /><br /> [opcional] **IRowsetCurrentIndex**<br /><br /> [opcional] **IRowsetFind**<br /><br /> [opcional] **IRowsetIdentity**<br /><br /> [opcional] **IRowsetIndex**<br /><br /> [opcional]`IRowsetLocate`<br /><br /> [opcional] **IRowsetRefresh**<br /><br /> [opcional]`IRowsetScroll`<br /><br /> [opcional]`IRowsetUpdate`<br /><br /> [opcional] **IRowsetView**<br /><br /> [opcional] **ISupportErrorInfo**<br /><br /> [opcional] **IRowsetBookmark**|El objeto de conjunto de filas representa los datos del origen de datos. El objeto es responsable de los enlaces de datos y las operaciones básicas (actualización, fetch, movimiento y otros) en los datos. Siempre que un objeto de conjunto de filas para contener y manipular datos.|  
|[Comando](../../data/oledb/command-object-interfaces.md) ([CCommand](http://msdn.microsoft.com/en-us/52bef5da-c1a0-4223-b4e6-9e464b6db409))|[obligatorio]`IAccessor`<br /><br /> [obligatorio]`IColumnsInfo`<br /><br /> [obligatorio]`ICommand`<br /><br /> [obligatorio] **ICommandProperties**<br /><br /> [obligatorio]`ICommandText`<br /><br /> [obligatorio] **IConvertType**<br /><br /> [opcional] **IColumnsRowset**<br /><br /> [opcional] **ICommandPersist**<br /><br /> [opcional] **ICommandPrepare**<br /><br /> [opcional]`ICommandWithParameters`<br /><br /> [opcional] **ISupportErrorInfo**<br /><br /> [opcional] **ICommandStream**|El objeto de comando controla las operaciones en los datos como las consultas. Puede controlar las instrucciones con parámetros o sin parámetros.<br /><br /> El objeto de comando también es responsable de controlar los enlaces para los parámetros y columnas de salida. Un enlace es una estructura que contiene información sobre cómo se debe recuperar una columna de un conjunto de filas. Contiene información como ordinal, tipo de datos, longitud y estado.|  
|[Transacción](../../data/oledb/transaction-object-interfaces.md) (opcional)|[obligatorio] **IConnectionPointContainer**<br /><br /> [obligatorio] **ITransaction**<br /><br /> [opcional] **ISupportErrorInfo**|El objeto de transacción define una unidad atómica de trabajo en un origen de datos y determina cómo se relacionan entre sí las unidades de trabajo. Este objeto no es compatible directamente con las plantillas de proveedor OLE DB (es decir, crear su propio objeto).|  
  
 Para obtener más información, vea los temas siguientes:  
  
-   [Mapas de propiedades](../../data/oledb/property-maps.md)  
  
-   [El registro de usuario](../../data/oledb/user-record.md)  
  
## <a name="see-also"></a>Vea también  
 [Plantillas del proveedor OLE DB](../../data/oledb/ole-db-provider-templates-cpp.md)   
 [Interfaces OLE DB](https://msdn.microsoft.com/en-us/library/ms709709.aspx)