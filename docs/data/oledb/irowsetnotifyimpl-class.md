---
title: IRowsetNotifyImpl (Clase)
ms.date: 11/04/2016
f1_keywords:
- ATL.IRowsetNotifyImpl
- ATL::IRowsetNotifyImpl
- IRowsetNotifyImpl
- IRowsetNotifyImpl.OnFieldChange
- IRowsetNotifyImpl::OnFieldChange
- OnFieldChange
- IRowsetNotifyImpl::OnRowChange
- IRowsetNotifyImpl.OnRowChange
- OnRowChange
- OnRowsetChange
- IRowsetNotifyImpl::OnRowsetChange
- IRowsetNotifyImpl.OnRowsetChange
helpviewer_keywords:
- IRowsetNotifyImpl class
- OnFieldChange method
- OnRowChange method
- OnRowsetChange method
ms.assetid: fbfd0cb2-38ff-4b42-899a-8de902f834b8
ms.openlocfilehash: 4e6b4c3298c063038e7365496f26f50d3789be86
ms.sourcegitcommit: 0e3da5cea44437c132b5c2ea522bd229ea000a10
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 07/12/2019
ms.locfileid: "79544445"
---
# <a name="irowsetnotifyimpl-class"></a>IRowsetNotifyImpl (Clase)

Implementa y registra [IRowsetNotify](/previous-versions/windows/desktop/ms712959(v=vs.85)) en el consumidor (también conocido como "receptor") para que pueda controlar las notificaciones.

## <a name="syntax"></a>Sintaxis

```cpp
class ATL_NO_VTABLE IRowsetNotifyImpl : public IRowsetNotify
```

## <a name="requirements"></a>Requisitos

**Encabezado:** atldbcli.h

## <a name="members"></a>Members

### <a name="methods"></a>Métodos

|||
|-|-|
|[OnFieldChange](#onfieldchange)|Notifica al consumidor cualquier cambio en el valor de una columna.|
|[OnRowChange](#onrowchange)|Notifica al consumidor el primer cambio en una fila o cualquier cambio que afecte a la fila completa.|
|[OnRowsetChange](#onrowsetchange)|Notifica al consumidor cualquier cambio que afecte al conjunto de filas completo.|

## <a name="remarks"></a>Observaciones

Vea [recibir notificaciones](../../data/oledb/receiving-notifications.md) sobre la implementación de la interfaz de punto de conexión en el consumidor.

`IRowsetNotifyImpl` proporciona una implementación ficticia para `IRowsetNotify`, con funciones vacías para los métodos de `IRowsetNotify` [OnFieldChange](/previous-versions/windows/desktop/ms715961(v=vs.85)), [OnRowChange](/previous-versions/windows/desktop/ms722694(v=vs.85))y [OnRowsetChange](/previous-versions/windows/desktop/ms722669(v=vs.85)). Si hereda de esta clase al implementar una interfaz `IRowsetNotify`, solo puede implementar los métodos que necesite. También debe proporcionar implementaciones vacías para los demás métodos.

## <a name="irowsetnotifyimplonfieldchange"></a><a name="onfieldchange"></a>Irowsetnotifyimpl (:: OnFieldChange

Notifica al consumidor cualquier cambio en el valor de una columna.

### <a name="syntax"></a>Sintaxis

```cpp
STDMETHOD(OnFieldChange)(
/* [in] */ IRowset* /* pRowset */,
/* [in] */ HROW /* hRow */,
/* [in] */ DBORDINAL /* cColumns */,
/* [size_is][in] */ DBORDINAL /* rgColumns */ [] ,
/* [in] */ DBREASON /* eReason */,
/* [in] */ DBEVENTPHASE /* ePhase */,
/* [in] */ BOOL /* fCantDeny */)
```

#### <a name="parameters"></a>Parámetros

Vea [IRowsetNotify:: OnFieldChange](/previous-versions/windows/desktop/ms715961(v=vs.85)) para obtener descripciones de los parámetros.

### <a name="return-value"></a>Valor devuelto

Vea [IRowsetNotify:: OnFieldChange](/previous-versions/windows/desktop/ms715961(v=vs.85)) para obtener descripciones de valores devueltos.

### <a name="remarks"></a>Observaciones

Este método encapsula el método [IRowsetNotify:: OnFieldChange](/previous-versions/windows/desktop/ms715961(v=vs.85)) . Vea la descripción del método en la referencia del programador de OLE DB para obtener más información.

## <a name="irowsetnotifyimplonrowchange"></a><a name="onrowchange"></a>Irowsetnotifyimpl (:: OnRowChange

Notifica al consumidor el primer cambio en una fila o cualquier cambio que afecte a la fila completa.

### <a name="syntax"></a>Sintaxis

```cpp
STDMETHOD(OnRowChange)(
/* [in] */ IRowset* /* pRowset */,
/* [in] */ DBCOUNTITEM /* cRows */,
/* [size_is][in] */ const HROW /* rghRows*/ [] ,
/* [in] */ DBREASON /* eReason */,
/* [in] */ DBEVENTPHASE /* ePhase */,
/* [in] */ BOOL /* fCantDeny */)
```

#### <a name="parameters"></a>Parámetros

Vea [IRowsetNotify:: OnRowChange](/previous-versions/windows/desktop/ms722694(v=vs.85)) para obtener descripciones de los parámetros.

### <a name="return-value"></a>Valor devuelto

Vea [IRowsetNotify:: OnRowChange](/previous-versions/windows/desktop/ms722694(v=vs.85)) para obtener descripciones de valores devueltos.

### <a name="remarks"></a>Observaciones

Este método encapsula el método [IRowsetNotify:: OnRowChange](/previous-versions/windows/desktop/ms722694(v=vs.85)) . Vea la descripción del método en la referencia del programador de OLE DB para obtener más información.

## <a name="irowsetnotifyimplonrowsetchange"></a><a name="onrowsetchange"></a>Irowsetnotifyimpl (:: OnRowsetChange

Notifica al consumidor cualquier cambio que afecte al conjunto de filas completo.

### <a name="syntax"></a>Sintaxis

```cpp
STDMETHOD(OnRowsetChange)(
/* [in] */ IRowset* /* pRowset */,
/* [in] */ DBREASON /* eReason */,
/* [in] */ DBEVENTPHASE /* ePhase */,
/* [in] */ BOOL /* fCantDeny */)
```

#### <a name="parameters"></a>Parámetros

Vea [IRowsetNotify:: OnRowsetChange](/previous-versions/windows/desktop/ms722669(v=vs.85)) para obtener descripciones de los parámetros.

### <a name="return-value"></a>Valor devuelto

Vea [IRowsetNotify:: OnRowsetChange](/previous-versions/windows/desktop/ms722669(v=vs.85)) para obtener descripciones de valores devueltos.

### <a name="remarks"></a>Observaciones

Este método encapsula el método [IRowsetNotify:: OnRowsetChange](/previous-versions/windows/desktop/ms722669(v=vs.85)) . Vea la descripción del método en la referencia del programador de OLE DB para obtener más información.

## <a name="see-also"></a>Consulte también

[Plantillas de consumidor OLE DB](../../data/oledb/ole-db-consumer-templates-cpp.md)<br/>
[IRowsetNotify](/previous-versions/windows/desktop/ms712959(v=vs.85))
[IRowsetNotifyCP (clase](../../data/oledb/irowsetnotifycp-class.md) )
