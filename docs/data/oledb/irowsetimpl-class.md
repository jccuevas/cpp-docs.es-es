---
title: IRowsetImpl (Clase)
ms.date: 11/04/2016
f1_keywords:
- IRowsetImpl
- IRowsetImpl::AddRefRows
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
- ATL::IRowsetImpl::RefRows
- ATL.IRowsetImpl.RefRows
- IRowsetImpl.RefRows
- RefRows
- IRowsetImpl::RefRows
- ATL.IRowsetImpl.ReleaseRows
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
ms.openlocfilehash: 2fbe461bfc812c5ac9b9a09aa3ed31c0a2a638e1
ms.sourcegitcommit: 63784729604aaf526de21f6c6b62813882af930a
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 03/17/2020
ms.locfileid: "79546048"
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
La clase, derivada de `IRowsetImpl`.

*RowsetInterface*<br/>
Una clase derivada de `IRowsetImpl`.

*RowClass*<br/>
Unidad de almacenamiento para el `HROW`.

*MapClass*<br/>
Unidad de almacenamiento para todos los identificadores de fila retenidos por el proveedor.

## <a name="requirements"></a>Requisitos

**Encabezado:** atldb.h

## <a name="members"></a>Members

### <a name="methods"></a>Métodos

|||
|-|-|
|[AddRefRows](#addrefrows)|Agrega un contador de referencias a un identificador de fila existente.|
|[CreateRow](#createrow)|Llamado por [GetNextRows](../../data/oledb/irowsetimpl-getnextrows.md) para asignar una nueva `HROW`. No lo llama directamente el usuario.|
|[GetData](#getdata)|Recupera los datos desde la copia del conjunto de filas de la fila.|
|[GetDBStatus](#getdbstatus)|Devuelve el estado del campo especificado.|
|[GetNextRows](#getnextrows)|Obtiene las filas de forma secuencial, recordando la posición anterior.|
|[IRowsetImpl](#irowsetimpl)|El constructor. No lo llama directamente el usuario.|
|[RefRows](#refrows)|Llamado por [AddRefRows](../../data/oledb/irowsetimpl-addrefrows.md) y [ReleaseRows](../../data/oledb/irowsetimpl-releaserows.md). No lo llama directamente el usuario.|
|[ReleaseRows](#releaserows)|Libera filas.|
|[RestartPosition](#restartposition)|Cambia de posición la siguiente posición de captura a su posición inicial; es decir, su posición cuando se creó el conjunto de filas por primera vez.|
|[SetDBStatus](#setdbstatus)|Establece las marcas de estado para el campo especificado.|

### <a name="data-members"></a>Miembros de datos

|||
|-|-|
|[m_bCanFetchBack](#bcanfetchback)|Indica si un proveedor admite la captura hacia atrás.|
|[m_bCanScrollBack](#bcanscrollback)|Indica si un proveedor puede desplazarse hacia atrás.|
|[m_bReset](#breset)|Indica si un proveedor ha restablecido su posición del cursor. Esto tiene un significado especial al desplazarse hacia atrás o al recuperar hacia atrás en [GetNextRows](../../data/oledb/irowsetimpl-getnextrows.md).|
|[m_iRowset](#irowset)|Índice del conjunto de filas que representa el cursor.|
|[m_rgRowHandles](#rgrowhandles)|Lista de identificadores de fila.|

## <a name="remarks"></a>Observaciones

[IRowset](/previous-versions/windows/desktop/ms720986(v=vs.85)) es la interfaz de conjunto de filas base.

## <a name="irowsetimpladdrefrows"></a><a name="addrefrows"></a>IRowsetImpl:: AddRefRows

Agrega un contador de referencias a un identificador de fila existente.

### <a name="syntax"></a>Sintaxis

```cpp
STDMETHOD(AddRefRows )(DBCOUNTITEM cRows,
   const HROW rghRows[],
   DBREFCOUNT rgRefCounts[],
   DBROWSTATUS rgRowStatus[]);
```

#### <a name="parameters"></a>Parámetros

Vea [IRowset:: AddRefRows](/previous-versions/windows/desktop/ms719619(v=vs.85)) en la *Referencia del programador de OLE DB*.

## <a name="irowsetimplcreaterow"></a><a name="createrow"></a>IRowsetImpl:: CreateRow

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
Referencia devuelta al usuario que indica el número de filas creadas.

*rgRows*<br/>
Matriz de `HROW`s que se devuelve al llamador con los identificadores de fila recién creados.

### <a name="remarks"></a>Observaciones

Si existe la fila, este método llama a [AddRefRows](../../data/oledb/irowsetimpl-addrefrows.md) y devuelve. De lo contrario, asigna una nueva instancia de la variable de plantilla RowClass y la agrega a [m_rgRowHandles](../../data/oledb/irowsetimpl-m-rgrowhandles.md).

## <a name="irowsetimplgetdata"></a><a name="getdata"></a>IRowsetImpl:: GetData

Recupera los datos desde la copia del conjunto de filas de la fila.

### <a name="syntax"></a>Sintaxis

```cpp
STDMETHOD(GetData )(HROW hRow,
   HACCESSOR hAccessor,
   void* pDstData);
```

#### <a name="parameters"></a>Parámetros

Vea [IRowset:: GetData](/previous-versions/windows/desktop/ms716988(v=vs.85)) en la *Referencia del programador de OLE DB*.

Algunos parámetros corresponden a los parámetros de *Referencia del programador de OLE DB* de nombres diferentes, que se describen en `IRowset::GetData`:

|OLE DB de los parámetros de plantilla|Parámetros *de referencia del programador de OLE DB*|
|--------------------------------|------------------------------------------------|
|*pDstData*|*pData*|

### <a name="remarks"></a>Observaciones

También controla la conversión de datos mediante la OLE DB DLL de conversión de datos.

## <a name="irowsetimplgetdbstatus"></a><a name="getdbstatus"></a>IRowsetImpl:: GetDBStatus

Devuelve las marcas de estado DBSTATUS para el campo especificado.

### <a name="syntax"></a>Sintaxis

```cpp
virtual DBSTATUS GetDBStatus(RowClass* currentRow,
   ATLCOLUMNINFO* columnNames);
```

#### <a name="parameters"></a>Parámetros

*currentRow*<br/>
de La fila actual.

*columnNames*<br/>
de Columna para la que se solicita el estado.

### <a name="return-value"></a>Valor devuelto

Marcas de [DBSTATUS](/previous-versions/windows/desktop/ms722617(v=vs.85)) para la columna.

## <a name="irowsetimplgetnextrows"></a><a name="getnextrows"></a>IRowsetImpl:: GetNextRows

Obtiene las filas de forma secuencial, recordando la posición anterior.

### <a name="syntax"></a>Sintaxis

```cpp
STDMETHOD(GetNextRows )(HCHAPTER hReserved,
   DBROWOFFSET lRowsOffset,
   DBROWCOUNT cRows,
   DBCOUNTITEM* pcRowsObtained,
   HROW** prghRows);
```

#### <a name="parameters"></a>Parámetros

Vea [IRowset:: GetNextRows](/previous-versions/windows/desktop/ms709827(v=vs.85)) en la *Referencia del programador de OLE DB*.

## <a name="irowsetimplirowsetimpl"></a><a name="irowsetimpl"></a>IRowsetImpl:: IRowsetImpl

El constructor.

### <a name="syntax"></a>Sintaxis

```cpp
IRowsetImpl();
```

### <a name="remarks"></a>Observaciones

Normalmente no es necesario llamar a este método directamente.

## <a name="irowsetimplrefrows"></a><a name="refrows"></a>IRowsetImpl:: RefRows

Lo llama [AddRefRows](../../data/oledb/irowsetimpl-addrefrows.md) y [ReleaseRows](../../data/oledb/irowsetimpl-releaserows.md) para aumentar o liberar un recuento de referencias a un identificador de fila existente.

### <a name="syntax"></a>Sintaxis

```cpp
HRESULT RefRows(DBCOUNTITEM cRows,
   const HROWrghRows[],
   DBREFCOUNT rgRefCounts[],
   DBROWSTATUS rgRowStatus[],
   BOOL bAdd);
```

#### <a name="parameters"></a>Parámetros

Vea [IRowset:: AddRefRows](/previous-versions/windows/desktop/ms719619(v=vs.85)) en la *Referencia del programador de OLE DB*.

### <a name="return-value"></a>Valor devuelto

Valor HRESULT estándar.

## <a name="irowsetimplreleaserows"></a><a name="releaserows"></a>IRowsetImpl:: ReleaseRows

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

Vea [IRowset:: ReleaseRows](/previous-versions/windows/desktop/ms719771(v=vs.85)) en la *Referencia del programador de OLE DB*.

## <a name="irowsetimplrestartposition"></a><a name="restartposition"></a>IRowsetImpl:: RestartPosition

Cambia de posición la siguiente posición de captura a su posición inicial; es decir, su posición cuando se creó el conjunto de filas por primera vez.

### <a name="syntax"></a>Sintaxis

```cpp
STDMETHOD(RestartPosition )(HCHAPTER /* hReserved */);
```

#### <a name="parameters"></a>Parámetros

Vea [IRowset:: RestartPosition](/previous-versions/windows/desktop/ms712877(v=vs.85)) en la *Referencia del programador de OLE DB*.

### <a name="remarks"></a>Observaciones

La posición del conjunto de filas no está definida hasta que se llama a `GetNextRow`. Puede desplazarse hacia atrás en un rowet llamando `RestartPosition` y, a continuación, obteniendo o desplazarse hacia atrás.

## <a name="irowsetimplsetdbstatus"></a><a name="setdbstatus"></a>IRowsetImpl:: SetDBStatus

Establece las marcas de estado de DBSTATUS para el campo especificado.

### <a name="syntax"></a>Sintaxis

```cpp
virtual HRESULT SetDBStatus(DBSTATUS* statusFlags,
   RowClass* currentRow,
   ATLCOLUMNINFO* columnInfo);
```

#### <a name="parameters"></a>Parámetros

*statusFlags*<br/>
Marcas [DBSTATUS](/previous-versions/windows/desktop/ms722617(v=vs.85)) que se van a establecer para la columna.

*currentRow*<br/>
La fila actual.

*columnInfo*<br/>
Columna para la que se establece el estado.

### <a name="return-value"></a>Valor devuelto

Valor HRESULT estándar.

### <a name="remarks"></a>Observaciones

El proveedor invalida esta función para proporcionar un procesamiento especial para DBSTATUS_S_ISNULL y DBSTATUS_S_DEFAULT.

## <a name="irowsetimplm_bcanfetchback"></a><a name="bcanfetchback"></a>IRowsetImpl:: m_bCanFetchBack

Indica si un proveedor admite la captura hacia atrás.

### <a name="syntax"></a>Sintaxis

```cpp
unsigned m_bCanFetchBack:1;
```

### <a name="remarks"></a>Observaciones

Vinculado a la propiedad `DBPROP_CANFETCHBACKWARDS` en el grupo de `DBPROPSET_ROWSET`. El proveedor debe admitir `DBPROP_CANFETCHBACKWARDS` para que `m_bCanFetchBackwards` sea **true**.

## <a name="irowsetimplm_bcanscrollback"></a><a name="bcanscrollback"></a>IRowsetImpl:: m_bCanScrollBack

Indica si un proveedor puede desplazarse hacia atrás.

### <a name="syntax"></a>Sintaxis

```cpp
unsigned  m_bCanScrollBack:1;
```

### <a name="remarks"></a>Observaciones

Vinculado a la propiedad `DBPROP_CANSCROLLBACKWARDS` en el grupo de `DBPROPSET_ROWSET`. El proveedor debe admitir `DBPROP_CANSCROLLBACKWARDS` para que `m_bCanFetchBackwards` sea **true**.

## <a name="irowsetimplm_breset"></a><a name="breset"></a>IRowsetImpl:: m_bReset

Marca de bits que se usa para determinar si la posición del cursor está definida en el conjunto de filas.

### <a name="syntax"></a>Sintaxis

```cpp
unsigned m_bReset:1;
```

### <a name="remarks"></a>Observaciones

Si el consumidor llama a [GetNextRows](../../data/oledb/irowsetimpl-getnextrows.md) con una `lOffset` negativa o *crows* y `m_bReset` es true, `GetNextRows` se desplaza al final del conjunto de filas. Si `m_bReset` es false, el consumidor recibe un código de error, de acuerdo con la especificación OLE DB. La marca de `m_bReset` se establece en **true** cuando el conjunto de filas se crea por primera vez y cuando el consumidor llama a [IRowsetImpl:: RestartPosition](../../data/oledb/irowsetimpl-restartposition.md). Se establece en **false** cuando se llama a `GetNextRows`.

## <a name="irowsetimplm_irowset"></a><a name="irowset"></a>IRowsetImpl:: m_iRowset

Índice del conjunto de filas que representa el cursor.

### <a name="syntax"></a>Sintaxis

```cpp
DBROWOFFSET m_iRowset;
```

## <a name="irowsetimplm_rgrowhandles"></a><a name="rgrowhandles"></a>IRowsetImpl:: m_rgRowHandles

Un mapa de identificadores de fila contenidos actualmente por el proveedor en respuesta a `GetNextRows`.

### <a name="syntax"></a>Sintaxis

```cpp
MapClass m_rgRowHandles;
```

### <a name="remarks"></a>Observaciones

Los identificadores de fila se quitan llamando a `ReleaseRows`. Vea la [información general de IRowsetImpl](../../data/oledb/irowsetimpl-class.md) para la definición de *MapClass*.

## <a name="see-also"></a>Consulte también

[Plantillas de proveedores OLE DB](../../data/oledb/ole-db-provider-templates-cpp.md)<br/>
[Arquitectura de plantillas de proveedores OLE DB](../../data/oledb/ole-db-provider-template-architecture.md)<br/>
[CSimpleRow (Clase)](../../data/oledb/csimplerow-class.md)