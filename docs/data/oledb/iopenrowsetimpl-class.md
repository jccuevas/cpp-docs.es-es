---
title: IOpenRowsetImpl (clase) | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-data
ms.topic: reference
f1_keywords:
- IOpenRowsetImpl
- IOpenRowsetImpl.CreateRowset
- IOpenRowsetImpl::CreateRowset
- CreateRowset
- OpenRowset
- IOpenRowsetImpl::OpenRowset
- IOpenRowsetImpl.OpenRowset
dev_langs:
- C++
helpviewer_keywords:
- IOpenRowsetImpl class
- CreateRowset method
- OpenRowset method
ms.assetid: d259cedc-1db4-41cf-bc9f-5030907ab486
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- data-storage
ms.openlocfilehash: 72ca35ad6f2246a517c8a8d103c1a7f37e142534
ms.sourcegitcommit: a9dcbcc85b4c28eed280d8e451c494a00d8c4c25
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/25/2018
ms.locfileid: "50063437"
---
# <a name="iopenrowsetimpl-class"></a>IOpenRowsetImpl (Clase)

Proporciona la implementación de la `IOpenRowset` interfaz.

## <a name="syntax"></a>Sintaxis

```cpp
template <class SessionClass>
class IOpenRowsetImpl : public IOpenRowset
```

### <a name="parameters"></a>Parámetros

*SessionClass*<br/>
La clase derivada de `IOpenRowsetImpl`.

## <a name="requirements"></a>Requisitos

**Encabezado:** atldb.h

## <a name="members"></a>Miembros

### <a name="methods"></a>Métodos

|||
|-|-|
|[CreateRowset](#createrowset)|Crea un objeto de conjunto de filas. No llama directamente al usuario.|
|[OpenRowset](#openrowset)|Se abre y devuelve un conjunto de filas que incluye todas las filas de una única tabla base o índice. (No en ATLDB. H)|

## <a name="remarks"></a>Comentarios

El [IOpenRowset](/previous-versions/windows/desktop/ms716946) interfaz es obligatoria para un objeto de sesión. Se abre y devuelve un conjunto de filas que incluye todas las filas de una única tabla base o índice.

## <a name="createrowset"></a> Iopenrowsetimpl:: CreateRowset

Crea un objeto de conjunto de filas. No llama directamente al usuario. Consulte [IOpenRowset:: OpenRowset](/previous-versions/windows/desktop/ms716724) en el *referencia del programador OLE DB.*

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
Un miembro de clase de plantilla que representa la clase de conjunto de filas del usuario. Normalmente, generado por el asistente.

*pRowsetObj*<br/>
[out] Un puntero a un objeto de conjunto de filas. Normalmente no se usa este parámetro, pero puede usarse si tiene que realizar más trabajo en el conjunto de filas antes de pasarlo a un objeto COM. La duración de *pRowsetObj* está limitado por *ppRowset*.

Para otros parámetros, vea [IOpenRowset:: OpenRowset](/previous-versions/windows/desktop/ms716724) en el *referencia del programador de OLE DB.*

## <a name="openrowset"></a> Iopenrowsetimpl:: OpenRowset

Se abre y devuelve un conjunto de filas que incluye todas las filas de una única tabla base o índice.

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

Consulte [IOpenRowset:: OpenRowset](/previous-versions/windows/desktop/ms716724) en el *referencia del programador OLE DB*.

### <a name="remarks"></a>Comentarios

Este método no se encuentra en ATLDB. H. Se crea mediante el Asistente para objetos ATL cuando se crea un proveedor.

## <a name="see-also"></a>Vea también

[Plantillas de proveedores OLE DB](../../data/oledb/ole-db-provider-templates-cpp.md)<br/>
[Arquitectura de plantillas de proveedores OLE DB](../../data/oledb/ole-db-provider-template-architecture.md)