---
title: CManualAccessor (clase) | Documentos de Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-windows
ms.tgt_pltfrm: 
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
caps.latest.revision: 
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
- data-storage
ms.openlocfilehash: ecb9f31c862f62ddc2422f201aa824a959e961a0
ms.sourcegitcommit: d51ed21ab2b434535f5c1d553b22e432073e1478
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 02/23/2018
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