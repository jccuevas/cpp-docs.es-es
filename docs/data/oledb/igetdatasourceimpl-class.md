---
title: IGetDataSourceImpl (Clase)
ms.date: 11/04/2016
f1_keywords:
- IGetDataSourceImpl
- ATL.IGetDataSourceImpl<T>
- ATL.IGetDataSourceImpl
- ATL::IGetDataSourceImpl
- ATL::IGetDataSourceImpl<T>
- GetDataSource
- IGetDataSourceImpl.GetDataSource
- IGetDataSourceImpl::GetDataSource
helpviewer_keywords:
- IGetDataSourceImpl class
- GetDataSource method
ms.assetid: d63f3178-d663-4f01-8c09-8aab2dd6805a
ms.openlocfilehash: 596dd2ea7f65040ae526662974d210c1f99a0cf2
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 03/24/2020
ms.locfileid: "80210618"
---
# <a name="igetdatasourceimpl-class"></a>IGetDataSourceImpl (Clase)

Proporciona una implementación del objeto [IGetDataSource](/previous-versions/windows/desktop/ms709721(v=vs.85)) .

## <a name="syntax"></a>Sintaxis

```cpp
template <class T>
class ATL_NO_VTABLE IGetDataSourceImpl : public IGetDataSource
```

### <a name="parameters"></a>Parámetros

*T*<br/>
La clase, derivada de `IGetDataSourceImpl`.

## <a name="requirements"></a>Requisitos

**Encabezado:** atldb.h

## <a name="members"></a>Members

### <a name="interface-methods"></a>Métodos de interfaz

|||
|-|-|
|[GetDataSource](#getdatasource)|Devuelve un puntero de interfaz en el objeto de origen de datos que creó la sesión.|

## <a name="remarks"></a>Observaciones

Se trata de una interfaz obligatoria en la sesión para obtener un puntero de interfaz al objeto de origen de datos.

## <a name="igetdatasourceimplgetdatasource"></a><a name="getdatasource"></a>Igetdatasourceimpl (:: GetDataSource

Devuelve un puntero de interfaz en el objeto de origen de datos que creó la sesión.

### <a name="syntax"></a>Sintaxis

```cpp
STDMETHOD(GetDataSource)(REFIID riid,
   IUnknown ** ppDataSource);
```

#### <a name="parameters"></a>Parámetros

Vea [IGetDataSource:: GetDataSource](/previous-versions/windows/desktop/ms725443(v=vs.85)) en la *Referencia del programador de OLE DB*.

### <a name="remarks"></a>Observaciones

Resulta útil si necesita tener acceso a las propiedades en el objeto de origen de datos.

## <a name="see-also"></a>Consulte también

[Plantillas de proveedores OLE DB](../../data/oledb/ole-db-provider-templates-cpp.md)<br/>
[Arquitectura de plantillas de proveedores OLE DB](../../data/oledb/ole-db-provider-template-architecture.md)
