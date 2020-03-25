---
title: Descriptores de acceso y conjuntos de filas
ms.date: 11/19/2018
helpviewer_keywords:
- accessors [C++]
- OLE DB consumer templates, rowset support
- OLE DB consumer templates, accessors
- rowsets [C++], accessing
- bulk rowsets
- CAccessorRowset class, accessor types
- single rowsets
- CArrayRowset class, accessors
- CBulkRowset class, accessors
- array rowsets
- CAccessorBase class
- CRowset class, accessors and rowsets
- accessors [C++], rowsets
- rowsets [C++], supported types
ms.assetid: edc9c8b3-1a2d-4c2d-869f-7e058c631042
ms.openlocfilehash: 45180b3ac2647c9f4f5d25a1322794552bd79004
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 03/24/2020
ms.locfileid: "80212386"
---
# <a name="accessors-and-rowsets"></a>Descriptores de acceso y conjuntos de filas

Para establecer y recuperar datos, las plantillas de OLE DB usan un descriptor de acceso y un conjunto de filas a través de la clase [CAccessorRowset](../../data/oledb/caccessorrowset-class.md) . Esta clase puede controlar varios descriptores de acceso de tipos diferentes.

## <a name="accessor-types"></a>Tipos descriptores de acceso

Todos los descriptores de acceso derivan de [CAccessorBase](../../data/oledb/caccessorbase-class.md). `CAccessorBase` proporciona enlaces de parámetros y columnas.

En la ilustración siguiente se muestran los tipos de descriptor de acceso.

![Tipos descriptores de acceso](../../data/oledb/media/vcaccessortypes.gif "Tipos de descriptores de acceso")<br/>
Clases accessor

- [CAccessor](../../data/oledb/caccessor-class.md) Use este descriptor de acceso cuando Conozca la estructura del origen de base de datos en tiempo de diseño. `CAccessor` enlaza estáticamente un registro de base de datos, que contiene el búfer, al origen de datos.

- [CDynamicAccessor](../../data/oledb/cdynamicaccessor-class.md) Use este descriptor de acceso si no conoce la estructura de la base de datos en tiempo de diseño. `CDynamicAccessor` llama `IColumnsInfo::GetColumnInfo` para obtener la información de la columna de base de datos. Crea y administra un descriptor de acceso y el búfer.

- [CDynamicParameterAccessor](../../data/oledb/cdynamicparameteraccessor-class.md) Use este descriptor de acceso para controlar tipos de comando desconocidos. Cuando se preparan los comandos, `CDynamicParameterAccessor` puede obtener información de parámetros de la interfaz `ICommandWithParameters`, si el proveedor admite `ICommandWithParameters`.

- [CDynamicStringAccessor](../../data/oledb/cdynamicstringaccessor-class.md), [cdynamicstringaccessora (](../../data/oledb/cdynamicstringaccessora-class.md)y [CDynamicStringAccessorW](../../data/oledb/cdynamicstringaccessorw-class.md) usan estas clases cuando no se conoce el esquema de la base de datos. `CDynamicStringAccessorA` recupera datos como cadenas ANSI; `CDynamicStringAccessorW` recupera datos como cadenas Unicode.

- [CManualAccessor](../../data/oledb/cmanualaccessor-class.md) Con esta clase, puede usar cualquier tipo de datos que desee si el proveedor puede convertir el tipo. Controla las columnas de resultados y los parámetros de comando.

En la tabla siguiente se resume la compatibilidad de con los tipos de descriptor de acceso de la plantilla OLE DB.

|Tipo descriptor de acceso|Dinámica|Controla los parámetros|Buffer|Varios descriptores de acceso|
|-------------------|-------------|--------------------|------------|------------------------|
|`CAccessor`|No|Sí|Usuario|Sí|
|`CDynamicAccessor`|Sí|No|Plantillas OLE DB|No|
|`CDynamicParameterAccessor`|Sí|Sí|Plantillas OLE DB|No|
|`CDynamicStringAccessor[A,W]`|Sí|No|Plantillas OLE DB|No|
|`CManualAccessor`|Sí|Sí|Usuario|Sí|

## <a name="rowset-types"></a>Tipos de conjuntos de filas

Las plantillas de OLE DB admiten tres tipos de conjuntos de filas (vea la ilustración anterior): conjuntos de filas individuales (implementados por [CRowset](../../data/oledb/crowset-class.md)), conjuntos de filas masivos (implementados por [CBulkRowset](../../data/oledb/cbulkrowset-class.md)) y conjuntos de filas de matriz (implementados por [CArrayRowset](../../data/oledb/carrayrowset-class.md)). Los conjuntos de filas individuales capturan un identificador de fila único cuando se llama a `MoveNext`. Los conjuntos de filas masivos pueden capturar varios identificadores de fila. Los conjuntos de filas de matriz son conjuntos de filas a los que se puede tener acceso mediante la sintaxis de la matriz.

En la ilustración siguiente se muestran los tipos de conjunto de filas.

![Gráfico RowsetType](../../data/oledb/media/vcrowsettypes.gif "Gráfico de RowsetType")<br/>
Clases de conjunto de filas

Los [conjuntos de filas de esquema](../../data/oledb/obtaining-metadata-with-schema-rowsets.md) no tienen acceso a los datos del almacén de datos, sino que obtienen acceso a información sobre el almacén de datos, denominados metadatos. Los conjuntos de filas de esquema se utilizan normalmente en situaciones en las que no se conoce la estructura de la base de datos en tiempo de compilación y se deben obtener en tiempo de ejecución.

## <a name="see-also"></a>Consulte también

[Plantillas de consumidor OLE DB](../../data/oledb/ole-db-consumer-templates-cpp.md)
