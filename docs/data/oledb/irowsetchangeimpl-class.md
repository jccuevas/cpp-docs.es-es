---
title: IRowsetChangeImpl (Clase)
ms.date: 11/04/2016
f1_keywords:
- ATL::IRowsetChangeImpl
- IRowsetChangeImpl
- ATL.IRowsetChangeImpl
- ATL.IRowsetChangeImpl.DeleteRows
- ATL::IRowsetChangeImpl::DeleteRows
- IRowsetChangeImpl.DeleteRows
- DeleteRows
- IRowsetChangeImpl::DeleteRows
- ATL.IRowsetChangeImpl.InsertRow
- InsertRow
- IRowsetChangeImpl.InsertRow
- ATL::IRowsetChangeImpl::InsertRow
- IRowsetChangeImpl::InsertRow
- IRowsetChangeImpl::SetData
- ATL.IRowsetChangeImpl.SetData
- IRowsetChangeImpl.SetData
- ATL::IRowsetChangeImpl::SetData
- IRowsetChangeImpl::FlushData
- IRowsetChangeImpl.FlushData
- FlushData
helpviewer_keywords:
- providers, updatable
- updatable providers, immediate update
- IRowsetChangeImpl class
- DeleteRows method
- InsertRow method
- SetData method
- FlushData method
ms.assetid: 1e9fee15-ed9e-4387-af8f-215569beca6c
ms.openlocfilehash: ae4ceea53ec91cc3f9593dd3789fcf61e0702274
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/14/2020
ms.locfileid: "81376947"
---
# <a name="irowsetchangeimpl-class"></a>IRowsetChangeImpl (Clase)

La implementación de plantillas OLE DB de la [interfaz IRowsetChange](/previous-versions/windows/desktop/ms715790(v=vs.85)) en la especificación OLE DB.

## <a name="syntax"></a>Sintaxis

```cpp
template <
   class T,
   class Storage,
   class BaseInterface = IRowsetChange,
   class RowClass = CSimpleRow,
   class MapClass = CAtlMap <RowClass::KeyType, RowClass*>>
class ATL_NO_VTABLE IRowsetChangeImpl : public BaseInterface
```

### <a name="parameters"></a>Parámetros

*T*<br/>
Una clase derivada `IRowsetChangeImpl`de .

*Storage*<br/>
El registro de usuario.

*BaseInterface*<br/>
La clase base para la `IRowsetChange`interfaz, como .

*RowClass*<br/>
La unidad de almacenamiento para el asa de fila.

*MapClass*<br/>
La unidad de almacenamiento para todos los identificadores de fila mantenidos por el proveedor.

## <a name="requirements"></a>Requisitos

**Encabezado:** atldb.h

## <a name="members"></a>Miembros

### <a name="interface-methods-used-with-irowsetchange"></a>Métodos de interfaz (utilizados con IRowsetChange)

|||
|-|-|
|[DeleteRows](#deleterows)|Elimina filas del conjunto de filas.|
|[InsertRow](#insertrow)|Inserta una fila en el conjunto de filas.|
|[Setdata](#setdata)|Establece los valores de datos en una o varias columnas.|

### <a name="implementation-method-callback"></a>Método Implementation (Callback)

|||
|-|-|
|[FlushData](#flushdata)|Reemplazado por el proveedor para confirmar datos en su almacén.|

## <a name="remarks"></a>Observaciones

Esta interfaz es responsable de las operaciones de escritura inmediatas en un almacén de datos. "Inmediato" significa que cuando el usuario final (la persona que utiliza el consumidor) realiza cambios, esos cambios se transmiten inmediatamente al almacén de datos (y no se pueden deshacer).

`IRowsetChangeImpl`implementa la interfaz OLE DB, `IRowsetChange` que permite actualizar los valores de las columnas en las filas existentes, eliminar filas e insertar nuevas filas.

La implementación de plantillas OLE`SetData`DB `InsertRow`admite `DeleteRows`todos los métodos base ( , , y ).

> [!IMPORTANT]
> Se recomienda encarecidamente que lea la siguiente documentación ANTES de intentar implementar el proveedor:

- [Creación de un proveedor actualizable](../../data/oledb/creating-an-updatable-provider.md)

- Capítulo 6 de la *referencia del programador OLE DB*

- Vea también `RUpdateRowset` cómo se utiliza la clase en el ejemplo [UpdatePV.](https://github.com/Microsoft/VCSamples/tree/master/VC2010Samples/ATL/OLEDB/Provider/UPDATEPV)

## <a name="irowsetchangeimpldeleterows"></a><a name="deleterows"></a>IRowsetChangeImpl::DeleteRows

Elimina filas del conjunto de filas.

### <a name="syntax"></a>Sintaxis

```cpp
STDMETHOD (DeleteRows )(HCHAPTER /* hReserved */,
   DBCOUNTITEM cRows,
   const HROW rghRows[],
   DBROWSTATUS rgRowStatus[]);
```

#### <a name="parameters"></a>Parámetros

Vea [IRowsetChange::DeleteRows](/previous-versions/windows/desktop/ms724362(v=vs.85)) en la *referencia del programador OLE DB*.

## <a name="irowsetchangeimplinsertrow"></a><a name="insertrow"></a>IRowsetChangeImpl::InsertRow

Crea e inicializa una nueva fila en el conjunto de filas.

### <a name="syntax"></a>Sintaxis

```cpp
STDMETHOD (InsertRow )(HCHAPTER /* hReserved */,
   HACCESSOR hAccessor,
   void* pData,
   HROW* phRow);
```

#### <a name="parameters"></a>Parámetros

Vea [IRowsetChange::InsertRow](/previous-versions/windows/desktop/ms716921(v=vs.85)) en la *referencia del programador OLE DB*.

## <a name="irowsetchangeimplsetdata"></a><a name="setdata"></a>IRowsetChangeImpl::SetData

Establece los valores de datos en una o varias columnas.

### <a name="syntax"></a>Sintaxis

```cpp
STDMETHOD (SetData )(HROW hRow,
   HACCESSOR hAccessor,
   void* pSrcData);
```

#### <a name="parameters"></a>Parámetros

Vea [IRowsetChange::SetData](/previous-versions/windows/desktop/ms721232(v=vs.85)) en la *referencia del programador OLE DB*.

## <a name="irowsetchangeimplflushdata"></a><a name="flushdata"></a>IRowsetChangeImpl::FlushData

Reemplazado por el proveedor para confirmar datos en su almacén.

### <a name="syntax"></a>Sintaxis

```cpp
HRESULT FlushData(HROW hRowToFlush,
   HACCESSOR hAccessorToFlush);
```

#### <a name="parameters"></a>Parámetros

*hRowToFlush*<br/>
[en] Controle las filas de los datos. El tipo de esta fila se determina a `IRowsetImpl` partir`CSimpleRow` del argumento de plantilla *RowClass* de la clase (de forma predeterminada).

*hAccessorToFlush*<br/>
[en] Controlar el descriptor de acceso, que contiene `PROVIDER_MAP` información de enlace e información de tipo en su (consulte [IAccessorImpl](../../data/oledb/iaccessorimpl-class.md)).

### <a name="return-value"></a>Valor devuelto

Un HRESULT estándar.

## <a name="see-also"></a>Consulte también

[Plantillas de proveedores OLE DB](../../data/oledb/ole-db-provider-templates-cpp.md)<br/>
[Arquitectura de plantillas de proveedor OLE DB](../../data/oledb/ole-db-provider-template-architecture.md)
