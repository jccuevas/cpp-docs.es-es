---
title: IDBCreateSessionImpl (clase) | Documentos de Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-windows
ms.tgt_pltfrm: 
ms.topic: reference
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
ms.openlocfilehash: 4cd7abcc35a7e3bff95c0945069689750c4d55ac
ms.sourcegitcommit: d51ed21ab2b434535f5c1d553b22e432073e1478
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 02/23/2018
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