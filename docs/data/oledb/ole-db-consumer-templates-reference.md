---
title: Referencia de plantillas de consumidor OLE DB | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-data
ms.topic: reference
f1_keywords:
- vc-attr.db_param
- vc-attr.db_column
- vc-attr.db_accessor
- vc-attr.db_command
- vc-attr.db_table
- vc.templates.ole
- vc-attr.db_source
dev_langs:
- C++
helpviewer_keywords:
- OLE DB consumer templates, classes
ms.assetid: cfc7f698-1a0e-4a09-a4d3-ccb99e6654fe
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- data-storage
ms.openlocfilehash: 4a4a96ca189c8363d4aaf8df17e00b2419715086
ms.sourcegitcommit: 889a75be1232817150be1e0e8d4d7f48f5993af2
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 07/30/2018
ms.locfileid: "39337958"
---
# <a name="ole-db-consumer-templates-reference"></a>Referencia de plantillas de consumidor OLE DB
Las plantillas de consumidor OLE DB contienen las siguientes clases. El material de referencia también incluye temas sobre la [macros para plantillas de consumidor OLE DB](../../data/oledb/macros-and-global-functions-for-ole-db-consumer-templates.md).  
  
## <a name="session-classes"></a>Clases de la sesión  
 [CDataConnection](../../data/oledb/cdataconnection-class.md)  
 Administra la conexión con el origen de datos. Se trata de una clase útil para crear clientes porque encapsula los objetos necesarios (origen de datos y sesión) y parte del trabajo que debe hacer cuando se conecta a un origen de datos.  
  
 [CDataSource](../../data/oledb/cdatasource-class.md)  
 Corresponde a un objeto de origen de datos OLE DB, que representa una conexión a través de un proveedor a un origen de datos. Uno o más sesiones base de datos, representado cada uno por un `CSession` de objetos, puede tener lugar en una sola conexión.  
  
 [CEnumerator](../../data/oledb/cenumerator-class.md)  
 Corresponde a un objeto de enumerador OLE DB, que recupera información de conjunto de filas sobre orígenes de datos disponibles.  
  
 [CEnumeratorAccessor](../../data/oledb/cenumeratoraccessor-class.md)  
 Utilizado por `CEnumerator` para tener acceso a los datos desde el conjunto de filas del enumerador. Este conjunto de filas se compone de los orígenes de datos y enumeradores visibles desde el enumerador actual.  
  
 [CSession](../../data/oledb/csession-class.md)  
 Representa una sesión de acceso de la base de datos única. Una o varias sesiones se pueden asociadas con cada `CDataSource` objeto.  
  
## <a name="accessor-classes"></a>Clases de descriptor de acceso  
 [CAccessor](../../data/oledb/caccessor-class.md)  
 Se usa para los registros que están enlazados estáticamente a un origen de datos. Utilice esta clase de descriptor de acceso cuando conoce la estructura del origen de datos.  
  
 [CAccessorBase](../../data/oledb/caccessorbase-class.md)  
 Clase base para todas las clases de descriptor de acceso.  
  
 [CDynamicAccessor](../../data/oledb/cdynamicaccessor-class.md)  
 Un descriptor de acceso que se puede crear en tiempo de ejecución, según la información de columna del conjunto de filas. Utilice esta clase para recuperar datos si no conoce la estructura del origen de datos.  
  
 [CDynamicParameterAccessor](../../data/oledb/cdynamicparameteraccessor-class.md)  
 Un descriptor de acceso que se puede usar cuando los tipos de comando están desconocidos. Obtiene la información de parámetros mediante una llamada a la `ICommandWithParameters` interfaz, si el proveedor admite la interfaz.  
  
 [CDynamicStringAccessor](../../data/oledb/cdynamicstringaccessor-class.md)  
 Permite obtener acceso a un origen de datos cuando no tiene conocimiento de la estructura subyacente de la base de datos.  
  
 [CDynamicStringAccessorA](../../data/oledb/cdynamicstringaccessora-class.md)  
 Similar a `CDynamicStringAccessor` , salvo que esta clase solicita acceso desde el almacén de datos como datos de cadena ANSI de datos.  
  
 [CDynamicStringAccessorW](../../data/oledb/cdynamicstringaccessorw-class.md)  
 Similar a `CDynamicStringAccessor` , salvo que esta clase solicita acceso desde el almacén de datos como datos de cadena UNICODE de datos.  
  
 [CManualAccessor](../../data/oledb/cmanualaccessor-class.md)  
 Un descriptor de acceso con los métodos para controlar las columnas y parámetros de comando. Con esta clase, puede usar los tipos de datos siempre y cuando el proveedor puede convertir al tipo.  
  
 [CNoAccessor](../../data/oledb/cnoaccessor-class.md)  
 Se puede usar como argumento de plantilla cuando no desea que la clase para admitir parámetros o columnas de salida.  
  
 [CXMLAccessor](../../data/oledb/cxmlaccessor-class.md)  
 Similar a `CDynamicStringAccessor` , salvo que esta clase convierte todos los datos que se obtiene acceso desde el almacén de datos como datos (etiquetados) en formato XML.  
  
## <a name="rowset-classes"></a>Clases de conjunto de filas  
 [CAccessorRowset](../../data/oledb/caccessorrowset-class.md)  
 Encapsula un conjunto de filas y sus descriptores de acceso asociados.  
  
 [CArrayRowset](../../data/oledb/carrayrowset-class.md)  
 Se usa para tener acceso a elementos de un conjunto de filas mediante la sintaxis de la matriz.  
  
 [CBulkRowset](../../data/oledb/cbulkrowset-class.md)  
 Se utiliza para capturar y manipular las filas de forma masiva mediante la recuperación de varios identificadores de fila con una sola llamada.  
  
 [CNoRowset](../../data/oledb/cnorowset-class.md)  
 Puede usarse como un argumento de plantilla, si el comando no devuelve un conjunto de filas.  
  
 [cRestrictions](../../data/oledb/crestrictions-class.md)  
 Se utiliza para especificar restricciones para los conjuntos de filas de esquema.  
  
 [CRowset](../../data/oledb/crowset-class.md)  
 Se usa para manipular, establecer y recuperar datos del conjunto de filas.  
  
 [CStreamRowset](../../data/oledb/cstreamrowset-class.md)  
 Devuelve un `ISequentialStream` objeto en lugar de un conjunto de filas; a continuación, usar el `Read` método para recuperar datos en formato XML. (SQL Server 2000 se aplica el formato; tenga en cuenta que esta característica funciona con SQL Server 2000 sólo).  
  
 [IRowsetNotifyImpl](../../data/oledb/irowsetnotifyimpl-class.md)  
 Proporciona una implementación ficticia para `IRowsetNotify`, con funciones vacías para el `IRowsetNotify` métodos `OnFieldChange`, `OnRowChange`, y `OnRowsetChange`.  
  
 [Clases de conjunto de filas de esquema y clases typedef](../../data/oledb/schema-rowset-classes-and-typedef-classes.md)  
  
 Las plantillas OLE DB proporcionan un conjunto de clases que corresponden a los conjuntos de filas de esquema OLE DB.  
  
## <a name="command-classes"></a>Clases de comandos  
 [CCommand](../../data/oledb/ccommand-class.md)  
 Se usa para establecer y ejecutar un comando de OLE DB basadas en parámetros. Para abrir simplemente un simple conjunto de filas, use `CTable` en su lugar.  
  
 [CMultipleResults](../../data/oledb/cmultipleresults-class.md)  
 Usar como un argumento de plantilla para el `CCommand` plantilla cuando desee que el comando para controlar varios conjuntos de resultados.  
  
 [CNoAccessor](../../data/oledb/cnoaccessor-class.md)  
 Usar como argumento de plantilla para las clases de plantilla, como `CCommand` y `CTable`, que toman un argumento de la clase de descriptor de acceso. Use `CNoAccessor` si no desea que la clase para admitir parámetros o columnas de salida.  
  
 [CNoMultipleResults](../../data/oledb/cnomultipleresults-class.md)  
 Usar como un argumento de plantilla para el `CCommand` plantilla cuando desee que el comando para controlar un conjunto de filas único. `CNoMultipleResults` es el valor predeterminado para el argumento de plantilla.  
  
 [CNoRowset](../../data/oledb/cnorowset-class.md)  
 Usar como un argumento de plantilla para `CCommand` o `CTable` si el comando o la tabla no devuelve un conjunto de filas.  
  
 [CTable](../../data/oledb/ctable-class.md)  
 Se utiliza para tener acceso a un conjunto de filas simple sin parámetros.  
  
## <a name="property-classes"></a>Clases de propiedad  
 [CDBPropIDSet](../../data/oledb/cdbpropidset-class.md)  
 Se usa para pasar una matriz de identificadores de propiedad para el que el consumidor desea información de la propiedad. Las propiedades pertenecen a una propiedad establecida.  
  
 [CDBPropSet](../../data/oledb/cdbpropset-class.md)  
 Se usa para establecer las propiedades de un proveedor.  
  
## <a name="bookmark-class"></a>Clase de marcador  
 [CBookmark](../../data/oledb/cbookmark-class.md)  
 Se usa como índice para tener acceso a datos en un conjunto de filas.  
  
## <a name="error-class"></a>Error (clase)  
 [CDBErrorInfo](../../data/oledb/cdberrorinfo-class.md)  
 Se utiliza para recuperar información de error de OLE DB.  
  
## <a name="see-also"></a>Vea también  
 [Referencia de plantillas de proveedores OLE DB](../../data/oledb/ole-db-provider-templates-reference.md)   
 [Plantillas OLE DB](../../data/oledb/ole-db-templates.md)