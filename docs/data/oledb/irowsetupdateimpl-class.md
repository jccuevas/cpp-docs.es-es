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
ms.openlocfilehash: dba962c761fac0408a3c68a46ec6447aa7832522
ms.sourcegitcommit: 63784729604aaf526de21f6c6b62813882af930a
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 03/17/2020
ms.locfileid: "79545724"
---
# <a name="irowsetupdateimpl-class"></a>IRowsetUpdateImpl (Clase)

La implementación de las plantillas de OLE DB de la interfaz [IRowsetUpdate](/previous-versions/windows/desktop/ms714401(v=vs.85)) .

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
Una clase derivada de `IRowsetUpdateImpl`.

*Storage*<br/>
Registro de usuario.

*UpdateArray*<br/>
Una matriz que contiene los datos en caché para actualizar el conjunto de filas.

*RowClass*<br/>
Unidad de almacenamiento para el `HROW`.

*MapClass*<br/>
Unidad de almacenamiento para todos los identificadores de fila retenidos por el proveedor.

## <a name="requirements"></a>Requisitos

**Encabezado:** atldb.h

## <a name="members"></a>Members

### <a name="interface-methods-used-with-irowsetchange"></a>Métodos de interfaz (usados con IRowsetChange)

|||
|-|-|
|[SetData](#setdata)|Establece los valores de datos en una o varias columnas.|

### <a name="interface-methods-used-with-irowsetupdate"></a>Métodos de interfaz (usados con IRowsetUpdate)

|||
|-|-|
|[GetOriginalData](#getoriginaldata)|Obtiene los datos transmitidos más recientemente o obtenidos del origen de datos, omitiendo los cambios pendientes.|
|[GetPendingRows](#getpendingrows)|Devuelve una lista de filas con cambios pendientes.|
|[GetRowStatus](#getrowstatus)|Devuelve el estado de las filas especificadas.|
|[Deshacer](#undo)|Deshace los cambios realizados en la fila desde la última vez que se recuperó o se actualizó la actualización.|
|[Actualizar](#update)|Transmite cualquier cambio realizado en la fila desde la última recuperación o actualización.|

### <a name="implementation-methods-callback"></a>Métodos de implementación (devolución de llamada)

|||
|-|-|
|[IsUpdateAllowed](#isupdateallowed)|Se utiliza para comprobar la seguridad, la integridad, etc. antes de permitir las actualizaciones.|

### <a name="data-members"></a>Miembros de datos

|||
|-|-|
|[m_mapCachedData](#mapcacheddata)|Contiene los datos originales de la operación diferida.|

## <a name="remarks"></a>Observaciones

Primero debe leer y comprender la documentación de [IRowsetChange](/previous-versions/windows/desktop/ms715790(v=vs.85)), ya que todo lo que se describe aquí también se aplica aquí. También debe leer el capítulo 6 de la *Referencia del programador de OLE DB* sobre la configuración de los datos.

`IRowsetUpdateImpl` implementa la interfaz `IRowsetUpdate` OLE DB, que permite a los consumidores retrasar la transmisión de los cambios realizados con `IRowsetChange` al origen de datos y deshacer los cambios antes de la transmisión.

> [!IMPORTANT]
>  Se recomienda encarecidamente que lea la siguiente documentación antes de intentar implementar el proveedor:

- [Crear un proveedor actualizable](../../data/oledb/creating-an-updatable-provider.md)

- Capítulo 6 de la *Referencia del programador de OLE DB*

- Vea también cómo se usa la clase `RUpdateRowset` en el ejemplo [UpdatePV](https://github.com/Microsoft/VCSamples/tree/master/VC2010Samples/ATL/OLEDB/Provider/UPDATEPV) .

## <a name="irowsetupdateimplsetdata"></a><a name="setdata"></a>IRowsetUpdateImpl:: SetData

Establece los valores de datos en una o varias columnas.

### <a name="syntax"></a>Sintaxis

```cpp
STDMETHOD (SetData )(HROW hRow,
   HACCESSOR hAccessor,
   void* pSrcData);
```

#### <a name="parameters"></a>Parámetros

Vea [IRowsetChange:: SetData](/previous-versions/windows/desktop/ms721232(v=vs.85)) en la *Referencia del programador de OLE DB*.

### <a name="remarks"></a>Observaciones

Este método invalida el método [IRowsetChangeImpl:: SetData](../../data/oledb/irowsetchangeimpl-setdata.md) , pero incluye el almacenamiento en caché de los datos originales para permitir el procesamiento inmediato o aplazado de la operación.

## <a name="irowsetupdateimplgetoriginaldata"></a><a name="getoriginaldata"></a>IRowsetUpdateImpl:: GetOriginalData

Obtiene los datos transmitidos más recientemente o obtenidos del origen de datos, omitiendo los cambios pendientes.

### <a name="syntax"></a>Sintaxis

```cpp
STDMETHOD (GetOriginalData )(HROW hRow,
   HACCESSOR hAccessor,
   void* pData);
```

#### <a name="parameters"></a>Parámetros

Vea [IRowsetUpdate:: GetOriginalData](/previous-versions/windows/desktop/ms709947(v=vs.85)) en la *Referencia del programador de OLE DB*.

## <a name="irowsetupdateimplgetpendingrows"></a><a name="getpendingrows"></a>IRowsetUpdateImpl:: GetPendingRows

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

*hReserved*<br/>
de Corresponde al parámetro *hChapter* de [IRowsetUpdate:: GetPendingRows](/previous-versions/windows/desktop/ms719626(v=vs.85)).

Para otros parámetros, vea [IRowsetUpdate:: GetPendingRows](/previous-versions/windows/desktop/ms719626(v=vs.85)) en la *Referencia del programador de OLE DB*.

### <a name="remarks"></a>Observaciones

Para obtener más información, vea [IRowsetUpdate:: GetPendingRows](/previous-versions/windows/desktop/ms719626(v=vs.85)) en la *Referencia del programador de OLE DB*.

## <a name="irowsetupdateimplgetrowstatus"></a><a name="getrowstatus"></a>IRowsetUpdateImpl:: GetRowStatus

Devuelve el estado de las filas especificadas.

### <a name="syntax"></a>Sintaxis

```cpp
STDMETHOD (GetRowStatus )(HCHAPTER /* hReserved */,
   DBCOUNTITEM cRows,
   const HROW rghRows[],
   DBPENDINGSTATUS rgPendingStatus[]);
```

#### <a name="parameters"></a>Parámetros

*hReserved*<br/>
de Corresponde al parámetro *hChapter* de [IRowsetUpdate:: GetRowStatus](/previous-versions/windows/desktop/ms724377(v=vs.85)).

Para otros parámetros, vea [IRowsetUpdate:: GetRowStatus](/previous-versions/windows/desktop/ms724377(v=vs.85)) en la *Referencia del programador de OLE DB*.

## <a name="irowsetupdateimplundo"></a><a name="undo"></a>IRowsetUpdateImpl:: Undo

Deshace los cambios realizados en la fila desde la última vez que se recuperó o se actualizó la actualización.

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

*hReserved*<br/>
de Corresponde al parámetro *hChapter* de [IRowsetUpdate:: Undo](/previous-versions/windows/desktop/ms719655(v=vs.85)).

*pcRowsUndone*<br/>
enuncia Corresponde al parámetro *pcRows* de [IRowsetUpdate:: Undo](/previous-versions/windows/desktop/ms719655(v=vs.85)).

*prgRowsUndone*<br/>
de Corresponde al parámetro *prgRows* de [IRowsetUpdate:: Undo](/previous-versions/windows/desktop/ms719655(v=vs.85)).

Para otros parámetros, vea [IRowsetUpdate:: Undo](/previous-versions/windows/desktop/ms719655(v=vs.85)) en la *Referencia del programador de OLE DB*.

## <a name="irowsetupdateimplupdate"></a><a name="update"></a>IRowsetUpdateImpl:: Update

Transmite cualquier cambio realizado en la fila desde la última recuperación o actualización.

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

*hReserved*<br/>
de Corresponde al parámetro *hChapter* de [IRowsetUpdate:: Update](/previous-versions/windows/desktop/ms719709(v=vs.85)).

Para otros parámetros, vea [IRowsetUpdate:: Update](/previous-versions/windows/desktop/ms719709(v=vs.85)) en la *Referencia del programador de OLE DB*.

### <a name="remarks"></a>Observaciones

Los cambios se transmiten llamando a [IRowsetChangeImpl:: FlushData](../../data/oledb/irowsetchangeimpl-flushdata.md). El consumidor debe llamar a [CRowset:: Update](../../data/oledb/crowset-update.md) para que los cambios surtan efecto. Establezca *prgRowstatus* en un valor adecuado, tal como se describe en [Estados de fila](/previous-versions/windows/desktop/ms722752(v=vs.85)) en la *Referencia del programador de OLE DB*.

## <a name="irowsetupdateimplisupdateallowed"></a><a name="isupdateallowed"></a>IRowsetUpdateImpl:: IsUpdateAllowed

Invalide este método para comprobar la seguridad, la integridad, etc. antes de las actualizaciones.

### <a name="syntax"></a>Sintaxis

```cpp
HRESULT IsUpdateAllowed(DBPENDINGSTATUS /* [in] */ /* status */,
   HROW /* [in] */ /* hRowUpdate */,
   DBROWSTATUS* /* [out] */ /* pRowStatus */);
```

#### <a name="parameters"></a>Parámetros

*status*<br/>
de Estado de las operaciones pendientes en las filas.

*hRowUpdate*<br/>
de Identificador de las filas que el usuario desea actualizar.

*pRowStatus*<br/>
enuncia El estado devuelto al usuario.

### <a name="remarks"></a>Observaciones

Si determina que se debe permitir una actualización, Devuelve S_OK; de lo contrario, devuelve E_FAIL. Si permite una actualización, también debe establecer el `DBROWSTATUS` en [IRowsetUpdateImpl:: Update](../../data/oledb/irowsetupdateimpl-update.md) en un [Estado de fila](/previous-versions/windows/desktop/ms722752(v=vs.85))adecuado.

## <a name="irowsetupdateimplm_mapcacheddata"></a><a name="mapcacheddata"></a>IRowsetUpdateImpl:: m_mapCachedData

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
Identificador de las filas de los datos.

*pData*<br/>
Puntero a los datos que se van a almacenar en caché. Los datos son de tipo *Storage* (clase de registro de usuario). Vea el argumento de plantilla de *almacenamiento* en la [clase IRowsetUpdateImpl](../../data/oledb/irowsetupdateimpl-class.md).

## <a name="see-also"></a>Consulte también

[Plantillas de proveedores OLE DB](../../data/oledb/ole-db-provider-templates-cpp.md)<br/>
[Arquitectura de plantillas de proveedores OLE DB](../../data/oledb/ole-db-provider-template-architecture.md)<br/>
[Crear un proveedor actualizable](../../data/oledb/creating-an-updatable-provider.md)