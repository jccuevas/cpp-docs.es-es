---
title: CDynamicStringAccessorW (clase) | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-data
ms.topic: reference
f1_keywords:
- CDynamicStringAccessorW
dev_langs:
- C++
helpviewer_keywords:
- CDynamicStringAccessorW class
ms.assetid: 9b7fd5cc-3a9b-4b57-b907-f1e35de2c98f
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- data-storage
ms.openlocfilehash: fb3e12853d384f433674331342541b7e69241d4a
ms.sourcegitcommit: 889a75be1232817150be1e0e8d4d7f48f5993af2
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 07/30/2018
ms.locfileid: "39340493"
---
# <a name="cdynamicstringaccessorw-class"></a>CDynamicStringAccessorW (Clase)
Permite obtener acceso a un origen de datos cuando no tiene conocimiento del esquema de base de datos (estructura subyacente).  
  
## <a name="syntax"></a>Sintaxis

```cpp
typedef CDynamicStringAccessorT<WCHAR, DBTYPE_WSTR> CDynamicStringAccessorW;  
```  
  
## <a name="remarks"></a>Comentarios  
 Solicitan que el proveedor recupere todos los datos que se obtiene acceso desde el almacén de datos como datos de cadena, pero `CDynamicStringAccessor` solicita datos de cadena Unicode.  
  
 `CDynamicStringAccessorW` hereda `GetString` y `SetString` desde `CDynamicStringAccessor`. Cuando se usan estos métodos en un `CDynamicStringAccessorW` objeto, ***BaseType*** es **WCHAR**.  
  
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