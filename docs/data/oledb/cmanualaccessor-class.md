---
title: CManualAccessor (clase) | Documentos de Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-data
ms.topic: reference
f1_keywords:
- ATL::CManualAccessor
- ATL.CManualAccessor
- CManualAccessor
dev_langs:
- C++
helpviewer_keywords:
- CManualAccessor class
ms.assetid: a0088074-7135-465c-b228-69097a50b8cc
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- data-storage
ms.openlocfilehash: 7b8efc46971b1aa72f8c5e572aa540bfed250d2b
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 05/04/2018
---
# <a name="cmanualaccessor-class"></a>CManualAccessor (Clase)
Representa un tipo de descriptor de acceso que se ha diseñado para uso avanzado.  
  
## <a name="syntax"></a>Sintaxis

```cpp
class CManualAccessor : public CAccessorBase  
```  
  
## <a name="members"></a>Miembros  
  
### <a name="methods"></a>Métodos  
  
|||  
|-|-|  
|[AddBindEntry](../../data/oledb/cmanualaccessor-addbindentry.md)|Agrega una entrada de enlace a las columnas de salida.|  
|[AddParameterEntry](../../data/oledb/cmanualaccessor-addparameterentry.md)|Agrega una entrada de parámetro para el descriptor de acceso de parámetro.|  
|[CreateAccessor](../../data/oledb/cmanualaccessor-createaccessor.md)|Asigna memoria a estructuras de enlace de la columna e inicializa a los miembros de datos de columna.|  
|[CreateParameterAccessor](../../data/oledb/cmanualaccessor-createparameteraccessor.md)|Asigna memoria para el parámetro de estructuras de enlace e inicializa a los miembros de datos de parámetro.|  
  
## <a name="remarks"></a>Comentarios  
 Usar `CManualAccessor`, puede especificar el parámetro y el enlace de columna de salida por llamadas a funciones de tiempo de ejecución.  
  
## <a name="requirements"></a>Requisitos  
 **Encabezado:** atldbcli.h  
  
## <a name="see-also"></a>Vea también  
 [DBViewer](../../visual-cpp-samples.md)   
 [Plantillas de consumidor OLE DB](../../data/oledb/ole-db-consumer-templates-cpp.md)   
 [Referencia de plantillas de consumidor OLE DB](../../data/oledb/ole-db-consumer-templates-reference.md)   
 [CAccessor (clase)](../../data/oledb/caccessor-class.md)   
 [CDynamicAccessor (clase)](../../data/oledb/cdynamicaccessor-class.md)   
 [CDynamicParameterAccessor (Clase)](../../data/oledb/cdynamicparameteraccessor-class.md)