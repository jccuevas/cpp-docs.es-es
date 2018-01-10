---
title: CXMLAccessor (clase) | Documentos de Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- ATL::CXMLAccessor
- CXMLAccessor
- ATL.CXMLAccessor
dev_langs: C++
helpviewer_keywords: CXMLAccessor class
ms.assetid: c88c082c-ec2f-4351-8947-a330b15e448a
caps.latest.revision: "12"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
- data-storage
ms.openlocfilehash: 96620f287522168cd7b6b78d43163e8c4bb64217
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 12/21/2017
---
# <a name="cxmlaccessor-class"></a>CXMLAccessor (Clase)
Permite obtener acceso a orígenes de datos como datos de cadena cuando no tiene ningún conocimiento del esquema del almacén de datos (estructura subyacente).  
  
## <a name="syntax"></a>Sintaxis  
  
```  
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