---
title: CBulkRowset (Clase)
ms.date: 11/04/2016
f1_keywords:
- ATL::CBulkRowset
- ATL.CBulkRowset
- ATL::CBulkRowset<TAccessor>
- CBulkRowset
- ATL.CBulkRowset<TAccessor>
- CBulkRowset::AddRefRows
- CBulkRowset.AddRefRows
- ATL.CBulkRowset<TAccessor>.AddRefRows
- ATL::CBulkRowset::AddRefRows
- CBulkRowset<TAccessor>::AddRefRows
- ATL.CBulkRowset.AddRefRows
- ATL::CBulkRowset<TAccessor>::AddRefRows
- ATL.CBulkRowset<TAccessor>.CBulkRowset
- ATL::CBulkRowset::CBulkRowset
- CBulkRowset.CBulkRowset
- CBulkRowset::CBulkRowset
- ATL.CBulkRowset.CBulkRowset
- ATL::CBulkRowset<TAccessor>::CBulkRowset
- CBulkRowset<TAccessor>::CBulkRowset
- ATL.CBulkRowset.MoveFirst
- CBulkRowset<TAccessor>.MoveFirst
- ATL.CBulkRowset<TAccessor>.MoveFirst
- ATL::CBulkRowset::MoveFirst
- ATL::CBulkRowset<TAccessor>::MoveFirst
- CBulkRowset::MoveFirst
- CBulkRowset<TAccessor>::MoveFirst
- CBulkRowset.MoveFirst
- CBulkRowset.MoveLast
- ATL.CBulkRowset.MoveLast
- ATL::CBulkRowset<TAccessor>::MoveLast
- CBulkRowset::MoveLast
- CBulkRowset<TAccessor>.MoveLast
- ATL::CBulkRowset::MoveLast
- ATL.CBulkRowset<TAccessor>.MoveLast
- CBulkRowset<TAccessor>::MoveLast
- ATL.CBulkRowset<TAccessor>.MoveNext
- ATL::CBulkRowset::MoveNext
- CBulkRowset::MoveNext
- ATL.CBulkRowset.MoveNext
- CBulkRowset.MoveNext
- ATL::CBulkRowset<TAccessor>::MoveNext
- CBulkRowset<TAccessor>.MoveNext
- CBulkRowset<TAccessor>::MoveNext
- CBulkRowset::MovePrev
- CBulkRowset<TAccessor>::MovePrev
- ATL::CBulkRowset<TAccessor>::MovePrev
- CBulkRowset<TAccessor>.MovePrev
- ATL::CBulkRowset::MovePrev
- CBulkRowset.MovePrev
- ATL.CBulkRowset.MovePrev
- ATL.CBulkRowset<TAccessor>.MovePrev
- CBulkRowset<TAccessor>::MoveToBookmark
- CBulkRowset.MoveToBookmark
- ATL.CBulkRowset.MoveToBookmark
- CBulkRowset::MoveToBookmark
- ATL::CBulkRowset<TAccessor>::MoveToBookmark
- ATL::CBulkRowset::MoveToBookmark
- CBulkRowset.MoveToRatio
- ATL::CBulkRowset::MoveToRatio
- CBulkRowset::MoveToRatio
- ATL.CBulkRowset<TAccessor>.MoveToRatio
- ATL::CBulkRowset<TAccessor>::MoveToRatio
- ATL.CBulkRowset.MoveToRatio
- CBulkRowset<TAccessor>::MoveToRatio
- ATL.CBulkRowset<TAccessor>.ReleaseRows
- ATL::CBulkRowset<TAccessor>::ReleaseRows
- ATL.CBulkRowset.ReleaseRows
- CBulkRowset<TAccessor>::ReleaseRows
- ATL::CBulkRowset::ReleaseRows
- CBulkRowset::ReleaseRows
- CBulkRowset.ReleaseRows
- ATL.CBulkRowset.SetRows
- CBulkRowset::SetRows
- CBulkRowset<TAccessor>.SetRows
- ATL.CBulkRowset<TAccessor>.SetRows
- CBulkRowset<TAccessor>::SetRows
- ATL::CBulkRowset<TAccessor>::SetRows
- ATL::CBulkRowset::SetRows
- CBulkRowset.SetRows
- SetRows
helpviewer_keywords:
- CBulkRowset class
- AddRefRows method
- CBulkRowset class, constructor
- MoveFirst method
- MoveLast method
- MoveNext method
- MovePrev method
- MoveToBookmark method
- MoveToRatio method
- ReleaseRows method
- SetRows method
ms.assetid: c6bde426-c543-4022-a98a-9519d9e2ae59
ms.openlocfilehash: e66a183c7bbafa16b3aefea8da1472255b507468
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 03/24/2020
ms.locfileid: "80212128"
---
# <a name="cbulkrowset-class"></a>CBulkRowset (Clase)

Captura y manipula las filas para trabajar en los datos de forma masiva mediante la recuperación de varios identificadores de fila con una sola llamada.

## <a name="syntax"></a>Sintaxis

```cpp
template <class TAccessor>
class CBulkRowset : public CRowset<TAccessor>
```

### <a name="parameters"></a>Parámetros

*TAccessor*<br/>
Una clase de descriptor de acceso.

## <a name="requirements"></a>Requisitos

**Encabezado:** atldbcli.h

## <a name="members"></a>Members

### <a name="methods"></a>Métodos

|||
|-|-|
|[AddRefRows](#addrefrows)|Incrementa el recuento de referencias.|
|[CBulkRowset](#cbulkrowset)|Constructor.|
|[MoveFirst](#movefirst)|Recupera la primera fila de datos y realiza una nueva recuperación en bloque si es necesario.|
|[MoveLast](#movelast)|Se desplaza a la última fila.|
|[MoveNext](#movenext)|Recupera la siguiente fila de datos.|
|[Plaza](#moveprev)|Se desplaza a la fila anterior.|
|[MoveToBookmark](#movetobookmark)|Captura la fila marcada por un marcador o la fila en un desplazamiento especificado de ese marcador.|
|[MoveToRatio](#movetoratio)|Captura las filas a partir de una posición fraccionaria en el conjunto de filas.|
|[ReleaseRows](#releaserows)|Establece la fila actual (`m_nCurrentRow`) en cero y libera todas las filas.|
|[SetRows](#setrows)|Establece el número de identificadores de fila que se van a recuperar en una llamada.|

## <a name="example"></a>Ejemplo

En el ejemplo siguiente se muestra el uso de la clase `CBulkRowset`.

[!code-cpp[NVC_OLEDB_Consumer#1](../../data/oledb/codesnippet/cpp/cbulkrowset-class_1.cpp)]

## <a name="cbulkrowsetaddrefrows"></a><a name="addrefrows"></a>CBulkRowset:: AddRefRows

Llama a [IRowset:: AddRefRows](/previous-versions/windows/desktop/ms719619(v=vs.85)) para incrementar el recuento de referencias para todas las filas recuperadas actualmente del conjunto de filas bulk.

### <a name="syntax"></a>Sintaxis

```cpp
HRESULT AddRefRows() throw();
```

### <a name="return-value"></a>Valor devuelto

HRESULT estándar.

## <a name="cbulkrowsetcbulkrowset"></a><a name="cbulkrowset"></a>CBulkRowset:: CBulkRowset

Crea un nuevo objeto `CBulkRowset` y establece el recuento de filas predeterminado en 10.

### <a name="syntax"></a>Sintaxis

```cpp
CBulkRowset();
```

## <a name="cbulkrowsetmovefirst"></a><a name="movefirst"></a>CBulkRowset:: MoveFirst

Recupera la primera fila de datos.

### <a name="syntax"></a>Sintaxis

```cpp
HRESULT MoveFirst() throw();
```

### <a name="return-value"></a>Valor devuelto

HRESULT estándar.

## <a name="cbulkrowsetmovelast"></a><a name="movelast"></a>CBulkRowset:: MoveLast

Se desplaza a la última fila.

### <a name="syntax"></a>Sintaxis

```cpp
HRESULT MoveLast() throw();
```

### <a name="return-value"></a>Valor devuelto

HRESULT estándar.

## <a name="cbulkrowsetmovenext"></a><a name="movenext"></a>CBulkRowset:: MoveNext

Recupera la siguiente fila de datos.

### <a name="syntax"></a>Sintaxis

```cpp
HRESULT MoveNext() throw();
```

### <a name="return-value"></a>Valor devuelto

HRESULT estándar. Cuando se alcanza el final del conjunto de filas, devuelve DB_S_ENDOFROWSET.

## <a name="cbulkrowsetmoveprev"></a><a name="moveprev"></a>CBulkRowset:: MovePrev

Se desplaza a la fila anterior.

### <a name="syntax"></a>Sintaxis

```cpp
HRESULT MovePrev() throw();
```

### <a name="return-value"></a>Valor devuelto

HRESULT estándar.

## <a name="cbulkrowsetmovetobookmark"></a><a name="movetobookmark"></a>CBulkRowset:: MoveToBookmark

Captura la fila marcada por un marcador o la fila en un desplazamiento especificado (*lSkip*) de ese marcador.

### <a name="syntax"></a>Sintaxis

```cpp
HRESULT MoveToBookmark(const CBookmarkBase& bookmark,
   DBCOUNTITEM lSkip = 0) throw();
```

#### <a name="parameters"></a>Parámetros

*Marcador*<br/>
de Marcador que marca la ubicación desde la que se van a capturar los datos.

*lSkip*<br/>
de Número de filas del marcador a la fila de destino. Si *lSkip* es cero, la primera fila capturada es la fila marcada. Si *lSkip* es 1, la primera fila capturada es la fila que se encuentra después de la fila marcada. Si *lSkip* es-1, la primera fila capturada es la fila anterior a la fila marcada.

### <a name="return-value"></a>Valor devuelto

Vea [IRowset:: GetData](/previous-versions/windows/desktop/ms716988(v=vs.85)) en la *Referencia del programador de OLE DB*.

## <a name="cbulkrowsetmovetoratio"></a><a name="movetoratio"></a>CBulkRowset:: MoveToRatio

Captura las filas a partir de una posición fraccionaria en el conjunto de filas.

### <a name="syntax"></a>Sintaxis

```cpp
HRESULT MoveToRatio(DBCOUNTITEM nNumerator,
   DBCOUNTITEM nDenominator)throw();
```

#### <a name="parameters"></a>Parámetros

*nNumerator*<br/>
de El numerador utilizado para determinar la posición decimal desde la que se van a capturar los datos.

*nDenominator*<br/>
de El denominador que se usa para determinar la posición fraccionaria desde la que se van a capturar los datos.

### <a name="return-value"></a>Valor devuelto

HRESULT estándar.

### <a name="remarks"></a>Observaciones

`MoveToRatio` captura las filas aproximadamente según la fórmula siguiente:

`(nNumerator *  RowsetSize ) / nDenominator`

donde `RowsetSize` es el tamaño del conjunto de filas, medido en filas. La precisión de esta fórmula depende del proveedor concreto. Para obtener más información, vea [IRowsetScroll:: GetRowsAtRatio](/previous-versions/windows/desktop/ms709602(v=vs.85)) en la *Referencia del programador de OLE DB*.

## <a name="cbulkrowsetreleaserows"></a><a name="releaserows"></a>CBulkRowset:: ReleaseRows

Llama a [IRowset:: ReleaseRows](/previous-versions/windows/desktop/ms719771(v=vs.85)) para reducir el recuento de referencias para todas las filas recuperadas actualmente del conjunto de filas bulk.

### <a name="syntax"></a>Sintaxis

```cpp
HRESULT ReleaseRows() throw();
```

### <a name="return-value"></a>Valor devuelto

HRESULT estándar.

## <a name="cbulkrowsetsetrows"></a><a name="setrows"></a>CBulkRowset:: SetRows

Establece el número de identificadores de fila recuperados por cada llamada.

### <a name="syntax"></a>Sintaxis

```cpp
void SetRows(DBROWCOUNT nRows) throw();
```

#### <a name="parameters"></a>Parámetros

*nRows*<br/>
de Nuevo tamaño del conjunto de filas (número de filas).

### <a name="remarks"></a>Observaciones

Si llama a esta función, debe ser antes de que se abra el conjunto de filas.

## <a name="see-also"></a>Consulte también

[Plantillas de consumidor OLE DB](../../data/oledb/ole-db-consumer-templates-cpp.md)<br/>
[Referencia de plantillas de consumidor OLE DB](../../data/oledb/ole-db-consumer-templates-reference.md)
