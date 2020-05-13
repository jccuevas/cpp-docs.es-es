---
title: Referencia de plantillas de consumidor OLE DB
ms.date: 11/04/2016
helpviewer_keywords:
- OLE DB consumer templates, classes
ms.assetid: cfc7f698-1a0e-4a09-a4d3-ccb99e6654fe
ms.openlocfilehash: 13805ab1dc2c2b4792fd05c9140006c610b42f75
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 03/24/2020
ms.locfileid: "80210111"
---
# <a name="ole-db-consumer-templates-reference"></a>Referencia de plantillas de consumidor OLE DB

Las plantillas de consumidor de OLE DB contienen las siguientes clases. El material de referencia también incluye temas sobre las [macros para las plantillas de consumidor OLE DB](../../data/oledb/macros-and-global-functions-for-ole-db-consumer-templates.md).

## <a name="session-classes"></a>Clases de sesión

[CDataConnection](../../data/oledb/cdataconnection-class.md)<br/>
Administra la conexión con el origen de datos. Esta es una clase útil para crear clientes, ya que encapsula los objetos necesarios (origen de datos y sesión) y parte del trabajo que debe realizar al conectarse a un origen de datos.

[CDataSource](../../data/oledb/cdatasource-class.md)<br/>
Corresponde a un objeto de origen de datos OLE DB, que representa una conexión a través de un proveedor a un origen de datos. Una o varias sesiones de base de datos, cada una representada por un objeto `CSession`, pueden tener lugar en una sola conexión.

[CEnumerator](../../data/oledb/cenumerator-class.md)<br/>
Corresponde a un objeto de enumerador de OLE DB, que recupera información del conjunto de filas sobre los orígenes de datos disponibles.

[CEnumeratorAccessor](../../data/oledb/cenumeratoraccessor-class.md)<br/>
Lo utiliza `CEnumerator` para tener acceso a los datos del conjunto de filas del enumerador. Este conjunto de filas consta de los orígenes de datos y los enumeradores visibles en el enumerador actual.

[CSession](../../data/oledb/csession-class.md)<br/>
Representa una única sesión de acceso a bases de datos. Se pueden asociar una o varias sesiones a cada `CDataSource` objeto.

## <a name="accessor-classes"></a>Clases accessor

[CAccessor](../../data/oledb/caccessor-class.md)<br/>
Se utiliza para los registros enlazados estáticamente a un origen de datos. Utilice esta clase de descriptor de acceso cuando Conozca la estructura del origen de datos.

[CAccessorBase](../../data/oledb/caccessorbase-class.md)<br/>
Clase base para todas las clases de descriptor de acceso.

[CDynamicAccessor](../../data/oledb/cdynamicaccessor-class.md)<br/>
Un descriptor de acceso que se puede crear en tiempo de ejecución, basado en la información de columna del conjunto de filas. Utilice esta clase para recuperar datos si no conoce la estructura del origen de datos.

[CDynamicParameterAccessor](../../data/oledb/cdynamicparameteraccessor-class.md)<br/>
Un descriptor de acceso que se puede usar cuando se desconocen los tipos de comando. Obtiene la información de parámetros llamando a la interfaz `ICommandWithParameters`, si el proveedor es compatible con la interfaz.

[CDynamicStringAccessor (](../../data/oledb/cdynamicstringaccessor-class.md)<br/>
Permite tener acceso a un origen de datos cuando no se tiene conocimiento de la estructura subyacente de la base de datos.

[Cdynamicstringaccessora (](../../data/oledb/cdynamicstringaccessora-class.md)<br/>
Similar a `CDynamicStringAccessor` excepto en que esta clase solicita datos a los que se tiene acceso desde el almacén de datos como datos de cadena ANSI.

[CDynamicStringAccessorW](../../data/oledb/cdynamicstringaccessorw-class.md)<br/>
Similar a `CDynamicStringAccessor`, salvo que esta clase solicita datos a los que se tiene acceso desde el almacén de datos como datos de cadena Unicode.

[CManualAccessor](../../data/oledb/cmanualaccessor-class.md)<br/>
Un descriptor de acceso con métodos para controlar las columnas y los parámetros de comando. Con esta clase, puede usar cualquier tipo de datos siempre que el proveedor pueda convertir el tipo.

[Cnoaccessor (](../../data/oledb/cnoaccessor-class.md)<br/>
Se puede utilizar como argumento de plantilla cuando no se desea que la clase admita parámetros o columnas de salida.

[CXMLAccessor](../../data/oledb/cxmlaccessor-class.md)<br/>
Similar a `CDynamicStringAccessor` excepto en que esta clase convierte todos los datos a los que se tiene acceso desde el almacén de datos como datos con formato XML.

## <a name="rowset-classes"></a>Clases de conjunto de filas

[Caccessorrowset (](../../data/oledb/caccessorrowset-class.md)<br/>
Encapsula un conjunto de filas y sus descriptores de acceso asociados.

[CArrayRowset](../../data/oledb/carrayrowset-class.md)<br/>
Se utiliza para tener acceso a los elementos de un conjunto de filas mediante la sintaxis de la matriz.

[CBulkRowset](../../data/oledb/cbulkrowset-class.md)<br/>
Se usa para capturar y manipular filas de forma masiva mediante la recuperación de varios identificadores de fila con una sola llamada.

[Cnorowset (](../../data/oledb/cnorowset-class.md)<br/>
Se puede utilizar como argumento de plantilla si el comando no devuelve un conjunto de filas.

[CRestrictions](../../data/oledb/crestrictions-class.md)<br/>
Se utiliza para especificar las restricciones de los conjuntos de filas de esquema.

[CRowset](../../data/oledb/crowset-class.md)<br/>
Se utiliza para manipular, establecer y recuperar los datos del conjunto de filas.

[CStreamRowset (](../../data/oledb/cstreamrowset-class.md)<br/>
Devuelve un objeto `ISequentialStream` en lugar de un conjunto de filas; a continuación, use el método `Read` para recuperar los datos en formato XML. (SQL Server 2000 hace el formato; tenga en cuenta que esta característica solo funciona con SQL Server 2000).

[Irowsetnotifyimpl (](../../data/oledb/irowsetnotifyimpl-class.md)<br/>
Proporciona una implementación ficticia de `IRowsetNotify`, con funciones vacías para los métodos de `IRowsetNotify` `OnFieldChange`, `OnRowChange`y `OnRowsetChange`.

[Clases de conjunto de filas de esquema y clases typedef](../../data/oledb/schema-rowset-classes-and-typedef-classes.md)

Las plantillas OLE DB proporcionan un conjunto de clases que corresponden a los conjuntos de filas de esquema OLE DB.

## <a name="command-classes"></a>Clases de comandos

[CCommand](../../data/oledb/ccommand-class.md)<br/>
Se usa para establecer y ejecutar un comando de OLE DB basado en parámetros. Para abrir simplemente un conjunto de filas simple, use `CTable` en su lugar.

[Cmultipleresults (](../../data/oledb/cmultipleresults-class.md)<br/>
Se usa como un argumento de plantilla para la plantilla de `CCommand` cuando se desea que el comando controle varios conjuntos de resultados.

[Cnoaccessor (](../../data/oledb/cnoaccessor-class.md)<br/>
Se utiliza como argumento de plantilla para las clases de plantilla, como `CCommand` y `CTable`, que toman un argumento de clase de descriptor de acceso. Use `CNoAccessor` si no desea que la clase admita parámetros o columnas de salida.

[Cnomultipleresults (](../../data/oledb/cnomultipleresults-class.md)<br/>
Se utiliza como argumento de plantilla para la plantilla de `CCommand` cuando se desea que el comando controle un conjunto de filas único. `CNoMultipleResults` es el valor predeterminado para el argumento de plantilla.

[Cnorowset (](../../data/oledb/cnorowset-class.md)<br/>
Se utiliza como argumento de plantilla para `CCommand` o `CTable` si el comando o la tabla no devuelve un conjunto de filas.

[CTable](../../data/oledb/ctable-class.md)<br/>
Se utiliza para tener acceso a un conjunto de filas simple sin parámetros.

## <a name="property-classes"></a>Clases de propiedad

[CDBPropIDSet](../../data/oledb/cdbpropidset-class.md)<br/>
Se usa para pasar una matriz de identificadores de propiedad para los que el consumidor desea información de propiedad. Las propiedades pertenecen a un conjunto de propiedades.

[CDBPropSet](../../data/oledb/cdbpropset-class.md)<br/>
Se utiliza para establecer las propiedades de un proveedor.

## <a name="bookmark-class"></a>Bookmark (clase)

[CBookmark](../../data/oledb/cbookmark-class.md)<br/>
Se utiliza como índice para tener acceso a los datos de un conjunto de filas.

## <a name="error-class"></a>Error (clase)

[CDBErrorInfo](../../data/oledb/cdberrorinfo-class.md)<br/>
Se utiliza para recuperar la información de error de OLE DB.

## <a name="see-also"></a>Consulte también

[Referencia de plantillas de proveedores OLE DB](../../data/oledb/ole-db-provider-templates-reference.md)<br/>
[Plantillas OLE DB](../../data/oledb/ole-db-templates.md)
