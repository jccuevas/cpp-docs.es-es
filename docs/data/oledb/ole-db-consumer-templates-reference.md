---
title: "Referencia de plantillas de consumidor OLE DB | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "vc-attr.db_param"
  - "vc-attr.db_column"
  - "vc-attr.db_accessor"
  - "vc-attr.db_command"
  - "vc-attr.db_table"
  - "vc.templates.ole"
  - "vc-attr.db_source"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "plantillas de consumidor OLE DB, clases"
ms.assetid: cfc7f698-1a0e-4a09-a4d3-ccb99e6654fe
caps.latest.revision: 7
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 7
---
# Referencia de plantillas de consumidor OLE DB
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

Las plantillas de consumidor OLE DB contienen clases siguientes.  El material de referencia también incluye temas de [macros para plantillas de consumidor OLE DB](../../data/oledb/macros-and-global-functions-for-ole-db-consumer-templates.md).  
  
## Clases de sesión  
 [CDataConnection](../../data/oledb/cdataconnection-class.md)  
 Administra la conexión con el origen de datos.  Esta es una clase útil para crear clientes porque encapsula objetos necesarios \(origen de datos y sesión\) y algunos de trabajo necesario al conectarse a un origen de datos.  
  
 [CDataSource](../../data/oledb/cdatasource-class.md)  
 Corresponde al origen de datos OLE DB un objeto, que representa una conexión a través de un proveedor a un origen de datos.  Una o varias sesiones de base de datos, cada representada por un objeto de `CSession` , pueden tener lugar en una sola conexión.  
  
 [CEnumerator](../../data/oledb/cenumerator-class.md)  
 Corresponde al enumerador OLE DB un objeto, que recupera información del conjunto de filas sobre orígenes de datos disponibles.  
  
 [CEnumeratorAccessor](../../data/oledb/cenumeratoraccessor-class.md)  
 Utilizado por `CEnumerator` para tener acceso a los datos del conjunto de filas de enumeradores.  Este conjunto de filas está formado por los orígenes de datos y los enumeradores visible del enumerador actual.  
  
 [CSession](../../data/oledb/csession-class.md)  
 Representa una sesión única de acceso a la base de datos.  Una o más sesiones pueden estar asociadas a cada objeto de `CDataSource` .  
  
## Clases de descriptores de acceso  
 [CAccessor](../../data/oledb/caccessor-class.md)  
 Se utiliza para los registros que están enlazados estáticamente a un origen de datos.  Utilice esta clase de descriptor de acceso si conoce la estructura del origen de datos.  
  
 [CAccessorBase](../../data/oledb/caccessorbase-class.md)  
 Clase base para todas las clases de descriptor de acceso.  
  
 [CDynamicAccessor](../../data/oledb/cdynamicaccessor-class.md)  
 Un descriptor de acceso que puede crear en tiempo de ejecución, basándose en la información de columna del conjunto de filas.  Utilice esta clase para recuperar datos si no conoce la estructura del origen de datos.  
  
 [CDynamicParameterAccessor](../../data/oledb/cdynamicparameteraccessor-class.md)  
 Un descriptor de acceso que se puede utilizar cuando los tipos de comando son desconocidos.  Obtiene la información de parámetros llamando a la interfaz de `ICommandWithParameters` , si el proveedor admite la interfaz.  
  
 [CDynamicStringAccessor](../../data/oledb/cdynamicstringaccessor-class.md)  
 Permite obtener acceso a un origen de datos cuando no tiene conocimiento de la estructura subyacente de la base de datos.  
  
 [CDynamicStringAccessorA](../../data/oledb/cdynamicstringaccessora-class.md)  
 Similar a `CDynamicStringAccessor` salvo que esta clase solicita el primero del almacén de datos como datos de cadena ANSI.  
  
 [CDynamicStringAccessorW](../../data/oledb/cdynamicstringaccessorw-class.md)  
 Similar a `CDynamicStringAccessor` salvo que esta clase solicita el primero del almacén de datos como datos de cadena Unicode.  
  
 [CManualAccessor](../../data/oledb/cmanualaccessor-class.md)  
 Un descriptor de acceso con los métodos para administrar columnas y parámetros de comando.  Con esta clase, puede utilizar los tipos de datos mientras el proveedor puede convertir el tipo.  
  
 [CNoAccessor](../../data/oledb/cnoaccessor-class.md)  
 Se puede utilizar como argumento de plantilla cuando no desea la clase para admitir parámetros o generar columnas.  
  
 [CXMLAccessor](../../data/oledb/cxmlaccessor-class.md)  
 Similar a `CDynamicStringAccessor` salvo que esta clase convierte todos los datos acceso de almacén como datos \(etiquetados\) XML\- con formato.  
  
## Clases de conjuntos de filas  
 [CAccessorRowset](../../data/oledb/caccessorrowset-class.md)  
 Encapsula un conjunto de filas y sus descriptores de acceso asociados.  
  
 [CArrayRowset](../../data/oledb/carrayrowset-class.md)  
 Se utiliza para tener acceso a elementos de un conjunto de filas mediante sintaxis de matriz.  
  
 [CBulkRowset](../../data/oledb/cbulkrowset-class.md)  
 Se utiliza para capturar y manipular filas de forma masiva recuperar múltiples identificadores de fila con una única llamada.  
  
 [CNoRowset](../../data/oledb/cnorowset-class.md)  
 Se puede utilizar como argumento de plantilla si el comando no devuelve un conjunto de filas.  
  
 [CRestrictions](../../data/oledb/crestrictions-class.md)  
 Se utiliza para especificar las restricciones de conjuntos de filas de esquema.  
  
 [CRowset](../../data/oledb/crowset-class.md)  
 Se utiliza para manipular, para establecer, y recuperar datos del conjunto de filas.  
  
 [CStreamRowset](../../data/oledb/cstreamrowset-class.md)  
 Devuelve un objeto de `ISequentialStream` en lugar de un conjunto de filas; se utiliza el método de **de lectura** para recuperar datos en formato XML. \(SQL Server 2000 hace que el formato; observe que esta característica sólo funciona con SQL Server 2000.\)  
  
 [IRowsetNotifyImpl](../../data/oledb/irowsetnotifyimpl-class.md)  
 Proporciona una implementación ficticia para `IRowsetNotify`, con las funciones vacías para los métodos `OnFieldChange`, `OnRowChange`, y `OnRowsetChange`de `IRowsetNotify` .  
  
 [Clases de conjunto de filas de esquema y clases de Typedef](../../data/oledb/schema-rowset-classes-and-typedef-classes.md)  
  
 Las plantillas OLE DB proporcionan un conjunto de clases que corresponden a OLE DB conjuntos de filas de esquema.  
  
## Clases de comando  
 [CCommand](../../data/oledb/ccommand-class.md)  
 Se utiliza para establecer y ejecutar un comando parámetro\- basado en OLE DB.  Para abrir simplemente un conjunto de filas, utilice `CTable` en su lugar.  
  
 [CMultipleResults](../../data/oledb/cmultipleresults-class.md)  
 Usa como argumento de plantilla para la plantilla de `CCommand` cuando desee que el comando de controlar varios conjuntos de resultados.  
  
 [CNoAccessor](../../data/oledb/cnoaccessor-class.md)  
 Usa como argumento de plantilla para las clases de plantilla, como `CCommand` y `CTable`, que toman un argumento de la clase de descriptor de acceso.  Utilice `CNoAccessor` si no desea que la clase para admitir parámetros o generar columnas.  
  
 [CNoMultipleResults](../../data/oledb/cnomultipleresults-class.md)  
 Usa como argumento de plantilla para la plantilla de `CCommand` cuando desee que el comando de controlar un único conjunto de filas.  `CNoMultipleResults` es el valor predeterminado para el argumento de plantilla.  
  
 [CNoRowset](../../data/oledb/cnorowset-class.md)  
 Usa como argumento de plantilla para `CCommand` o `CTable` si el comando o la tabla no devuelve un conjunto de filas.  
  
 [CTable](../../data/oledb/ctable-class.md)  
 Se utiliza para tener acceso a un conjunto de filas sin parámetros.  
  
## Clases de propiedad  
 [CDBPropIDSet](../../data/oledb/cdbpropidset-class.md)  
 Utilizado para pasar una matriz de los id. de propiedad para los que el consumidor desea información de la propiedad.  Las propiedades pertenecen a un conjunto de propiedades.  
  
 [CDBPropSet](../../data/oledb/cdbpropset-class.md)  
 Se utiliza para establecer las propiedades de un proveedor.  
  
## Clase de marcador  
 [CBookmark](../../data/oledb/cbookmark-class.md)  
 Utilizado como índice para tener acceso a los datos de un conjunto de filas.  
  
## Tipo de error  
 [CDBErrorInfo](../../data/oledb/cdberrorinfo-class.md)  
 Se utiliza para recuperar la información de error de OLE DB.  
  
## Vea también  
 [Referencia de plantillas de proveedores OLE DB](../../data/oledb/ole-db-provider-templates-reference.md)   
 [plantillas OLE DB](../../data/oledb/ole-db-templates.md)