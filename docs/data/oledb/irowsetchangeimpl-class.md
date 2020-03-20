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
ms.openlocfilehash: 1e07289a2d0fb283a20657797db5f915c06a39ad
ms.sourcegitcommit: 63784729604aaf526de21f6c6b62813882af930a
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 03/17/2020
ms.locfileid: "79545904"
---
# <a name="irowsetchangeimpl-class"></a>IRowsetChangeImpl (Clase)

La implementación de las plantillas de OLE DB de la interfaz [IRowsetChange](/previous-versions/windows/desktop/ms715790(v=vs.85)) en la especificación de OLE DB.

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
Una clase derivada de `IRowsetChangeImpl`.

*Storage*<br/>
Registro de usuario.

*BaseInterface*<br/>
La clase base de la interfaz, como `IRowsetChange`.

*RowClass*<br/>
Unidad de almacenamiento para el identificador de fila.

*MapClass*<br/>
Unidad de almacenamiento para todos los identificadores de fila retenidos por el proveedor.

## <a name="requirements"></a>Requisitos

**Encabezado:** atldb.h

## <a name="members"></a>Members

### <a name="interface-methods-used-with-irowsetchange"></a>Métodos de interfaz (usados con IRowsetChange)

|||
|-|-|
|[DeleteRows](#deleterows)|Elimina filas del conjunto de filas.|
|[InsertRow](#insertrow)|Inserta una fila en el conjunto de filas.|
|[SetData](#setdata)|Establece los valores de datos en una o varias columnas.|

### <a name="implementation-method-callback"></a>Método de implementación (devolución de llamada)

|||
|-|-|
|[FlushData](#flushdata)|Invalidado por el proveedor para confirmar los datos en su almacén.|

## <a name="remarks"></a>Observaciones

Esta interfaz es responsable de las operaciones de escritura inmediatas en un almacén de datos. "Inmediato" significa que cuando el usuario final (la persona que usa el consumidor) realiza cualquier cambio, esos cambios se transmiten inmediatamente al almacén de datos (y no se pueden deshacer).

`IRowsetChangeImpl` implementa la interfaz `IRowsetChange` OLE DB, que permite actualizar los valores de las columnas de las filas existentes, eliminar filas e insertar nuevas filas.

La implementación de las plantillas de OLE DB admite todos los métodos base (`SetData`, `InsertRow`y `DeleteRows`).

> [!IMPORTANT]
>  Se recomienda encarecidamente que lea la siguiente documentación antes de intentar implementar el proveedor:

- [Crear un proveedor actualizable](../../data/oledb/creating-an-updatable-provider.md)

- Capítulo 6 de la *Referencia del programador de OLE DB*

- Vea también cómo se usa la clase `RUpdateRowset` en el ejemplo [UpdatePV](https://github.com/Microsoft/VCSamples/tree/master/VC2010Samples/ATL/OLEDB/Provider/UPDATEPV) .

## <a name="irowsetchangeimpldeleterows"></a><a name="deleterows"></a>IRowsetChangeImpl::D eleteRows

Elimina filas del conjunto de filas.

### <a name="syntax"></a>Sintaxis

```cpp
STDMETHOD (DeleteRows )(HCHAPTER /* hReserved */,
   DBCOUNTITEM cRows,
   const HROW rghRows[],
   DBROWSTATUS rgRowStatus[]);
```

#### <a name="parameters"></a>Parámetros

Vea [IRowsetChange::D eleterows](/previous-versions/windows/desktop/ms724362(v=vs.85)) en la *Referencia del programador de OLE DB*.

## <a name="irowsetchangeimplinsertrow"></a><a name="insertrow"></a>IRowsetChangeImpl:: InsertRow

Crea e inicializa una nueva fila en el conjunto de filas.

### <a name="syntax"></a>Sintaxis

```cpp
STDMETHOD (InsertRow )(HCHAPTER /* hReserved */,
   HACCESSOR hAccessor,
   void* pData,
   HROW* phRow);
```

#### <a name="parameters"></a>Parámetros

Vea [IRowsetChange:: InsertRow](/previous-versions/windows/desktop/ms716921(v=vs.85)) en la *Referencia del programador de OLE DB*.

## <a name="irowsetchangeimplsetdata"></a><a name="setdata"></a>IRowsetChangeImpl:: SetData

Establece los valores de datos en una o varias columnas.

### <a name="syntax"></a>Sintaxis

```cpp
STDMETHOD (SetData )(HROW hRow,
   HACCESSOR hAccessor,
   void* pSrcData);
```

#### <a name="parameters"></a>Parámetros

Vea [IRowsetChange:: SetData](/previous-versions/windows/desktop/ms721232(v=vs.85)) en la *Referencia del programador de OLE DB*.

## <a name="irowsetchangeimplflushdata"></a><a name="flushdata"></a>IRowsetChangeImpl:: FlushData

Invalidado por el proveedor para confirmar los datos en su almacén.

### <a name="syntax"></a>Sintaxis

```cpp
HRESULT FlushData(HROW hRowToFlush,
   HACCESSOR hAccessorToFlush);
```

#### <a name="parameters"></a>Parámetros

*hRowToFlush*<br/>
de Identificador de las filas de los datos. El tipo de esta fila se determina a partir del argumento de plantilla *RowClass* de la clase `IRowsetImpl` (`CSimpleRow` de forma predeterminada).

*hAccessorToFlush*<br/>
de Identificador del descriptor de acceso, que contiene información de enlace e información de tipo en su `PROVIDER_MAP` (vea [IAccessorImpl](../../data/oledb/iaccessorimpl-class.md)).

### <a name="return-value"></a>Valor devuelto

HRESULT estándar.

## <a name="see-also"></a>Consulte también

[Plantillas de proveedores OLE DB](../../data/oledb/ole-db-provider-templates-cpp.md)<br/>
[Arquitectura de plantillas de proveedores OLE DB](../../data/oledb/ole-db-provider-template-architecture.md)