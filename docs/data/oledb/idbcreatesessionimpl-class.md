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
ms.openlocfilehash: cff1ca374c9489cb9c5df0dad153c4bf7a4cbc9e
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 03/24/2020
ms.locfileid: "80210787"
---
# <a name="idbcreatesessionimpl-class"></a>IDBCreateSessionImpl (Clase)

Proporciona una implementación para la interfaz [IDBCreateSession](/previous-versions/windows/desktop/ms724076(v=vs.85)) .

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
Objeto de sesión.

## <a name="requirements"></a>Requisitos

**Encabezado:** atldb.h

## <a name="members"></a>Members

### <a name="interface-methods"></a>Métodos de interfaz

|||
|-|-|
|[CreateSession](#createsession)|Crea una nueva sesión a partir del objeto de origen de datos y devuelve la interfaz solicitada en la sesión recién creada.|

## <a name="remarks"></a>Observaciones

Interfaz obligatoria en los objetos de origen de datos.

## <a name="idbcreatesessionimplcreatesession"></a><a name="createsession"></a>Idbcreatesessionimpl (:: CreateSession

Crea una nueva sesión a partir del objeto de origen de datos y devuelve la interfaz solicitada en la sesión recién creada.

### <a name="syntax"></a>Sintaxis

```cpp
STDMETHOD(CreateSession)(IUnknown * pUnkOuter,
   REFIID riid,
   IUnknown ** ppDBSession);
```

#### <a name="parameters"></a>Parámetros

Vea [IDBCreateSession:: createSession](/previous-versions/windows/desktop/ms714942(v=vs.85)) en la *Referencia del programador de OLE DB*.

## <a name="see-also"></a>Consulte también

[Plantillas de proveedores OLE DB](../../data/oledb/ole-db-provider-templates-cpp.md)<br/>
[Arquitectura de plantillas de proveedores OLE DB](../../data/oledb/ole-db-provider-template-architecture.md)
