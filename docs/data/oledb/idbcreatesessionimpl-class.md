---
title: IDBCreateSessionImpl (clase) | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-data
ms.topic: reference
f1_keywords:
- IDBCreateSessionImpl
- ATL.IDBCreateSessionImpl
- ATL::IDBCreateSessionImpl
- IDBCreateSessionImpl::CreateSession
- IDBCreateSessionImpl.CreateSession
- CreateSession
dev_langs:
- C++
helpviewer_keywords:
- IDBCreateSessionImpl class
- CreateSession method
ms.assetid: 48c02c5c-8362-45ac-af8e-bb119cf8c5c7
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- data-storage
ms.openlocfilehash: 7f148176b8d5d0c85f3e899cfd117bbb381794b0
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/18/2018
ms.locfileid: "46047400"
---
# <a name="idbcreatesessionimpl-class"></a>IDBCreateSessionImpl (Clase)

Proporciona una implementación para el [IDBCreateSession](/previous-versions/windows/desktop/ms724076\(v=vs.85\)) interfaz.  
  
## <a name="syntax"></a>Sintaxis

```cpp
template <class T, class SessionClass>  
class ATL_NO_VTABLE IDBCreateSessionImpl   
   : public IDBCreateSession  
```  
  
### <a name="parameters"></a>Parámetros  

*T*<br/>
LA CLASE, DERIVADA DE  
  
*SessionClass*<br/>
El objeto de sesión.  

## <a name="requirements"></a>Requisitos  

**Encabezado:** atldb.h 
  
## <a name="members"></a>Miembros  
  
### <a name="interface-methods"></a>Métodos de interfaz  
  
|||  
|-|-|  
|[CreateSession](#createsession)|Crea una nueva sesión desde el objeto de origen de datos y devuelve la interfaz solicitada en la sesión recién creada.|  
  
## <a name="remarks"></a>Comentarios  

Una interfaz obligatoria en los objetos de origen de datos.  

## <a name="createsession"></a> Idbcreatesessionimpl:: CreateSession

Crea una nueva sesión desde el objeto de origen de datos y devuelve la interfaz solicitada en la sesión recién creada.  
  
### <a name="syntax"></a>Sintaxis  
  
```cpp
STDMETHOD(CreateSession)(IUnknown * pUnkOuter,   
   REFIID riid,   
   IUnknown ** ppDBSession);  
```  
  
#### <a name="parameters"></a>Parámetros  

Consulte [IDBCreateSession](/previous-versions/windows/desktop/ms714942\(v=vs.85\)) en el *referencia del programador OLE DB*.   
  
## <a name="see-also"></a>Vea también  

[Plantillas de proveedores OLE DB](../../data/oledb/ole-db-provider-templates-cpp.md)<br/>
[Arquitectura de plantillas de proveedores OLE DB](../../data/oledb/ole-db-provider-template-architecture.md)