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
ms.openlocfilehash: 2056b93fd6c1d32b72996970352e87670ff406de
ms.sourcegitcommit: 72583d30170d6ef29ea5c6848dc00169f2c909aa
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/18/2019
ms.locfileid: "59034214"
---
# <a name="igetdatasourceimpl-class"></a>IGetDataSourceImpl (Clase)

Proporciona una implementación de la [IGetDataSource](/previous-versions/windows/desktop/ms709721(v=vs.85)) objeto.

## <a name="syntax"></a>Sintaxis

```cpp
template <class T>
class ATL_NO_VTABLE IGetDataSourceImpl : public IGetDataSource
```

### <a name="parameters"></a>Parámetros

*T*<br/>
La clase derivada de `IGetDataSourceImpl`.

## <a name="requirements"></a>Requisitos

**Encabezado:** atldb.h

## <a name="members"></a>Miembros

### <a name="interface-methods"></a>Métodos de interfaz

|||
|-|-|
|[GetDataSource](#getdatasource)|Devuelve un puntero de interfaz en el objeto de origen de datos que creó la sesión.|

## <a name="remarks"></a>Comentarios

Esto es una interfaz obligatoria en la sesión para obtener un puntero de interfaz al objeto de origen de datos.

## <a name="getdatasource"></a> IGetDataSourceImpl::GetDataSource

Devuelve un puntero de interfaz en el objeto de origen de datos que creó la sesión.

### <a name="syntax"></a>Sintaxis

```cpp
STDMETHOD(GetDataSource)(REFIID riid,
   IUnknown ** ppDataSource);
```

#### <a name="parameters"></a>Parámetros

Consulte [IGetDataSource::GetDataSource](/previous-versions/windows/desktop/ms725443(v=vs.85)) en el *referencia del programador OLE DB*.

### <a name="remarks"></a>Comentarios

Resulta útil si necesita tener acceso a propiedades en el objeto de origen de datos.

## <a name="see-also"></a>Vea también

[Plantillas de proveedores OLE DB](../../data/oledb/ole-db-provider-templates-cpp.md)<br/>
[Arquitectura de plantillas de proveedores OLE DB](../../data/oledb/ole-db-provider-template-architecture.md)