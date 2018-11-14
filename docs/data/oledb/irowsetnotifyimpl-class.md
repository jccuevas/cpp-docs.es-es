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
ms.openlocfilehash: 01bcc60b0c88a3953d5e75b53ac58877f7eb15df
ms.sourcegitcommit: c40469825b6101baac87d43e5f4aed6df6b078f5
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 11/12/2018
ms.locfileid: "51556392"
---
# <a name="irowsetnotifyimpl-class"></a>IRowsetNotifyImpl (Clase)

Implementa y registra [IRowsetNotify](https://docs.microsoft.com/previous-versions/windows/desktop/ms712959(v=vs.85)) en el consumidor (también conocido como "receptor") que puede controlar las notificaciones.

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

`IRowsetNotifyImpl` Proporciona una implementación ficticia para `IRowsetNotify`, con funciones vacías para el `IRowsetNotify` métodos [OnFieldChange](https://docs.microsoft.com/previous-versions/windows/desktop/ms715961(v=vs.85)), [OnRowChange](https://docs.microsoft.com/previous-versions/windows/desktop/ms722694(v=vs.85)), y [OnRowsetChange](https://docs.microsoft.com/previous-versions/windows/desktop/ms722669(v=vs.85)). Si se hereda de esta clase al implementar un `IRowsetNotify` interfaz, puede implementar sólo los métodos que necesita. También deberá proporcionar implementaciones vacías para los otros métodos usted mismo.

## <a name="onfieldchange"></a> IRowsetNotifyImpl:: Onfieldchange

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

Consulte [IRowsetNotify::OnFieldChange](https://docs.microsoft.com/previous-versions/windows/desktop/ms715961(v=vs.85)) para descripciones de parámetros.

### <a name="return-value"></a>Valor devuelto

Consulte [IRowsetNotify::OnFieldChange](https://docs.microsoft.com/previous-versions/windows/desktop/ms715961(v=vs.85)) para devolver las descripciones de valor.

### <a name="remarks"></a>Comentarios

Este método ajusta el [IRowsetNotify::OnFieldChange](https://docs.microsoft.com/previous-versions/windows/desktop/ms715961(v=vs.85)) método. Consulte la descripción del método en referencia del programador de OLE DB para obtener más información.

## <a name="onrowchange"></a> IRowsetNotifyImpl:: Onrowchange

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

Consulte [IRowsetNotify::OnRowChange](https://docs.microsoft.com/previous-versions/windows/desktop/ms722694(v=vs.85)) para descripciones de parámetros.

### <a name="return-value"></a>Valor devuelto

Consulte [IRowsetNotify::OnRowChange](https://docs.microsoft.com/previous-versions/windows/desktop/ms722694(v=vs.85)) para devolver las descripciones de valor.

### <a name="remarks"></a>Comentarios

Este método ajusta el [IRowsetNotify::OnRowChange](https://docs.microsoft.com/previous-versions/windows/desktop/ms722694(v=vs.85)) método. Consulte la descripción del método en referencia del programador de OLE DB para obtener más información.

## <a name="onrowsetchange"></a> IRowsetNotifyImpl:: Onrowsetchange

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

Consulte [IRowsetNotify::OnRowsetChange](https://docs.microsoft.com/previous-versions/windows/desktop/ms722669(v=vs.85)) para descripciones de parámetros.

### <a name="return-value"></a>Valor devuelto

Consulte [IRowsetNotify::OnRowsetChange](https://docs.microsoft.com/previous-versions/windows/desktop/ms722669(v=vs.85)) para devolver las descripciones de valor.

### <a name="remarks"></a>Comentarios

Este método ajusta el [IRowsetNotify::OnRowsetChange](https://docs.microsoft.com/previous-versions/windows/desktop/ms722669(v=vs.85)) método. Consulte la descripción del método en referencia del programador de OLE DB para obtener más información.

## <a name="see-also"></a>Vea también

[Plantillas de consumidor OLE DB](../../data/oledb/ole-db-consumer-templates-cpp.md)<br/>
[Plantillas de consumidor OLE DB](../../data/oledb/ole-db-consumer-templates-cpp.md)<br/>
[IRowsetNotify](https://docs.microsoft.com/previous-versions/windows/desktop/ms712959(v=vs.85))
[IRowsetNotifyCP (clase)](../../data/oledb/irowsetnotifycp-class.md)