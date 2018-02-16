---
title: IOpenRowsetImpl (clase) | Documentos de Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- IOpenRowsetImpl
dev_langs:
- C++
helpviewer_keywords:
- IOpenRowsetImpl class
ms.assetid: d259cedc-1db4-41cf-bc9f-5030907ab486
caps.latest.revision: 
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
- data-storage
ms.openlocfilehash: aa59f1a4f8b599cc74cbe824815c65b60e7b6af1
ms.sourcegitcommit: 6002df0ac79bde5d5cab7bbeb9d8e0ef9920da4a
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 02/14/2018
---
# <a name="iopenrowsetimpl-class"></a>IOpenRowsetImpl (Clase)
Proporciona la implementación de la `IOpenRowset` interfaz.  
  
## <a name="syntax"></a>Sintaxis

```cpp
template <class SessionClass>  
class IOpenRowsetImpl : public IOpenRowset  
```  
  
#### <a name="parameters"></a>Parámetros  
 `SessionClass`  
 La clase derivada de `IOpenRowsetImpl`.  
  
## <a name="members"></a>Miembros  
  
### <a name="methods"></a>Métodos  
  
|||  
|-|-|  
|[CreateRowset](../../data/oledb/iopenrowsetimpl-createrowset.md)|Crea un objeto de conjunto de filas. No llama directamente al usuario.|  
|[OpenRowset](../../data/oledb/iopenrowsetimpl-openrowset.md)|Se abre y devuelve un conjunto de filas que incluye todas las filas de una única tabla base o índice. (No en ATLDB. H)|  
  
## <a name="remarks"></a>Comentarios  
 El [IOpenRowset](https://msdn.microsoft.com/en-us/library/ms716946.aspx) interfaz es obligatoria para un objeto de sesión. Se abre y devuelve un conjunto de filas que incluye todas las filas de una única tabla base o índice.  
  
## <a name="requirements"></a>Requisitos  
 **Encabezado:** atldb.h  
  
## <a name="see-also"></a>Vea también  
 [Plantillas del proveedor OLE DB](../../data/oledb/ole-db-provider-templates-cpp.md)   
 [Arquitectura de plantillas de proveedores OLE DB](../../data/oledb/ole-db-provider-template-architecture.md)