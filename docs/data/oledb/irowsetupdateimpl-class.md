---
title: IRowsetUpdateImpl (Clase)
ms.date: 11/04/2016
f1_keywords:
- IRowsetUpdateImpl
- ATL.IRowsetUpdateImpl
- ATL::IRowsetUpdateImpl
- IRowsetUpdateImpl::SetData
- IRowsetUpdateImpl.SetData
- ATL::IRowsetUpdateImpl::SetData
- ATL.IRowsetUpdateImpl.SetData
- ATL.IRowsetUpdateImpl.GetOriginalData
- IRowsetUpdateImpl.GetOriginalData
- ATL::IRowsetUpdateImpl::GetOriginalData
- IRowsetUpdateImpl::GetOriginalData
- IRowsetUpdateImpl::GetPendingRows
- GetPendingRows
- IRowsetUpdateImpl.GetPendingRows
- ATL::IRowsetUpdateImpl::GetPendingRows
- ATL.IRowsetUpdateImpl.GetPendingRows
- ATL.IRowsetUpdateImpl.GetRowStatus
- IRowsetUpdateImpl::GetRowStatus
- IRowsetUpdateImpl.GetRowStatus
- ATL::IRowsetUpdateImpl::GetRowStatus
- ATL.IRowsetUpdateImpl.Undo
- ATL::IRowsetUpdateImpl::Undo
- IRowsetUpdateImpl::Undo
- IRowsetUpdateImpl.Undo
- ATL::IRowsetUpdateImpl::Update
- IRowsetUpdateImpl::Update
- IRowsetUpdateImpl.Update
- ATL.IRowsetUpdateImpl.Update
- IRowsetUpdateImpl::IsUpdateAllowed
- IRowsetUpdateImpl.IsUpdateAllowed
- IsUpdateAllowed
- IRowsetUpdateImpl.m_mapCachedData
- IRowsetUpdateImpl::m_mapCachedData
- m_mapCachedData
helpviewer_keywords:
- providers, updatable
- IRowsetUpdateImpl class
- updatable providers, deferred update
- SetData method
- GetOriginalData method
- GetPendingRows method
- GetRowStatus method
- Undo method
- Update method
- IsUpdateAllowed method
- m_mapCachedData
ms.assetid: f85af76b-ab6f-4f8b-8f4a-337c9679d68f
ms.openlocfilehash: 6347a42b9065239f768c6b50c430946393358df1
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/14/2020
ms.locfileid: "81370744"
---
# <a name="irowsetupdateimpl-class"></a>IRowsetUpdateImpl (Clase)

La implementación de plantillas OLE DB de la [interfaz IRowsetUpdate.](/previous-versions/windows/desktop/ms714401(v=vs.85))

## <a name="syntax"></a>Sintaxis

```cpp
template <
   class T,
   class Storage,
   class UpdateArray = CAtlArray<Storage>,
   class RowClass = CSimpleRow,
   class MapClass = CAtlMap <RowClass::KeyType, RowClass*>
>

class IRowsetUpdateImpl : public IRowsetChangeImpl<
   T,
   Storage,
   IRowsetUpdate,
   RowClass,
   MapClass>
```

### <a name="parameters"></a>Parámetros

*T*<br/>
Una clase derivada `IRowsetUpdateImpl`de .

*Storage*<br/>
El registro de usuario.

*UpdateArray*<br/>
Matriz que contiene datos almacenados en caché para actualizar el conjunto de filas.

*RowClass*<br/>
La unidad de `HROW`almacenamiento para el archivo .

*MapClass*<br/>
La unidad de almacenamiento para todos los identificadores de fila mantenidos por el proveedor.

## <a name="requirements"></a>Requisitos

**Encabezado:** atldb.h

## <a name="members"></a>Miembros

### <a name="interface-methods-used-with-irowsetchange"></a>Métodos de interfaz (utilizados con IRowsetChange)

|||
|-|-|
|[Setdata](#setdata)|Establece los valores de datos en una o varias columnas.|

### <a name="interface-methods-used-with-irowsetupdate"></a>Métodos de interfaz (utilizados con IRowsetUpdate)

|||
|-|-|
|[GetOriginalData](#getoriginaldata)|Obtiene los datos transmitidos u obtenidos más recientemente del origen de datos, ignorando los cambios pendientes.|
|[GetPendingRows](#getpendingrows)|Devuelve una lista de filas con cambios pendientes.|
|[GetRowStatus](#getrowstatus)|Devuelve el estado de las filas especificadas.|
|[Deshacer](#undo)|Deshace los cambios realizados en la fila desde la última captura o actualización.|
|[Actualizar](#update)|Transmite los cambios realizados en la fila desde la última captura o actualización.|

### <a name="implementation-methods-callback"></a>Métodos de implementación (devolución de llamada)

|||
|-|-|
|[IsUpdateAllowed](#isupdateallowed)|Se utiliza para comprobar la seguridad, la integridad, etc. antes de permitir las actualizaciones.|

### <a name="data-members"></a>Miembros de datos

|||
|-|-|
|[m_mapCachedData](#mapcacheddata)|Contiene los datos originales de la operación diferida.|

## <a name="remarks"></a>Observaciones

Primero debe leer y comprender la documentación de [IRowsetChange](/previous-versions/windows/desktop/ms715790(v=vs.85)), porque todo lo que se describe allí también se aplica aquí. También debe leer el capítulo 6 de la *referencia del programador OLE DB* sobre la configuración de datos.

`IRowsetUpdateImpl`implementa la interfaz OLE DB, `IRowsetUpdate` que permite a los `IRowsetChange` consumidores retrasar la transmisión de los cambios realizados con el origen de datos y deshacer los cambios antes de la transmisión.

> [!IMPORTANT]
> Se recomienda encarecidamente que lea la siguiente documentación ANTES de intentar implementar el proveedor:

- [Creación de un proveedor actualizable](../../data/oledb/creating-an-updatable-provider.md)

- Capítulo 6 de la *referencia del programador OLE DB*

- Vea también `RUpdateRowset` cómo se utiliza la clase en el ejemplo [UpdatePV](https://github.com/Microsoft/VCSamples/tree/master/VC2010Samples/ATL/OLEDB/Provider/UPDATEPV)

## <a name="irowsetupdateimplsetdata"></a><a name="setdata"></a>IRowsetUpdateImpl::SetData

Establece los valores de datos en una o varias columnas.

### <a name="syntax"></a>Sintaxis

```cpp
STDMETHOD (SetData )(HROW hRow,
   HACCESSOR hAccessor,
   void* pSrcData);
```

#### <a name="parameters"></a>Parámetros

Vea [IRowsetChange::SetData](/previous-versions/windows/desktop/ms721232(v=vs.85)) en la *referencia del programador OLE DB*.

### <a name="remarks"></a>Observaciones

Este método reemplaza el [método IRowsetChangeImpl::SetData,](../../data/oledb/irowsetchangeimpl-setdata.md) pero incluye el almacenamiento en caché de los datos originales para permitir el procesamiento inmediato o diferido de la operación.

## <a name="irowsetupdateimplgetoriginaldata"></a><a name="getoriginaldata"></a>IRowsetUpdateImpl::GetOriginalData

Obtiene los datos transmitidos u obtenidos más recientemente del origen de datos, ignorando los cambios pendientes.

### <a name="syntax"></a>Sintaxis

```cpp
STDMETHOD (GetOriginalData )(HROW hRow,
   HACCESSOR hAccessor,
   void* pData);
```

#### <a name="parameters"></a>Parámetros

Vea [IRowsetUpdate::GetOriginalData](/previous-versions/windows/desktop/ms709947(v=vs.85)) en la *referencia del programador OLE DB*.

## <a name="irowsetupdateimplgetpendingrows"></a><a name="getpendingrows"></a>IRowsetUpdateImpl::GetPendingRows

Devuelve una lista de filas con cambios pendientes.

### <a name="syntax"></a>Sintaxis

```cpp
STDMETHOD (GetPendingRows )(HCHAPTER /* hReserved */,
   DBPENDINGSTATUS dwRowStatus,
   DBCOUNTITEM* pcPendingRows,
   HROW** prgPendingRows,
   DBPENDINGSTATUS** prgPendingStatus);
```

#### <a name="parameters"></a>Parámetros

*hReservado*<br/>
[en] Corresponde al parámetro *hChapter* en [IRowsetUpdate::GetPendingRows](/previous-versions/windows/desktop/ms719626(v=vs.85)).

Para otros parámetros, vea [IRowsetUpdate::GetPendingRows](/previous-versions/windows/desktop/ms719626(v=vs.85)) en la *referencia del programador OLE DB*.

### <a name="remarks"></a>Observaciones

Para obtener más información, vea [IRowsetUpdate::GetPendingRows](/previous-versions/windows/desktop/ms719626(v=vs.85)) en la *referencia del programador OLE DB*.

## <a name="irowsetupdateimplgetrowstatus"></a><a name="getrowstatus"></a>IRowsetUpdateImpl::GetRowStatus

Devuelve el estado de las filas especificadas.

### <a name="syntax"></a>Sintaxis

```cpp
STDMETHOD (GetRowStatus )(HCHAPTER /* hReserved */,
   DBCOUNTITEM cRows,
   const HROW rghRows[],
   DBPENDINGSTATUS rgPendingStatus[]);
```

#### <a name="parameters"></a>Parámetros

*hReservado*<br/>
[en] Corresponde al parámetro *hChapter* de [IRowsetUpdate::GetRowStatus](/previous-versions/windows/desktop/ms724377(v=vs.85)).

Para otros parámetros, vea [IRowsetUpdate::GetRowStatus](/previous-versions/windows/desktop/ms724377(v=vs.85)) en la *referencia del programador OLE DB*.

## <a name="irowsetupdateimplundo"></a><a name="undo"></a>IRowsetUpdateImpl::Deshacer

Deshace los cambios realizados en la fila desde la última captura o actualización.

### <a name="syntax"></a>Sintaxis

```cpp
STDMETHOD (Undo )(HCHAPTER /* hReserved */,
   DBCOUNTITEM cRows,
   const HROW rghRows[ ],
   DBCOUNTITEM* pcRowsUndone,
   HROW** prgRowsUndone,
   DBROWSTATUS** prgRowStatus);
```

#### <a name="parameters"></a>Parámetros

*hReservado*<br/>
[en] Corresponde al parámetro *hChapter* en [IRowsetUpdate::Undo](/previous-versions/windows/desktop/ms719655(v=vs.85)).

*pcRowsUndone*<br/>
[fuera] Corresponde al parámetro *pcRows* en [IRowsetUpdate::Undo](/previous-versions/windows/desktop/ms719655(v=vs.85)).

*prgRowsUndone*<br/>
[en] Corresponde al parámetro *prgRows* en [IRowsetUpdate::Undo](/previous-versions/windows/desktop/ms719655(v=vs.85)).

Para otros parámetros, vea [IRowsetUpdate::Undo](/previous-versions/windows/desktop/ms719655(v=vs.85)) en la *referencia del programador OLE DB*.

## <a name="irowsetupdateimplupdate"></a><a name="update"></a>IRowsetUpdateImpl::Update

Transmite los cambios realizados en la fila desde la última captura o actualización.

### <a name="syntax"></a>Sintaxis

```cpp
STDMETHOD (Update )(HCHAPTER /* hReserved */,
   DBCOUNTITEM cRows,
   const HROW rghRows[],
   DBCOUNTITEM* pcRows,
   HROW** prgRows,
   DBROWSTATUS** prgRowStatus);
```

#### <a name="parameters"></a>Parámetros

*hReservado*<br/>
[en] Corresponde al parámetro *hChapter* en [IRowsetUpdate::Update](/previous-versions/windows/desktop/ms719709(v=vs.85)).

Para otros parámetros, vea [IRowsetUpdate::Update](/previous-versions/windows/desktop/ms719709(v=vs.85)) en la *referencia del programador OLE DB*.

### <a name="remarks"></a>Observaciones

Los cambios se transmiten llamando a [IRowsetChangeImpl::FlushData](../../data/oledb/irowsetchangeimpl-flushdata.md). El consumidor debe llamar a [CRowset::Update](../../data/oledb/crowset-update.md) para que los cambios surtan efecto. Establezca *prgRowstatus* en un valor adecuado como se describe en [Estados de fila](/previous-versions/windows/desktop/ms722752(v=vs.85)) en la referencia del programador OLE *DB*.

## <a name="irowsetupdateimplisupdateallowed"></a><a name="isupdateallowed"></a>IRowsetUpdateImpl::IsUpdateAllowed

Invalide este método para comprobar la seguridad, la integridad, etc. antes de las actualizaciones.

### <a name="syntax"></a>Sintaxis

```cpp
HRESULT IsUpdateAllowed(DBPENDINGSTATUS /* [in] */ /* status */,
   HROW /* [in] */ /* hRowUpdate */,
   DBROWSTATUS* /* [out] */ /* pRowStatus */);
```

#### <a name="parameters"></a>Parámetros

*status*<br/>
[en] El estado de las operaciones pendientes en las filas.

*hRowUpdate*<br/>
[en] Control de las filas que el usuario desea actualizar.

*pRowStatus*<br/>
[fuera] El estado devuelto al usuario.

### <a name="remarks"></a>Observaciones

Si determina que se debe permitir una actualización, devuelve S_OK; de lo contrario E_FAIL devoluciones. Si permite una actualización, también debe `DBROWSTATUS` establecer en [IRowsetUpdateImpl::Update](../../data/oledb/irowsetupdateimpl-update.md) en un estado de [fila](/previous-versions/windows/desktop/ms722752(v=vs.85))adecuado.

## <a name="irowsetupdateimplm_mapcacheddata"></a><a name="mapcacheddata"></a>IRowsetUpdateImpl::m_mapCachedData

Mapa que contiene los datos originales de la operación diferida.

### <a name="syntax"></a>Sintaxis

```cpp
CAtlMap<
   HROW hRow,
   Storage* pData
>
m_mapCachedData;
```

#### <a name="parameters"></a>Parámetros

*hRow*<br/>
Controle las filas de los datos.

*pData*<br/>
Puntero a los datos que se van a almacenar en caché. Los datos son de tipo *Storage* (la clase de registro de usuario). Consulte el argumento Plantilla de *almacenamiento* en [IRowsetUpdateImpl (Clase).](../../data/oledb/irowsetupdateimpl-class.md)

## <a name="see-also"></a>Consulte también

[Plantillas de proveedores OLE DB](../../data/oledb/ole-db-provider-templates-cpp.md)<br/>
[Arquitectura de plantillas de proveedor OLE DB](../../data/oledb/ole-db-provider-template-architecture.md)<br/>
[Creación de un proveedor actualizable](../../data/oledb/creating-an-updatable-provider.md)
