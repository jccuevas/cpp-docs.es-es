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
ms.openlocfilehash: 8ad3fe7a79d4847c4583f79229e4cf4aad616fa8
ms.sourcegitcommit: bff17488ac5538b8eaac57156a4d6f06b37d6b7f
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 03/05/2019
ms.locfileid: "57417351"
---
# <a name="irowsetnotifyimpl-class"></a>IRowsetNotifyImpl (Clase)

Implementa y registra [IRowsetNotify](/previous-versions/windows/desktop/ms712959(v=vs.85)) en el consumidor (también conocido como "receptor") que puede controlar las notificaciones.

## <a name="syntax"></a>Sintaxis

```cpp
class ATL_NO_VTABLE IRowsetNotifyImpl : public IRowsetNotify
```

## <a name="requirements"></a>Requisitos

**Encabezado:** atldbcli.h

## <a name="members"></a>Miembros

### <a name="methods"></a>Métodos

|||
|-|-|
|[OnFieldChange](#onfieldchange)|Notifica al consumidor cualquier cambio en el valor de una columna.|
|[OnRowChange](#onrowchange)|Notifica al consumidor el primer cambio a una fila o de cualquier cambio que afecte a toda la fila.|
|[OnRowsetChange](#onrowsetchange)|Notifica al consumidor cualquier cambio que afecte a todo el conjunto de filas.|

## <a name="remarks"></a>Comentarios

Consulte [recibir notificaciones](../../data/oledb/receiving-notifications.md) acerca de cómo implementar la interfaz de punto de conexión del consumidor.

`IRowsetNotifyImpl` Proporciona una implementación ficticia para `IRowsetNotify`, con funciones vacías para el `IRowsetNotify` métodos [OnFieldChange](/previous-versions/windows/desktop/ms715961(v=vs.85)), [OnRowChange](/previous-versions/windows/desktop/ms722694(v=vs.85)), y [OnRowsetChange](/previous-versions/windows/desktop/ms722669(v=vs.85)). Si se hereda de esta clase al implementar un `IRowsetNotify` interfaz, puede implementar sólo los métodos que necesita. También deberá proporcionar implementaciones vacías para los otros métodos usted mismo.

## <a name="onfieldchange"></a> IRowsetNotifyImpl::OnFieldChange

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

Consulte [IRowsetNotify::OnFieldChange](/previous-versions/windows/desktop/ms715961(v=vs.85)) para descripciones de parámetros.

### <a name="return-value"></a>Valor devuelto

Consulte [IRowsetNotify::OnFieldChange](/previous-versions/windows/desktop/ms715961(v=vs.85)) para devolver las descripciones de valor.

### <a name="remarks"></a>Comentarios

Este método ajusta el [IRowsetNotify::OnFieldChange](/previous-versions/windows/desktop/ms715961(v=vs.85)) método. Consulte la descripción del método en referencia del programador de OLE DB para obtener más información.

## <a name="onrowchange"></a> IRowsetNotifyImpl::OnRowChange

Notifica al consumidor el primer cambio a una fila o de cualquier cambio que afecte a toda la fila.

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

Consulte [IRowsetNotify::OnRowChange](/previous-versions/windows/desktop/ms722694(v=vs.85)) para descripciones de parámetros.

### <a name="return-value"></a>Valor devuelto

Consulte [IRowsetNotify::OnRowChange](/previous-versions/windows/desktop/ms722694(v=vs.85)) para devolver las descripciones de valor.

### <a name="remarks"></a>Comentarios

Este método ajusta el [IRowsetNotify::OnRowChange](/previous-versions/windows/desktop/ms722694(v=vs.85)) método. Consulte la descripción del método en referencia del programador de OLE DB para obtener más información.

## <a name="onrowsetchange"></a> IRowsetNotifyImpl::OnRowsetChange

Notifica al consumidor cualquier cambio que afecte a todo el conjunto de filas.

### <a name="syntax"></a>Sintaxis

```cpp
STDMETHOD(OnRowsetChange)(
/* [in] */ IRowset* /* pRowset */,
/* [in] */ DBREASON /* eReason */,
/* [in] */ DBEVENTPHASE /* ePhase */,
/* [in] */ BOOL /* fCantDeny */)
```

#### <a name="parameters"></a>Parámetros

Consulte [IRowsetNotify::OnRowsetChange](/previous-versions/windows/desktop/ms722669(v=vs.85)) para descripciones de parámetros.

### <a name="return-value"></a>Valor devuelto

Consulte [IRowsetNotify::OnRowsetChange](/previous-versions/windows/desktop/ms722669(v=vs.85)) para devolver las descripciones de valor.

### <a name="remarks"></a>Comentarios

Este método ajusta el [IRowsetNotify::OnRowsetChange](/previous-versions/windows/desktop/ms722669(v=vs.85)) método. Consulte la descripción del método en referencia del programador de OLE DB para obtener más información.

## <a name="see-also"></a>Vea también

[Plantillas de consumidor OLE DB](../../data/oledb/ole-db-consumer-templates-cpp.md)<br/>
[Plantillas de consumidor OLE DB](../../data/oledb/ole-db-consumer-templates-cpp.md)<br/>
[IRowsetNotify](/previous-versions/windows/desktop/ms712959(v=vs.85))
[IRowsetNotifyCP (clase)](../../data/oledb/irowsetnotifycp-class.md)