---
title: IRowsetImpl (Clase)
ms.date: 11/04/2016
f1_keywords:
- IRowsetImpl
- IRowsetImpl::AddRefRows
- AddRefRows
- IRowsetImpl.AddRefRows
- ATL::IRowsetImpl::AddRefRows
- ATL.IRowsetImpl.AddRefRows
- IRowsetImpl.CreateRow
- ATL.IRowsetImpl.CreateRow
- ATL::IRowsetImpl::CreateRow
- CreateRow
- IRowsetImpl::CreateRow
- ATL.IRowsetImpl.GetData
- ATL::IRowsetImpl::GetData
- IRowsetImpl::GetData
- IRowsetImpl.GetData
- GetDBStatus
- IRowsetImpl.GetDBStatus
- IRowsetImpl::GetDBStatus
- GetNextRows
- ATL.IRowsetImpl.GetNextRows
- ATL::IRowsetImpl::GetNextRows
- IRowsetImpl::GetNextRows
- IRowsetImpl.GetNextRows
- IRowsetImpl.IRowsetImpl
- ATL::IRowsetImpl::IRowsetImpl
- ATL.IRowsetImpl.IRowsetImpl
- IRowsetImpl::IRowsetImpl
- IRowsetImpl
- ATL::IRowsetImpl::RefRows
- ATL.IRowsetImpl.RefRows
- IRowsetImpl.RefRows
- RefRows
- IRowsetImpl::RefRows
- ATL.IRowsetImpl.ReleaseRows
- ReleaseRows
- IRowsetImpl::ReleaseRows
- ATL::IRowsetImpl::ReleaseRows
- IRowsetImpl.ReleaseRows
- ATL.IRowsetImpl.RestartPosition
- IRowsetImpl::RestartPosition
- RestartPosition
- ATL::IRowsetImpl::RestartPosition
- IRowsetImpl.RestartPosition
- IRowsetImpl.SetDBStatus
- IRowsetImpl::SetDBStatus
- SetDBStatus
- ATL.IRowsetImpl.m_bCanFetchBack
- ATL::IRowsetImpl::m_bCanFetchBack
- IRowsetImpl.m_bCanFetchBack
- IRowsetImpl::m_bCanFetchBack
- m_bCanFetchBack
- IRowsetImpl::m_bCanScrollBack
- ATL::IRowsetImpl::m_bCanScrollBack
- IRowsetImpl.m_bCanScrollBack
- ATL.IRowsetImpl.m_bCanScrollBack
- m_bCanScrollBack
- ATL.IRowsetImpl.m_bReset
- IRowsetImpl.m_bReset
- m_bReset
- IRowsetImpl::m_bReset
- ATL::IRowsetImpl::m_bReset
- IRowsetImpl::m_iRowset
- IRowsetImpl.m_iRowset
- ATL::IRowsetImpl::m_iRowset
- ATL.IRowsetImpl.m_iRowset
- m_iRowset
- IRowsetImpl::m_rgRowHandles
- IRowsetImpl.m_rgRowHandles
- m_rgRowHandles
- ATL::IRowsetImpl::m_rgRowHandles
- ATL.IRowsetImpl.m_rgRowHandles
helpviewer_keywords:
- IRowsetImpl class
- AddRefRows method
- CreateRow method
- GetData method [OLE DB]
- GetDBStatus method
- GetNextRows method
- IRowsetImpl constructor
- RefRows method
- ReleaseRows method
- RestartPosition method
- SetDBStatus method
- m_bCanFetchBack
- m_bCanScrollBack
- m_bReset
- m_iRowset
- m_rgRowHandles
ms.assetid: 6a9189af-7556-45b1-adcb-9d62bb36704c
ms.openlocfilehash: 744614dac72a96da2de8722d98789ab5babb170d
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/31/2018
ms.locfileid: "50646694"
---
# <a name="irowsetimpl-class"></a>IRowsetImpl (Clase)

Proporciona una implementación de la interfaz `IRowset`.

## <a name="syntax"></a>Sintaxis

```cpp
template <
   class T, 
   class RowsetInterface,
   class RowClass = CSimpleRow,
   class MapClass = CAtlMap <
      RowClass::KeyType,
      RowClass*>>
class ATL_NO_VTABLE IRowsetImpl : public RowsetInterface
```

### <a name="parameters"></a>Parámetros

*T*<br/>
La clase derivada de `IRowsetImpl`.

*RowsetInterface*<br/>
Una clase derivada de `IRowsetImpl`.

*RowClass*<br/>
Unidad de almacenamiento para el `HROW`.

*MapClass*<br/>
Unidad de almacenamiento para todos los identificadores de fila mantenidos por el proveedor.

## <a name="requirements"></a>Requisitos

**Encabezado:** atldb.h

## <a name="members"></a>Miembros

### <a name="methods"></a>Métodos

|||
|-|-|
|[AddRefRows](#addrefrows)|Agrega un contador de referencia a un identificador de fila existente.|
|[CreateRow](#createrow)|Lo llama [GetNextRows](../../data/oledb/irowsetimpl-getnextrows.md) para asignar un nuevo `HROW`. No llama directamente al usuario.|
|[GetData](#getdata)|Recupera datos de copia del conjunto de filas de la fila.|
|[GetDBStatus](#getdbstatus)|Devuelve el estado para el campo especificado.|
|[GetNextRows](#getnextrows)|Recupera filas de forma secuencial, recordando la posición anterior.|
|[IRowsetImpl](#irowsetimpl)|El constructor. No llama directamente al usuario.|
|[RefRows](#refrows)|Lo llama [AddRefRows](../../data/oledb/irowsetimpl-addrefrows.md) y [ReleaseRows](../../data/oledb/irowsetimpl-releaserows.md). No llama directamente al usuario.|
|[ReleaseRows](#releaserows)|Libera filas.|
|[RestartPosition](#restartposition)|Se sitúa la siguiente posición de captura su posición inicial; es decir, su posición cuando el conjunto de filas se crea.|
|[SetDBStatus](#setdbstatus)|Establece las marcas de estado para el campo especificado.|

### <a name="data-members"></a>Miembros de datos

|||
|-|-|
|[m_bCanFetchBack](#bcanfetchback)|Indica si un proveedor admite la captura con versiones anteriores.|
|[m_bCanScrollBack](#bcanscrollback)|Indica si un proveedor puede tener su desplazamiento de cursor hacia atrás.|
|[m_bReset](#breset)|Indica si un proveedor restablece su posición del cursor. Esto tiene un significado especial cuando se desplazan hacia atrás o hacia atrás en la obtención [GetNextRows](../../data/oledb/irowsetimpl-getnextrows.md).|
|[m_iRowset](#irowset)|Un índice al conjunto de filas, que representa el cursor.|
|[m_rgRowHandles](#rgrowhandles)|Una lista de identificadores de fila.|

## <a name="remarks"></a>Comentarios

[IRowset](/previous-versions/windows/desktop/ms720986) es la interfaz base del conjunto de filas.

## <a name="addrefrows"></a> IRowsetImpl:: Addrefrows

Agrega un contador de referencia a un identificador de fila existente.

### <a name="syntax"></a>Sintaxis

```cpp
STDMETHOD(AddRefRows )(DBCOUNTITEM cRows,
   const HROW rghRows[],
   DBREFCOUNT rgRefCounts[],
   DBROWSTATUS rgRowStatus[]);
```

#### <a name="parameters"></a>Parámetros

Consulte [IRowset::AddRefRows](/previous-versions/windows/desktop/ms719619) en el *referencia del programador OLE DB*.

## <a name="createrow"></a> IRowsetImpl:: CreateRow

Un método auxiliar llamado por [GetNextRows](../../data/oledb/irowsetimpl-getnextrows.md) para asignar un nuevo `HROW`.

### <a name="syntax"></a>Sintaxis

```cpp
HRESULT CreateRow(DBROWOFFSET lRowsOffset,
   DBCOUNTITEM& cRowsObtained,
   HROW* rgRows);
```

#### <a name="parameters"></a>Parámetros

*lRowsOffset*<br/>
Posición del cursor de la fila que se va a crear.

*cRowsObtained*<br/>
Pasa una referencia al usuario que indica el número de filas creadas.

*rgRows*<br/>
Una matriz de `HROW`devolverá al autor de llamada con los identificadores de fila recién creado.

### <a name="remarks"></a>Comentarios

Si la fila no existe, este método llama a [AddRefRows](../../data/oledb/irowsetimpl-addrefrows.md) y devuelve. En caso contrario, asigna una nueva instancia de la variable de plantilla RowClass y lo agrega a [m_rgRowHandles](../../data/oledb/irowsetimpl-m-rgrowhandles.md).

## <a name="getdata"></a> IRowsetImpl:: GetData

Recupera datos de copia del conjunto de filas de la fila.

### <a name="syntax"></a>Sintaxis

```cpp
STDMETHOD(GetData )(HROW hRow,
   HACCESSOR hAccessor,
   void* pDstData);
```

#### <a name="parameters"></a>Parámetros

Consulte [IRowset:: GetData](/previous-versions/windows/desktop/ms716988) en el *referencia del programador OLE DB*.

Algunos parámetros se corresponden con *referencia del programador de OLE DB* parámetros de nombres diferentes, que se describen en `IRowset::GetData`:

|Parámetros de plantilla OLE DB|*Referencia del programador de OLE DB* parámetros|
|--------------------------------|------------------------------------------------|
|*pDstData*|*pData*|

### <a name="remarks"></a>Comentarios

También controla la conversión de datos mediante la conversión de datos OLE DB DLL.

## <a name="getdbstatus"></a> IRowsetImpl:: GetDBStatus

Devuelve las marcas de estado DBSTATUS para el campo especificado.

### <a name="syntax"></a>Sintaxis

```cpp
virtual DBSTATUS GetDBStatus(RowClass* currentRow,
   ATLCOLUMNINFO* columnNames);
```

#### <a name="parameters"></a>Parámetros

*currentRow*<br/>
[in] La fila actual.

*columnNames*<br/>
[in] La columna para el que se solicita el estado.

### <a name="return-value"></a>Valor devuelto

El [DBSTATUS](/previous-versions/windows/desktop/ms722617) marcas para la columna.

## <a name="getnextrows"></a> IRowsetImpl:: GetNextRows

Recupera filas de forma secuencial, recordando la posición anterior.

### <a name="syntax"></a>Sintaxis

```cpp
STDMETHOD(GetNextRows )(HCHAPTER hReserved,
   DBROWOFFSET lRowsOffset,
   DBROWCOUNT cRows,
   DBCOUNTITEM* pcRowsObtained,
   HROW** prghRows);
```

#### <a name="parameters"></a>Parámetros

Consulte [IRowset:: GetNextRows](/previous-versions/windows/desktop/ms709827) en el *referencia del programador OLE DB*.

## <a name="irowsetimpl"></a> IRowsetImpl:: IRowsetImpl

El constructor.

### <a name="syntax"></a>Sintaxis

```cpp
IRowsetImpl();
```

### <a name="remarks"></a>Comentarios

Normalmente, es necesario llamar a este método directamente.

## <a name="refrows"></a> IRowsetImpl:: Refrows

Lo llama [AddRefRows](../../data/oledb/irowsetimpl-addrefrows.md) y [ReleaseRows](../../data/oledb/irowsetimpl-releaserows.md) para incrementar o liberar un recuento de referencias a un identificador de fila existente.

### <a name="syntax"></a>Sintaxis

```cpp
HRESULT RefRows(DBCOUNTITEM cRows,
   const HROWrghRows[],
   DBREFCOUNT rgRefCounts[],
   DBROWSTATUS rgRowStatus[],
   BOOL bAdd);
```

#### <a name="parameters"></a>Parámetros

Consulte [IRowset::AddRefRows](/previous-versions/windows/desktop/ms719619) en el *referencia del programador OLE DB*.

### <a name="return-value"></a>Valor devuelto

Un valor HRESULT estándar.

## <a name="releaserows"></a> IRowsetImpl:: ReleaseRows

Libera filas.

### <a name="syntax"></a>Sintaxis

```cpp
STDMETHOD(ReleaseRows )(DBCOUNTITEM cRows,
   const HROW rghRows[],
   DBROWOPTIONS rgRowOptions[],
   DBREFCOUNT rgRefCounts[],
   DBROWSTATUS rgRowStatus[]);
```

#### <a name="parameters"></a>Parámetros

Consulte [IRowset:: ReleaseRows](/previous-versions/windows/desktop/ms719771) en el *referencia del programador OLE DB*.

## <a name="restartposition"></a> IRowsetImpl:: RestartPosition

Se sitúa la siguiente posición de captura su posición inicial; es decir, su posición cuando el conjunto de filas se crea.

### <a name="syntax"></a>Sintaxis

```cpp
STDMETHOD(RestartPosition )(HCHAPTER /* hReserved */);
```

#### <a name="parameters"></a>Parámetros

Consulte [IRowset:: RestartPosition](/previous-versions/windows/desktop/ms712877) en el *referencia del programador OLE DB*.

### <a name="remarks"></a>Comentarios

La posición del conjunto de filas no está definida hasta `GetNextRow` se llama. Puede mover hacia atrás en un rowet mediante una llamada a `RestartPosition` y, a continuación, captura o el desplazamiento hacia atrás.

## <a name="setdbstatus"></a> IRowsetImpl:: SetDBStatus

Establece las marcas de estado DBSTATUS para el campo especificado.

### <a name="syntax"></a>Sintaxis

```cpp
virtual HRESULT SetDBStatus(DBSTATUS* statusFlags,
   RowClass* currentRow,
   ATLCOLUMNINFO* columnInfo);
```

#### <a name="parameters"></a>Parámetros

*statusFlags*<br/>
El [DBSTATUS](/previous-versions/windows/desktop/ms722617) marcas van a establecer para la columna.

*currentRow*<br/>
La fila actual.

*columnInfo*<br/>
La columna para el que se define el estado.

### <a name="return-value"></a>Valor devuelto

Un valor HRESULT estándar.

### <a name="remarks"></a>Comentarios

El proveedor reemplaza esta función para proporcionar un procesamiento especial para DBSTATUS_S_ISNULL y DBSTATUS_S_DEFAULT.

## <a name="bcanfetchback"></a> IRowsetImpl:: M_bcanfetchback

Indica si un proveedor admite la captura con versiones anteriores.

### <a name="syntax"></a>Sintaxis

```cpp
unsigned m_bCanFetchBack:1;
```

### <a name="remarks"></a>Comentarios

Vinculado a la `DBPROP_CANFETCHBACKWARDS` propiedad en el `DBPROPSET_ROWSET` grupo. El proveedor debe admitir `DBPROP_CANFETCHBACKWARDS` para `m_bCanFetchBackwards` sea **true**.

## <a name="bcanscrollback"></a> IRowsetImpl:: M_bcanscrollback

Indica si un proveedor puede tener su desplazamiento de cursor hacia atrás.

### <a name="syntax"></a>Sintaxis

```cpp
unsigned  m_bCanScrollBack:1;
```

### <a name="remarks"></a>Comentarios

Vinculado a la `DBPROP_CANSCROLLBACKWARDS` propiedad en el `DBPROPSET_ROWSET` grupo. El proveedor debe admitir `DBPROP_CANSCROLLBACKWARDS` para `m_bCanFetchBackwards` sea **true**.

## <a name="breset"></a> IRowsetImpl:: M_breset

Un indicador de bits que se usa para determinar si se define la posición del cursor en el conjunto de filas.

### <a name="syntax"></a>Sintaxis

```cpp
unsigned m_bReset:1;
```

### <a name="remarks"></a>Comentarios

Si el consumidor llama a [GetNextRows](../../data/oledb/irowsetimpl-getnextrows.md) con un valor negativo `lOffset` o *cRows* y `m_bReset` es true, `GetNextRows` mueve al final del conjunto de filas. Si `m_bReset` es false, el consumidor recibe un código de error, de acuerdo con la especificación de OLE DB. El `m_bReset` marca se establece para **true** cuando se crea por primera vez el conjunto de filas y cuando el consumidor llama a [IRowsetImpl:: RestartPosition](../../data/oledb/irowsetimpl-restartposition.md). Obtiene el conjunto **false** cuando se llama a `GetNextRows`.

## <a name="irowset"></a> IRowsetImpl:: M_irowset

Un índice al conjunto de filas, que representa el cursor.

### <a name="syntax"></a>Sintaxis

```cpp
DBROWOFFSET m_iRowset;
```

## <a name="rgrowhandles"></a> IRowsetImpl:: M_rgrowhandles

Una asignación de identificadores de fila que contiene actualmente el proveedor en respuesta a `GetNextRows`.

### <a name="syntax"></a>Sintaxis

```cpp
MapClass m_rgRowHandles;
```

### <a name="remarks"></a>Comentarios

Se quitan los identificadores de fila mediante una llamada a `ReleaseRows`. Consulte la [IRowsetImpl Introducción](../../data/oledb/irowsetimpl-class.md) para la definición de *MapClass*.

## <a name="see-also"></a>Vea también

[Plantillas de proveedores OLE DB](../../data/oledb/ole-db-provider-templates-cpp.md)<br/>
[Arquitectura de plantillas de proveedores OLE DB](../../data/oledb/ole-db-provider-template-architecture.md)<br/>
[CSimpleRow (Clase)](../../data/oledb/csimplerow-class.md)