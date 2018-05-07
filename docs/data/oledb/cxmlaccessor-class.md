---
title: CXMLAccessor (clase) | Documentos de Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-data
ms.topic: reference
f1_keywords:
- ATL::CXMLAccessor
- CXMLAccessor
- ATL.CXMLAccessor
dev_langs:
- C++
helpviewer_keywords:
- CXMLAccessor class
ms.assetid: c88c082c-ec2f-4351-8947-a330b15e448a
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- data-storage
ms.openlocfilehash: 916e9dbe4e142192e4e716f57f97d5bd6865c709
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 05/04/2018
---
# <a name="cxmlaccessor-class"></a>CXMLAccessor (Clase)
Permite obtener acceso a orígenes de datos como datos de cadena cuando no tiene ningún conocimiento del esquema del almacén de datos (estructura subyacente).  
  
## <a name="syntax"></a>Sintaxis

```cpp
class CXMLAccessor : public CDynamicStringAccessorW  
```  
  
## <a name="members"></a>Miembros  
  
### <a name="methods"></a>Métodos  
  
|||  
|-|-|  
|[GetXMLColumnData](../../data/oledb/cxmlaccessor-getxmlcolumndata.md)|Recupera la información de columna.|  
|[GetXMLRowData](../../data/oledb/cxmlaccessor-getxmlrowdata.md)|Recupera el contenido completo de una tabla por filas.|  
  
## <a name="remarks"></a>Comentarios  
 Sin embargo, `CXMLAccessor` difiere de `CDynamicStringAccessorW` en que convierte todos los datos que se tiene acceso desde el almacén de datos como datos (etiquetados) en formato XML. Esto es especialmente útil para la salida de páginas Web compatible con XML. Los nombres de etiqueta XML coincidirá con nombres de columna del almacén de datos lo más fielmente posible.  
  
 Use `CDynamicAccessor` métodos para obtener información de columna. Utilice esta información de columna para crear un descriptor de acceso de forma dinámica en tiempo de ejecución.  
  
 La información de columna se almacena en un búfer creado y administrado por esta clase. Obtener información de columna con [GetXMLColumnData](../../data/oledb/cxmlaccessor-getxmlcolumndata.md) u obtener datos de las columnas por filas mediante [GetXMLRowData](../../data/oledb/cxmlaccessor-getxmlrowdata.md).  
  
## <a name="example"></a>Ejemplo  
 [!code-cpp[NVC_OLEDB_Consumer#14](../../data/oledb/codesnippet/cpp/cxmlaccessor-class_1.cpp)]  
  
## <a name="requirements"></a>Requisitos  
 **Encabezado**: atldbcli.h  
  
## <a name="see-also"></a>Vea también  
 [Plantillas de consumidor OLE DB](../../data/oledb/ole-db-consumer-templates-cpp.md)   
 [Referencia de plantillas de consumidor OLE DB](../../data/oledb/ole-db-consumer-templates-reference.md)   
 [CAccessor (clase)](../../data/oledb/caccessor-class.md)   
 [CDynamicAccessor (clase)](../../data/oledb/cdynamicaccessor-class.md)   
 [CDynamicParameterAccessor (clase)](../../data/oledb/cdynamicparameteraccessor-class.md)   
 [CDynamicStringAccessor (clase)](../../data/oledb/cdynamicstringaccessor-class.md)   
 [CDynamicStringAccessorA (clase)](../../data/oledb/cdynamicstringaccessora-class.md)   
 [CDynamicStringAccessorW (clase)](../../data/oledb/cdynamicstringaccessorw-class.md)   
 [CManualAccessor (Clase)](../../data/oledb/cmanualaccessor-class.md)