---
title: CDynamicStringAccessorA (clase) | Documentos de Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-windows
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- CDynamicStringAccessorA
dev_langs:
- C++
helpviewer_keywords:
- CDynamicStringAccessorA class
ms.assetid: ed0d9821-a655-41f1-a902-43c3042ac49c
caps.latest.revision: 
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
- data-storage
ms.openlocfilehash: b7dfd677d0a0090946cfa7d6a19ac36e1da57a0f
ms.sourcegitcommit: d51ed21ab2b434535f5c1d553b22e432073e1478
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 02/23/2018
---
# <a name="cdynamicstringaccessora-class"></a>CDynamicStringAccessorA (Clase)
Permite obtener acceso a un origen de datos cuando no tiene ningún conocimiento del esquema de base de datos (estructura subyacente).  
  
## <a name="syntax"></a>Sintaxis

```cpp
typedef CDynamicStringAccessorT<CHAR, DBTYPE_STR> CDynamicStringAccessorA;  
```  
  
## <a name="remarks"></a>Comentarios  
 Solicitan que el proveedor recupere todos los datos que se tiene acceso desde el almacén de datos como datos de cadena, pero `CDynamicStringAccessor` datos de cadena de las solicitudes de ANSI.  
  
 `CDynamicStringAccessorA` hereda **GetString** y `SetString` de `CDynamicStringAccessor`. Cuando se usan estos métodos en un `CDynamicStringAccessorA` objeto, ***BaseType*** es **CHAR**.  
  
## <a name="requirements"></a>Requisitos  
 **Encabezado**: atldbcli.h  
  
## <a name="see-also"></a>Vea también  
 [Plantillas de consumidor OLE DB](../../data/oledb/ole-db-consumer-templates-cpp.md)   
 [Referencia de plantillas de consumidor OLE DB](../../data/oledb/ole-db-consumer-templates-reference.md)   
 [CAccessor (clase)](../../data/oledb/caccessor-class.md)   
 [CDynamicParameterAccessor (clase)](../../data/oledb/cdynamicparameteraccessor-class.md)   
 [CManualAccessor (clase)](../../data/oledb/cmanualaccessor-class.md)   
 [CDynamicAccessor (clase)](../../data/oledb/cdynamicaccessor-class.md)   
 [CDynamicStringAccessor (Clase)](../../data/oledb/cdynamicstringaccessor-class.md)