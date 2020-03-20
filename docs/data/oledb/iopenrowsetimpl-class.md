---
title: IOpenRowsetImpl (Clase)
ms.date: 11/04/2016
f1_keywords:
- IOpenRowsetImpl
- IOpenRowsetImpl.CreateRowset
- IOpenRowsetImpl::CreateRowset
- OpenRowset
- IOpenRowsetImpl::OpenRowset
- IOpenRowsetImpl.OpenRowset
helpviewer_keywords:
- IOpenRowsetImpl class
- CreateRowset method
- OpenRowset method
ms.assetid: d259cedc-1db4-41cf-bc9f-5030907ab486
ms.openlocfilehash: 66fce9d2ffe63798738be1658a5328e907395a54
ms.sourcegitcommit: 63784729604aaf526de21f6c6b62813882af930a
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 03/17/2020
ms.locfileid: "79545910"
---
# <a name="iopenrowsetimpl-class"></a>IOpenRowsetImpl (Clase)

Proporciona la implementación para la interfaz `IOpenRowset`.

## <a name="syntax"></a>Sintaxis

```cpp
template <class SessionClass>
class IOpenRowsetImpl : public IOpenRowset
```

### <a name="parameters"></a>Parámetros

*SessionClass*<br/>
La clase, derivada de `IOpenRowsetImpl`.

## <a name="requirements"></a>Requisitos

**Encabezado:** atldb.h

## <a name="members"></a>Members

### <a name="methods"></a>Métodos

|||
|-|-|
|[CreateRowset](#createrowset)|Crea un objeto de conjunto de filas. No lo llama directamente el usuario.|
|[OpenRowset](#openrowset)|Abre y devuelve un conjunto de filas que incluye todas las filas de una sola tabla base o índice. (No en ATLDB. C|

## <a name="remarks"></a>Observaciones

La interfaz [IOpenRowset](/previous-versions/windows/desktop/ms716946(v=vs.85)) es obligatoria para un objeto de sesión. Se abre y devuelve un conjunto de filas que incluye todas las filas de una sola tabla base o índice.

## <a name="iopenrowsetimplcreaterowset"></a><a name="createrowset"></a>Iopenrowsetimpl (:: CreateRowset

Crea un objeto de conjunto de filas. No lo llama directamente el usuario. Vea [IOpenRowset:: OPENROWSET](/previous-versions/windows/desktop/ms716724(v=vs.85)) en la *Referencia del programador de OLE DB.*

### <a name="syntax"></a>Sintaxis

```cpp
template template <class RowsetClass>
HRESULT CreateRowset(IUnknown* pUnkOuter,
   DBID* pTableID,
   DBID* pIndexID,
   REFIID riid,
   ULONG cPropertySets,
   DBPROPSET rgPropertySets[],
   IUnknown** ppRowset,
   RowsetClass*& pRowsetObj);
```

#### <a name="parameters"></a>Parámetros

*RowsetClass*<br/>
Un miembro de clase de plantilla que representa la clase de conjunto de filas del usuario. Normalmente generado por el asistente.

*pRowsetObj*<br/>
enuncia Un puntero a un objeto de conjunto de filas. Normalmente, este parámetro no se usa, pero se puede usar si debe realizar más trabajo en el conjunto de filas antes de pasarlo a un objeto COM. La duración de *pRowsetObj* está limitada por *ppRowset*.

Para otros parámetros, vea [IOpenRowset:: OPENROWSET](/previous-versions/windows/desktop/ms716724(v=vs.85)) en la *Referencia del programador de OLE DB.*

## <a name="iopenrowsetimplopenrowset"></a><a name="openrowset"></a>Iopenrowsetimpl (:: OpenRowset

Abre y devuelve un conjunto de filas que incluye todas las filas de una sola tabla base o índice.

### <a name="syntax"></a>Sintaxis

```cpp
HRESULT OpenRowset(IUnknown* pUnkOuter,
   DBID* pTableID,
   DBID* pIndexID,
   REFIID riid,
   ULONG cPropertySets,
   DBPROPSET rgPropertySets[],
   IUnknown** ppRowset);
```

#### <a name="parameters"></a>Parámetros

Vea [IOpenRowset:: OPENROWSET](/previous-versions/windows/desktop/ms716724(v=vs.85)) en la *Referencia del programador de OLE DB*.

### <a name="remarks"></a>Observaciones

Este método no se encuentra en ATLDB. C. Lo crea el Asistente para objetos ATL al crear un proveedor.

## <a name="see-also"></a>Consulte también

[Plantillas de proveedores OLE DB](../../data/oledb/ole-db-provider-templates-cpp.md)<br/>
[Arquitectura de plantillas de proveedores OLE DB](../../data/oledb/ole-db-provider-template-architecture.md)