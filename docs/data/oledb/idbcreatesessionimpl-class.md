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
ms.openlocfilehash: 2e4427eede8efcd492e90597efe9488a89e6d4de
ms.sourcegitcommit: 3a141cf07b5411d5f1fdf6cf67c4ce928cf389c3
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/11/2018
ms.locfileid: "49082376"
---
# <a name="idbcreatesessionimpl-class"></a>IDBCreateSessionImpl (Clase)

Proporciona una implementación para el [IDBCreateSession](/previous-versions/windows/desktop/ms724076) interfaz.  
  
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

Consulte [IDBCreateSession](/previous-versions/windows/desktop/ms714942) en el *referencia del programador OLE DB*.   
  
## <a name="see-also"></a>Vea también  

[Plantillas de proveedores OLE DB](../../data/oledb/ole-db-provider-templates-cpp.md)<br/>
[Arquitectura de plantillas de proveedores OLE DB](../../data/oledb/ole-db-provider-template-architecture.md)