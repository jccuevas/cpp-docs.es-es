---
title: IDBCreateSessionImpl (Clase)
ms.date: 11/04/2016
f1_keywords:
- IDBCreateSessionImpl
- ATL.IDBCreateSessionImpl
- ATL::IDBCreateSessionImpl
- IDBCreateSessionImpl::CreateSession
- IDBCreateSessionImpl.CreateSession
- CreateSession
helpviewer_keywords:
- IDBCreateSessionImpl class
- CreateSession method
ms.assetid: 48c02c5c-8362-45ac-af8e-bb119cf8c5c7
ms.openlocfilehash: 0b15cd45ca63847e5489091226feba81a4040985
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/31/2018
ms.locfileid: "50459428"
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