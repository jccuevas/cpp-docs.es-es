---
title: IRowsetLocateImpl (clase) | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-data
ms.topic: reference
f1_keywords:
- IRowsetLocateImpl
- ATL.IRowsetLocateImpl.Compare
- IRowsetLocateImpl::Compare
- IRowsetLocateImpl.Compare
- ATL::IRowsetLocateImpl::Compare
- GetRowsAt
- IRowsetLocateImpl.GetRowsAt
- ATL::IRowsetLocateImpl::GetRowsAt
- IRowsetLocateImpl::GetRowsAt
- ATL.IRowsetLocateImpl.GetRowsAt
- IRowsetLocateImpl::GetRowsByBookmark
- IRowsetLocateImpl.GetRowsByBookmark
- GetRowsByBookmark
- IRowsetLocateImpl::Hash
- IRowsetLocateImpl.Hash
- m_rgBookmarks
- IRowsetLocateImpl::m_rgBookmarks
- ATL.IRowsetLocateImpl.m_rgBookmarks
- ATL::IRowsetLocateImpl::m_rgBookmarks
- IRowsetLocateImpl.m_rgBookmarks
dev_langs:
- C++
helpviewer_keywords:
- providers, bookmarks
- IRowsetLocateImpl class
- bookmarks, OLE DB
- Compare method
- GetRowsAt method
- GetRowsByBookmark method
- Hash method
- m_rgbookmarks
ms.assetid: a8aa3149-7ce8-4976-a680-2da193fd3234
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- data-storage
ms.openlocfilehash: 35ebe1a4534fa1c3a738d84e3e6dd7037254fd49
ms.sourcegitcommit: a9dcbcc85b4c28eed280d8e451c494a00d8c4c25
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/25/2018
ms.locfileid: "50059407"
---
# <a name="irowsetlocateimpl-class"></a>IRowsetLocateImpl (Clase)

Implementa OLE DB [IRowsetLocate](/previous-versions/windows/desktop/ms721190) interfaz, que recupera filas arbitrarias de un conjunto de filas.

## <a name="syntax"></a>Sintaxis

```cpp
template <
   class T,
   class RowsetInterface,
   class RowClass = CSimpleRow,
   class MapClass = CAtlMap < RowClass::KeyType, RowClass* >,
   class BookmarkKeyType = LONG,
   class BookmarkType = LONG,
   class BookmarkMapClass = CAtlMap < RowClass::KeyType, RowClass* >>
class ATL_NO_VTABLE IRowsetLocateImpl : public IRowsetImpl<
       T,
       RowsetInterface,
       RowClass,
       MapClass>
```

### <a name="parameters"></a>Parámetros

*T*<br/>
Una clase derivada de `IRowsetLocateImpl`.

*RowsetInterface*<br/>
Una clase derivada de `IRowsetImpl`.

*RowClass*<br/>
La unidad de almacenamiento para el `HROW`.

*MapClass*<br/>
La unidad de almacenamiento para todos los identificadores de fila mantenidos por el proveedor.

*BookmarkKeyType*<br/>
El tipo del marcador, como un valor largo o una cadena. Los marcadores normales deben tener una longitud de al menos dos bytes. (Longitud de un byte está reservado para OLE DB [marcadores estándares](/previous-versions/windows/desktop/ms712954)`DBBMK_FIRST`, `DBBMK_LAST`, y `DBBMK_INVALID`.)

*BookmarkType*<br/>
El mecanismo de asignación para mantener las relaciones de datos de marcador.

*BookmarkMapClass*<br/>
La unidad de almacenamiento para todos los identificadores de fila mantenidos por el marcador.

## <a name="requirements"></a>Requisitos

**Encabezado**: atldb.h

## <a name="members"></a>Miembros

### <a name="interface-methods"></a>Métodos de interfaz

|||
|-|-|
|[Compare](#compare)|Compara dos marcadores.|
|[GetRowsAt](#getrowsat)|Captura de filas a partir de la fila especificada por un desplazamiento de un marcador.|
|[GetRowsByBookmark](#getrowsbybookmark)|Captura las filas que coinciden con los marcadores especificados.|
|[hash](#hash)|Devuelve el hash valores para los marcadores especificados.|

### <a name="data-members"></a>Miembros de datos

|||
|-|-|
|[m_rgBookmarks](#rgbookmarks)|Una matriz de marcadores.|

## <a name="remarks"></a>Comentarios

`IRowsetLocateImpl` es la implementación de plantillas OLE DB de la [IRowsetLocate](/previous-versions/windows/desktop/ms721190) interfaz. `IRowsetLocate` se utiliza para capturar filas arbitrarias de un conjunto de filas. Un conjunto de filas que implementan esta interfaz es un `sequential` conjunto de filas. Cuando `IRowsetLocate` está presente en un conjunto de filas, la columna 0 es el marcador para las filas; leyendo esta columna, se obtendrá un valor de marcador que se puede usar para cambiar la posición en la misma fila.

`IRowsetLocateImpl` se utiliza para implementar la compatibilidad con marcadores en proveedores. Los marcadores son marcadores de posición (índices en un conjunto de filas) que permiten a los consumidores volver rápidamente a una fila, lo que permite el acceso a los datos de alta velocidad. El proveedor determina qué marcadores inequívocamente pueden identificar una fila. Uso de `IRowsetLocateImpl` métodos, puede comparar los marcadores, fetch filas por desplazamiento, captura filas por marcador y devuelven valores de hash de marcadores.

Para admitir los marcadores de OLE DB en un conjunto de filas, hacer el conjunto de filas que herede de esta clase.

Para obtener información sobre la compatibilidad con marcadores de implementación, consulte [proveedor admite marcadores](../../data/oledb/provider-support-for-bookmarks.md) en el *Guía del programador de Visual C++* y [marcadores](/previous-versions/windows/desktop/ms709728) en el *Referencia del programador OLE DB* en Platform SDK.

## <a name="compare"></a> IRowsetLocateImpl:: Compare

Compara dos marcadores.

### <a name="syntax"></a>Sintaxis

```cpp
STDMETHOD (Compare )(HCHAPTER /* hReserved */,
   DBBKMARK cbBookmark1,
   const BYTE* pBookmark1,
   DBBKMARK cbBookmark2,
   const BYTE* pBookmark2,
   DBCOMPARE* pComparison);
```

#### <a name="parameters"></a>Parámetros

Consulte [IRowsetLocate:: Compare](/previous-versions/windows/desktop/ms709539) en el *referencia del programador OLE DB*.

### <a name="remarks"></a>Comentarios

Cualquiera de los marcadores pueden ser un estándar definido por OLE DB [marcador estándar](/previous-versions/windows/desktop/ms712954) (`DBBMK_FIRST`, `DBBMK_LAST`, o `DBBMK_INVALID`). El valor devuelto en `pComparison` indica la relación entre los dos marcadores:

- DBCOMPARE_LT (`cbBookmark1` antes `cbBookmark2`.)

- DBCOMPARE_EQ (`cbBookmark1` es igual a `cbBookmark2`.)

- DBCOMPARE_GT (`cbBookmark1` después `cbBookmark2`.)

- DBCOMPARE_NE (los marcadores son iguales y no ordenada).

- DBCOMPARE_NOTCOMPARABLE (no se pueden comparar los marcadores).

## <a name="getrowsat"></a> IRowsetLocateImpl:: GetRowsAt

Captura de filas a partir de la fila especificada por un desplazamiento de un marcador.

### <a name="syntax"></a>Sintaxis

```cpp
STDMETHOD (GetRowsAt )(HWATCHREGION /* hReserved1 */,
   HCHAPTER hReserved2,
   DBBKMARK cbBookmark,
   const BYTE* pBookmark,
   DBROWOFFSET lRowsOffset,
   DBROWCOUNT cRows,
   DBCOUNTITEM* pcRowsObtained,
   HROW** prghRows);
```

#### <a name="parameters"></a>Parámetros

Consulte [IRowsetLocate:: GetRowsAt](/previous-versions/windows/desktop/ms723031) en el *referencia del programador OLE DB*.

### <a name="remarks"></a>Comentarios

Para capturar desde la posición del cursor en su lugar, use [IRowset::GetRowsAt](/previous-versions/windows/desktop/ms723031).

`IRowsetLocateImpl::GetRowsAt` no cambia la posición del cursor.

## <a name="getrowsbybookmark"></a> IRowsetLocateImpl:: Getrowsbybookmark

Captura una o varias filas que coinciden con los marcadores especificados.

### <a name="syntax"></a>Sintaxis

```cpp
STDMETHOD (GetRowsByBookmark )(HCHAPTER /* hReserved */,
   DBCOUNTITEM cRows,
   const DBBKMARK rgcbBookmarks[],
   const BYTE* rgpBookmarks,
   HROW rghRows[],
   DBROWSTATUS* rgRowStatus[]);
```

#### <a name="parameters"></a>Parámetros

*hReserved*<br/>
[in] Corresponde a *hChapter* parámetro [IRowsetLocate:: Getrowsbybookmark](/previous-versions/windows/desktop/ms725420).

Para otros parámetros, vea [IRowsetLocate:: Getrowsbybookmark](/previous-versions/windows/desktop/ms725420) en el *referencia del programador de OLE DB*.

### <a name="remarks"></a>Comentarios

El marcador puede ser un valor que defina u OLE DB [marcadores estándares](/previous-versions/windows/desktop/ms712954) (`DBBMK_FIRST` o `DBBMK_LAST`). no cambia la posición del cursor.

## <a name="hash"></a> IRowsetLocateImpl:: hash

Devuelve el hash valores para los marcadores especificados.

### <a name="syntax"></a>Sintaxis

```cpp
STDMETHOD (Hash )(HCHAPTER /* hReserved */,
   DBBKMARK cbBookmarks,
   const DBBKMARK* rgcbBookmarks[],
   const BYTE* rgpBookmarks[],
   DBHASHVALUE rgHashValues[],
   DBROWSTATUS rgBookmarkStatus[]);
```

#### <a name="parameters"></a>Parámetros

*hReserved*<br/>
[in] Corresponde a *hChapter* parámetro [IRowsetLocate::Hash](/previous-versions/windows/desktop/ms709697).

Para otros parámetros, vea [IRowsetLocate::Hash](/previous-versions/windows/desktop/ms709697) en el *referencia del programador de OLE DB*.

## <a name="rgbookmarks"></a> IRowsetLocateImpl:: M_rgbookmarks

Una matriz de marcadores.

### <a name="syntax"></a>Sintaxis

```cpp
CAtlArray<DBROWCOUNT> m_rgBookmarks;
```

## <a name="see-also"></a>Vea también

[Plantillas de proveedores OLE DB](../../data/oledb/ole-db-provider-templates-cpp.md)<br/>
[Arquitectura de plantillas de proveedores OLE DB](../../data/oledb/ole-db-provider-template-architecture.md)<br/>
[IRowsetLocate:IRowset](/previous-versions/windows/desktop/ms721190)
[compatibilidad del proveedor con marcadores](../../data/oledb/provider-support-for-bookmarks.md)<br/>
[Marcadores](/previous-versions/windows/desktop/ms709728)