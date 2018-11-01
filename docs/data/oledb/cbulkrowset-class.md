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
- AddRefRows
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
- CBulkRowset
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
- MoveLast
- ATL.CBulkRowset<TAccessor>.MoveNext
- ATL::CBulkRowset::MoveNext
- CBulkRowset::MoveNext
- ATL.CBulkRowset.MoveNext
- CBulkRowset.MoveNext
- ATL::CBulkRowset<TAccessor>::MoveNext
- CBulkRowset<TAccessor>.MoveNext
- CBulkRowset<TAccessor>::MoveNext
- CBulkRowset::MovePrev
- MovePrev
- CBulkRowset<TAccessor>::MovePrev
- ATL::CBulkRowset<TAccessor>::MovePrev
- CBulkRowset<TAccessor>.MovePrev
- ATL::CBulkRowset::MovePrev
- CBulkRowset.MovePrev
- ATL.CBulkRowset.MovePrev
- ATL.CBulkRowset<TAccessor>.MovePrev
- CBulkRowset<TAccessor>::MoveToBookmark
- CBulkRowset.MoveToBookmark
- MoveToBookmark
- ATL.CBulkRowset.MoveToBookmark
- CBulkRowset::MoveToBookmark
- ATL::CBulkRowset<TAccessor>::MoveToBookmark
- ATL::CBulkRowset::MoveToBookmark
- CBulkRowset.MoveToRatio
- ATL::CBulkRowset::MoveToRatio
- MoveToRatio
- CBulkRowset::MoveToRatio
- ATL.CBulkRowset<TAccessor>.MoveToRatio
- ATL::CBulkRowset<TAccessor>::MoveToRatio
- ATL.CBulkRowset.MoveToRatio
- CBulkRowset<TAccessor>::MoveToRatio
- ReleaseRows
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
ms.openlocfilehash: c62dd4ba7f4f91371378b7c1a6b0295edb3625e9
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/31/2018
ms.locfileid: "50431075"
---
# <a name="cbulkrowset-class"></a>CBulkRowset (Clase)

Recupera y manipula filas que se va a trabajar con datos de forma masiva mediante la recuperación de varios identificadores de fila con una sola llamada.

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

## <a name="members"></a>Miembros

### <a name="methods"></a>Métodos

|||
|-|-|
|[AddRefRows](#addrefrows)|Incrementa el recuento de referencias.|
|[CBulkRowset](#cbulkrowset)|Constructor.|
|[MoveFirst](#movefirst)|Recupera la primera fila de datos, realice una captura de forma masiva de nuevo si es necesario.|
|[MoveLast](#movelast)|Se mueve a la última fila.|
|[MoveNext](#movenext)|Recupera la siguiente fila de datos.|
|[MovePrev](#moveprev)|Se desplaza a la fila anterior.|
|[MoveToBookmark](#movetobookmark)|Recupera la fila en un desplazamiento especificado o la fila marcada con un marcador de marcador.|
|[MoveToRatio](#movetoratio)|Captura las filas a partir de una posición en el conjunto de filas fraccionaria.|
|[ReleaseRows](#releaserows)|Establece la fila actual (`m_nCurrentRow`) a cero y libera todas las filas.|
|[SetRows](#setrows)|Establece el número de identificadores de fila para ser recuperado por una llamada.|

## <a name="example"></a>Ejemplo

El ejemplo siguiente muestra el uso de la `CBulkRowset` clase.

[!code-cpp[NVC_OLEDB_Consumer#1](../../data/oledb/codesnippet/cpp/cbulkrowset-class_1.cpp)]

## <a name="addrefrows"></a> CBulkRowset:: Addrefrows

Las llamadas [IRowset::AddRefRows](/previous-versions/windows/desktop/ms719619) para incrementar el recuento de referencias para todas las filas recuperadas actualmente desde el conjunto de filas bulk.

### <a name="syntax"></a>Sintaxis

```cpp
HRESULT AddRefRows() throw();
```

### <a name="return-value"></a>Valor devuelto

Un HRESULT estándar.

## <a name="cbulkrowset"></a> CBulkRowset:: CBulkRowset

Crea un nuevo `CBulkRowset` de objetos y el recuento de filas de forma predeterminada se establece en 10.

### <a name="syntax"></a>Sintaxis

```cpp
CBulkRowset();
```

## <a name="movefirst"></a> CBulkRowset:: MoveFirst

Recupera la primera fila de datos.

### <a name="syntax"></a>Sintaxis

```cpp
HRESULT MoveFirst() throw();
```

### <a name="return-value"></a>Valor devuelto

Un HRESULT estándar.

## <a name="movelast"></a> CBulkRowset:: MoveLast

Se mueve a la última fila.

### <a name="syntax"></a>Sintaxis

```cpp
HRESULT MoveLast() throw();
```

### <a name="return-value"></a>Valor devuelto

Un HRESULT estándar.

## <a name="movenext"></a> CBulkRowset:: MoveNext

Recupera la siguiente fila de datos.

### <a name="syntax"></a>Sintaxis

```cpp
HRESULT MoveNext() throw();
```

### <a name="return-value"></a>Valor devuelto

Un HRESULT estándar. Cuando se alcanza el final del conjunto de filas, devuelve DB_S_ENDOFROWSET.

## <a name="moveprev"></a> CBulkRowset:: MovePrev

Se desplaza a la fila anterior.

### <a name="syntax"></a>Sintaxis

```cpp
HRESULT MovePrev() throw();
```

### <a name="return-value"></a>Valor devuelto

Un HRESULT estándar.

## <a name="movetobookmark"></a> CBulkRowset:: MoveToBookmark

Recopila la fila marcada por fila en un desplazamiento especificado o un marcador (*lSkip*) desde ese marcador.

### <a name="syntax"></a>Sintaxis

```cpp
HRESULT MoveToBookmark(const CBookmarkBase& bookmark,
   DBCOUNTITEM lSkip = 0) throw();
```

#### <a name="parameters"></a>Parámetros

*Marcador*<br/>
[in] Un marcador de marcar la ubicación desde la que desea capturar datos.

*lSkip*<br/>
[in] El recuento de número de filas desde el marcador para la fila de destino. Si *lSkip* es cero, la primera fila es la fila marcada. Si *lSkip* es 1, la primera fila es la fila después de la fila marcada. Si *lSkip* es -1, la primera fila es la fila antes de la fila marcada.

### <a name="return-value"></a>Valor devuelto

Consulte [IRowset:: GetData](/previous-versions/windows/desktop/ms716988) en el *referencia del programador OLE DB*.

## <a name="movetoratio"></a> CBulkRowset:: Movetoratio

Captura las filas a partir de una posición en el conjunto de filas fraccionaria.

### <a name="syntax"></a>Sintaxis

```cpp
HRESULT MoveToRatio(DBCOUNTITEM nNumerator,
   DBCOUNTITEM nDenominator)throw();
```

#### <a name="parameters"></a>Parámetros

*nNumerator*<br/>
[in] El numerador usa para determinar la posición desde la que se va a capturar datos fraccionaria.

*nDenominator*<br/>
[in] El denominador que se usa para determinar la posición desde la que se va a capturar datos fraccionaria.

### <a name="return-value"></a>Valor devuelto

Un HRESULT estándar.

### <a name="remarks"></a>Comentarios

`MoveToRatio` captura las filas más o menos según la siguiente fórmula:

`(nNumerator *  RowsetSize ) / nDenominator`

Donde `RowsetSize` es el tamaño del conjunto de filas, medido en filas. El proveedor específico depende de la precisión de esta fórmula. Para obtener más información, consulte [IRowsetScroll:: GetRowsAtRatio](/previous-versions/windows/desktop/ms709602) en el *referencia del programador de OLE DB*.

## <a name="releaserows"></a> CBulkRowset:: ReleaseRows

Las llamadas [IRowset:: ReleaseRows](/previous-versions/windows/desktop/ms719771) para reducir el recuento de referencias para todas las filas recuperadas actualmente desde el conjunto de filas bulk.

### <a name="syntax"></a>Sintaxis

```cpp
HRESULT ReleaseRows() throw();
```

### <a name="return-value"></a>Valor devuelto

Un HRESULT estándar.

## <a name="setrows"></a> CBulkRowset:: setRows

Establece el número de identificadores de fila recuperados por cada llamada.

### <a name="syntax"></a>Sintaxis

```cpp
void SetRows(DBROWCOUNT nRows) throw();
```

#### <a name="parameters"></a>Parámetros

*nRows*<br/>
[in] El nuevo tamaño del conjunto de filas (número de filas).

### <a name="remarks"></a>Comentarios

Si se llama a esta función, debe ser antes de abre el conjunto de filas.

## <a name="see-also"></a>Vea también

[Plantillas de consumidor OLE DB](../../data/oledb/ole-db-consumer-templates-cpp.md)<br/>
[Referencia de plantillas de consumidor OLE DB](../../data/oledb/ole-db-consumer-templates-reference.md)