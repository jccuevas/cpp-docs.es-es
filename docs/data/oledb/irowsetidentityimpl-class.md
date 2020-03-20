---
title: IRowsetIdentityImpl (Clase)
ms.date: 11/04/2016
f1_keywords:
- ATL::IRowsetIdentityImpl
- ATL.IRowsetIdentityImpl
- IRowsetIdentityImpl
- IRowsetIdentityImpl.IsSameRow
- ATL.IRowsetIdentityImpl.IsSameRow
- IRowsetIdentityImpl::IsSameRow
- ATL::IRowsetIdentityImpl::IsSameRow
helpviewer_keywords:
- IRowsetIdentityImpl class
- IsSameRow method
ms.assetid: 56821edf-e045-40c8-96bd-231552cd5799
ms.openlocfilehash: 3e8c976fcb23bf41d88d88be3887db4dde52379d
ms.sourcegitcommit: 63784729604aaf526de21f6c6b62813882af930a
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 03/17/2020
ms.locfileid: "79545898"
---
# <a name="irowsetidentityimpl-class"></a>IRowsetIdentityImpl (Clase)

Implementa la interfaz OLE DB [IRowsetIdentity](/previous-versions/windows/desktop/ms715913(v=vs.85)) , que permite probar la identidad de fila.

## <a name="syntax"></a>Sintaxis

```cpp
template <class T, class RowClass = CSimpleRow>
class ATL_NO_VTABLE IRowsetIdentityImpl
   : public IRowsetIdentity
```

### <a name="parameters"></a>Parámetros

*T*<br/>
Una clase derivada de `IRowsetIdentityImpl`.

*RowClass*<br/>
Unidad de almacenamiento para el `HROW`.

## <a name="requirements"></a>Requisitos

**Encabezado:** atldb.h

## <a name="members"></a>Members

### <a name="methods"></a>Métodos

|||
|-|-|
|[IsSameRow](#issamerow)|Compara dos identificadores de fila para ver si hacen referencia a la misma fila.|

## <a name="irowsetidentityimplissamerow"></a><a name="issamerow"></a>Irowsetidentityimpl (:: IsSameRow

Compara dos identificadores de fila para ver si hacen referencia a la misma fila.

### <a name="syntax"></a>Sintaxis

```cpp
STDMETHOD(IsSameRow )(HROW hThisRow,
   HROW hThatRow);
```

#### <a name="parameters"></a>Parámetros

Vea [IRowsetIdentity:: IsSameRow](/previous-versions/windows/desktop/ms719629(v=vs.85)) en la *Referencia del programador de OLE DB*.

### <a name="remarks"></a>Observaciones

Para comparar los identificadores de fila, este método convierte los controladores de `HROW` en miembros de `RowClass` y llama a `memcmp` en los punteros.

## <a name="see-also"></a>Consulte también

[Plantillas de proveedores OLE DB](../../data/oledb/ole-db-provider-templates-cpp.md)<br/>
[Arquitectura de plantillas de proveedores OLE DB](../../data/oledb/ole-db-provider-template-architecture.md)