---
title: IDBCreateSessionImpl (clase) | Documentos de Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- IDBCreateSessionImpl
- ATL.IDBCreateSessionImpl
- ATL::IDBCreateSessionImpl
dev_langs:
- C++
helpviewer_keywords:
- IDBCreateSessionImpl class
ms.assetid: 48c02c5c-8362-45ac-af8e-bb119cf8c5c7
caps.latest.revision: 
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
- data-storage
ms.openlocfilehash: 07504eeaa9f46e4618b08be4a572d62a9ecdecef
ms.sourcegitcommit: 6002df0ac79bde5d5cab7bbeb9d8e0ef9920da4a
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 02/14/2018
---
# <a name="idbcreatesessionimpl-class"></a>IDBCreateSessionImpl (Clase)
Proporciona una implementación para el [IDBCreateSession](https://msdn.microsoft.com/en-us/library/ms724076.aspx) interfaz.  
  
## <a name="syntax"></a>Sintaxis

```cpp
template <class T, class SessionClass>  
class ATL_NO_VTABLE IDBCreateSessionImpl   
   : public IDBCreateSession  
```  
  
#### <a name="parameters"></a>Parámetros  
 `T`  
 LA CLASE, DERIVADA DE  
  
 `SessionClass`  
 El objeto de sesión.  
  
## <a name="members"></a>Miembros  
  
### <a name="interface-methods"></a>Métodos de interfaz  
  
|||  
|-|-|  
|[CreateSession](../../data/oledb/idbcreatesessionimpl-createsession.md)|Crea una nueva sesión desde el objeto de origen de datos y devuelve la interfaz solicitada en la sesión recién creada.|  
  
## <a name="remarks"></a>Comentarios  
 Una interfaz obligatoria en los objetos de origen de datos.  
  
## <a name="requirements"></a>Requisitos  
 **Encabezado:** atldb.h  
  
## <a name="see-also"></a>Vea también  
 [Plantillas del proveedor OLE DB](../../data/oledb/ole-db-provider-templates-cpp.md)   
 [Arquitectura de plantillas de proveedores OLE DB](../../data/oledb/ole-db-provider-template-architecture.md)