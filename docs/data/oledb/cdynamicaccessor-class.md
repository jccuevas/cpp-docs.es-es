---
title: CDynamicAccessor (clase) | Documentos de Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-data
ms.topic: reference
f1_keywords:
- ATL.CDynamicAccessor
- ATL::CDynamicAccessor
- CDynamicAccessor
dev_langs:
- C++
helpviewer_keywords:
- CDynamicAccessor class
ms.assetid: 374b13b7-1f09-457d-9e6b-df260ff4d178
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- data-storage
ms.openlocfilehash: 2a4006afa9ebdfcf95a01103d1fd97643a6b749f
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 05/04/2018
ms.locfileid: "33098308"
---
# <a name="cdynamicaccessor-class"></a>CDynamicAccessor (Clase)
Permite obtener acceso a un origen de datos cuando no tiene ningún conocimiento del esquema de base de datos (estructura subyacente de la base de datos).  
  
## <a name="syntax"></a>Sintaxis

```cpp
class CDynamicAccessor : public CAccessorBase  
```  
  
## <a name="members"></a>Miembros  
  
### <a name="methods"></a>Métodos  
  
|||  
|-|-|  
|[AddBindEntry](../../data/oledb/cdynamicaccessor-addbindentry.md)|Agrega una entrada de enlace a las columnas de salida al reemplazar el descriptor de acceso de forma predeterminada.|  
|[CDynamicAccessor](../../data/oledb/cdynamicaccessor-class.md)|Crea e inicializa la `CDynamicAccessor` objeto.|  
|[Cerrar](../../data/oledb/cdynamicaccessor-close.md)|Desenlaza todas las columnas, libera la memoria asignada y libera el [IAccessor](https://msdn.microsoft.com/en-us/library/ms719672.aspx) puntero de interfaz en la clase.|  
|[GetBookmark](../../data/oledb/cdynamicaccessor-getbookmark.md)|Recupera el marcador de la fila actual.|  
|[GetBlobHandling](../../data/oledb/cdynamicaccessor-getblobhandling.md)|Recupera el BLOB de control de valor de la fila actual.|  
|[GetBlobSizeLimit](../../data/oledb/cdynamicaccessor-getblobsizelimit.md)|Recupera el tamaño máximo de BLOB en bytes.|  
|[GetColumnCount](../../data/oledb/cdynamicaccessor-getcolumncount.md)|Recupera el número de columnas del conjunto de filas.|  
|[GetColumnFlags](../../data/oledb/cdynamicaccessor-getcolumnflags.md)|Recupera las características de la columna.|  
|[GetColumnInfo](../../data/oledb/cdynamicaccessor-getcolumninfo.md)|Recupera los metadatos de columna.|  
|[getColumnName](../../data/oledb/cdynamicaccessor-getcolumnname.md)|Recupera el nombre de una columna especificada.|  
|[getColumnType](../../data/oledb/cdynamicaccessor-getcolumntype.md)|Recupera el tipo de datos de una columna especificada.|  
|[GetLength](../../data/oledb/cdynamicaccessor-getlength.md)|Recupera la longitud máxima posible de una columna en bytes.|  
|[GetOrdinal](../../data/oledb/cdynamicaccessor-getordinal.md)|Recupera el índice de columna dado un nombre de columna.|  
|[GetStatus](../../data/oledb/cdynamicaccessor-getstatus.md)|Recupera el estado de una columna especificada.|  
|[GetValue](../../data/oledb/cdynamicaccessor-getvalue.md)|Recupera los datos desde el búfer.|  
|[SetBlobHandling](../../data/oledb/cdynamicaccessor-setblobhandling.md)|Establece el BLOB de control de valor de la fila actual.|  
|[SetBlobSizeLimit](../../data/oledb/cdynamicaccessor-setblobsizelimit.md)|Establece el tamaño máximo de BLOB en bytes.|  
|[SetLength](../../data/oledb/cdynamicaccessor-setlength.md)|Establece la longitud de la columna en bytes.|  
|[SetStatus](../../data/oledb/cdynamicaccessor-setstatus.md)|Establece el estado de una columna especificada.|  
|[SetValue](../../data/oledb/cdynamicaccessor-setvalue.md)|Almacena los datos en el búfer.|  
  
## <a name="remarks"></a>Comentarios  
 Use `CDynamicAccessor` métodos para obtener información de columna como nombres de columna, número de columnas, tipo de datos y así sucesivamente. A continuación, utilizar esta información de columna para crear un descriptor de acceso dinámicamente en tiempo de ejecución.  
  
 La información de columna se almacena en un búfer creado y administrado por esta clase. Obtener datos desde el búfer mediante [GetValue](../../data/oledb/cdynamicaccessor-getvalue.md).  
  
 Para obtener una descripción y ejemplos del uso de las clases de descriptor de acceso dinámico, vea [utilizando descriptores de acceso dinámicos](../../data/oledb/using-dynamic-accessors.md).  
  
## <a name="requirements"></a>Requisitos  
 **Encabezado**: atldbcli.h  
  
## <a name="see-also"></a>Vea también  
 [Plantillas de consumidor OLE DB](../../data/oledb/ole-db-consumer-templates-cpp.md)   
 [Referencia de plantillas de consumidor OLE DB](../../data/oledb/ole-db-consumer-templates-reference.md)   
 [CAccessor (clase)](../../data/oledb/caccessor-class.md)   
 [CDynamicParameterAccessor (clase)](../../data/oledb/cdynamicparameteraccessor-class.md)   
 [CManualAccessor (Clase)](../../data/oledb/cmanualaccessor-class.md)