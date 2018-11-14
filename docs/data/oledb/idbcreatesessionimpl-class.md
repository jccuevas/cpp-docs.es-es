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
ms.openlocfilehash: ecc06bf5e3514ea87c86de17dbafd59b9da9f8b6
ms.sourcegitcommit: c40469825b6101baac87d43e5f4aed6df6b078f5
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 11/12/2018
ms.locfileid: "51556427"
---
# <a name="idbcreatesessionimpl-class"></a>IDBCreateSessionImpl (Clase)

Proporciona una implementación para el [IDBCreateSession](https://docs.microsoft.com/previous-versions/windows/desktop/ms724076(v=vs.85)) interfaz.

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

Consulte [IDBCreateSession](https://docs.microsoft.com/previous-versions/windows/desktop/ms714942(v=vs.85)) en el *referencia del programador OLE DB*.

## <a name="see-also"></a>Vea también

[Plantillas de proveedores OLE DB](../../data/oledb/ole-db-provider-templates-cpp.md)<br/>
[Arquitectura de plantillas de proveedores OLE DB](../../data/oledb/ole-db-provider-template-architecture.md)