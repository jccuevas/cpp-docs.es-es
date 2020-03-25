---
title: IRowsetLocateImpl (Clase)
ms.date: 11/04/2016
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
ms.openlocfilehash: 06e860425215d9fde268b780c001301b14a1caa1
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 03/24/2020
ms.locfileid: "80210436"
---
# <a name="irowsetlocateimpl-class"></a>IRowsetLocateImpl (Clase)

Implementa el OLE DB interfaz [IRowsetLocate](/previous-versions/windows/desktop/ms721190(v=vs.85)) , que captura filas arbitrarias de un conjunto de filas.

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
Unidad de almacenamiento para el `HROW`.

*MapClass*<br/>
Unidad de almacenamiento para todos los identificadores de fila retenidos por el proveedor.

*BookmarkKeyType*<br/>
Tipo del marcador, como un valor LONG o una cadena. Los marcadores ordinarios deben tener una longitud de al menos dos bytes. (La longitud de un solo byte está reservada para los [marcadores estándar](/previous-versions/windows/desktop/ms712954(v=vs.85)) OLE DB`DBBMK_FIRST`, `DBBMK_LAST`y `DBBMK_INVALID`).

*BookmarkType*<br/>
Mecanismo de asignación para mantener relaciones de marcador a datos.

*BookmarkMapClass*<br/>
Unidad de almacenamiento para todos los identificadores de fila mantenidos por el marcador.

## <a name="requirements"></a>Requisitos

**Encabezado**: atldb. h

## <a name="members"></a>Members

### <a name="interface-methods"></a>Métodos de interfaz

|||
|-|-|
|[Comparar](#compare)|Compara dos marcadores.|
|[GetRowsAt](#getrowsat)|Captura las filas a partir de la fila especificada por un desplazamiento de un marcador.|
|[GetRowsByBookmark](#getrowsbybookmark)|Captura las filas que coinciden con los marcadores especificados.|
|[Hash](#hash)|Devuelve valores hash para los marcadores especificados.|

### <a name="data-members"></a>Miembros de datos

|||
|-|-|
|[m_rgBookmarks](#rgbookmarks)|Matriz de marcadores.|

## <a name="remarks"></a>Observaciones

`IRowsetLocateImpl` es la implementación de plantillas de OLE DB de la interfaz [IRowsetLocate](/previous-versions/windows/desktop/ms721190(v=vs.85)) . `IRowsetLocate` se utiliza para capturar filas arbitrarias de un conjunto de filas. Un conjunto de filas que no implementa esta interfaz es un conjunto de filas `sequential`. Cuando `IRowsetLocate` está presente en un conjunto de filas, la columna 0 es el marcador de las filas; al leer esta columna se obtiene un valor de marcador que se puede usar para cambiar la posición a la misma fila.

`IRowsetLocateImpl` se usa para implementar la compatibilidad de marcadores en los proveedores. Los marcadores son marcadores de posición (índices en un conjunto de filas) que permiten al consumidor volver rápidamente a una fila, lo que permite el acceso de alta velocidad a los datos. El proveedor determina qué marcadores pueden identificar una fila de forma única. Mediante el uso de métodos `IRowsetLocateImpl`, puede comparar marcadores, capturar filas por desplazamiento, capturar filas por marcador y devolver valores hash para marcadores.

Para admitir OLE DB marcadores en un conjunto de filas, haga que el conjunto de filas herede de esta clase.

Para obtener información sobre cómo implementar la compatibilidad con marcadores, vea [compatibilidad de proveedores para marcadores](../../data/oledb/provider-support-for-bookmarks.md) en la *Guía del programador Visual C++*  y [marcadores](/previous-versions/windows/desktop/ms709728(v=vs.85)) en la *Referencia del programador de OLE DB* en el SDK de la plataforma.

## <a name="irowsetlocateimplcompare"></a><a name="compare"></a>IRowsetLocateImpl:: Compare

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

Vea [IRowsetLocate:: Compare](/previous-versions/windows/desktop/ms709539(v=vs.85)) en la *Referencia del programador de OLE DB*.

### <a name="remarks"></a>Observaciones

Cualquiera de los marcadores puede ser un [marcador](/previous-versions/windows/desktop/ms712954(v=vs.85)) estándar definido por el OLE DB estándar (`DBBMK_FIRST`, `DBBMK_LAST`o `DBBMK_INVALID`). El valor devuelto en `pComparison` indica la relación entre los dos marcadores:

- DBCOMPARE_LT (`cbBookmark1` es anterior a `cbBookmark2`).

- DBCOMPARE_EQ (`cbBookmark1` es igual a `cbBookmark2`).

- DBCOMPARE_GT (`cbBookmark1` se encuentra después de `cbBookmark2`).

- DBCOMPARE_NE (los marcadores son iguales y no se ordenan).

- DBCOMPARE_NOTCOMPARABLE (no se pueden comparar los marcadores).

## <a name="irowsetlocateimplgetrowsat"></a><a name="getrowsat"></a>IRowsetLocateImpl:: GetRowsAt

Captura las filas a partir de la fila especificada por un desplazamiento de un marcador.

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

Vea [IRowsetLocate:: GetRowsAt](/previous-versions/windows/desktop/ms723031(v=vs.85)) en la *Referencia del programador de OLE DB*.

### <a name="remarks"></a>Observaciones

Para recuperar desde la posición del cursor en su lugar, use [IRowset:: GetRowsAt](/previous-versions/windows/desktop/ms723031(v=vs.85)).

`IRowsetLocateImpl::GetRowsAt` no cambia la posición del cursor.

## <a name="irowsetlocateimplgetrowsbybookmark"></a><a name="getrowsbybookmark"></a>IRowsetLocateImpl:: GetRowsByBookmark

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
de Corresponde al parámetro *hChapter* en [IRowsetLocate:: GetRowsByBookmark](/previous-versions/windows/desktop/ms725420(v=vs.85)).

Para otros parámetros, vea [IRowsetLocate:: GetRowsByBookmark](/previous-versions/windows/desktop/ms725420(v=vs.85)) en la *Referencia del programador de OLE DB*.

### <a name="remarks"></a>Observaciones

El marcador puede ser un valor definido por el usuario o un OLE DB [marcadores estándar](/previous-versions/windows/desktop/ms712954(v=vs.85)) (`DBBMK_FIRST` o `DBBMK_LAST`). No cambia la posición del cursor.

## <a name="irowsetlocateimplhash"></a><a name="hash"></a>IRowsetLocateImpl:: hash

Devuelve valores hash para los marcadores especificados.

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
de Corresponde al parámetro *hChapter* en [IRowsetLocate:: hash](/previous-versions/windows/desktop/ms709697(v=vs.85)).

Para otros parámetros, vea [IRowsetLocate:: hash](/previous-versions/windows/desktop/ms709697(v=vs.85)) en la *Referencia del programador de OLE DB*.

## <a name="irowsetlocateimplm_rgbookmarks"></a><a name="rgbookmarks"></a>IRowsetLocateImpl:: m_rgBookmarks

Matriz de marcadores.

### <a name="syntax"></a>Sintaxis

```cpp
CAtlArray<DBROWCOUNT> m_rgBookmarks;
```

## <a name="see-also"></a>Consulte también

[Plantillas de proveedores OLE DB](../../data/oledb/ole-db-provider-templates-cpp.md)<br/>
[Arquitectura de plantillas de proveedores OLE DB](../../data/oledb/ole-db-provider-template-architecture.md)<br/>
[IRowsetLocate: IRowset](/previous-versions/windows/desktop/ms721190(v=vs.85))
[compatibilidad del proveedor](../../data/oledb/provider-support-for-bookmarks.md) con los marcadores<br/>
[Marcadores](/previous-versions/windows/desktop/ms709728(v=vs.85))
