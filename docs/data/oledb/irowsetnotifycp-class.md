---
title: IRowsetNotifyCP (Clase)
ms.date: 11/04/2016
f1_keywords:
- IRowsetNotifyCP
- Fire_OnFieldChange
- ATL::IRowsetNotifyCP::Fire_OnFieldChange
- ATL.IRowsetNotifyCP.Fire_OnFieldChange
- IRowsetNotifyCP.Fire_OnFieldChange
- IRowsetNotifyCP::Fire_OnFieldChange
- IRowsetNotifyCP.Fire_OnRowChange
- ATL.IRowsetNotifyCP.Fire_OnRowChange
- Fire_OnRowChange
- ATL::IRowsetNotifyCP::Fire_OnRowChange
- IRowsetNotifyCP::Fire_OnRowChange
- Fire_OnRowsetChange
- IRowsetNotifyCP::Fire_OnRowsetChange
- IRowsetNotifyCP.Fire_OnRowsetChange
- ATL::IRowsetNotifyCP::Fire_OnRowsetChange
- ATL.IRowsetNotifyCP.Fire_OnRowsetChange
helpviewer_keywords:
- IRowsetNotifyCP class
- Fire_OnFieldChange method
- Fire_OnRowChange method
- Fire_OnRowsetChange method
ms.assetid: ccef402b-94a0-4c2e-9a13-7e854ef82390
ms.openlocfilehash: 481c2c0ec28972e9cef8d1103e49afa2037c2393
ms.sourcegitcommit: fcb48824f9ca24b1f8bd37d647a4d592de1cc925
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 08/15/2019
ms.locfileid: "79544571"
---
# <a name="irowsetnotifycp-class"></a>IRowsetNotifyCP (Clase)

Implementa el sitio del proveedor para la interfaz de punto de conexión [IRowsetNotify](/previous-versions/windows/desktop/ms712959(v=vs.85)).

## <a name="syntax"></a>Sintaxis

```cpp
template <class T, class ReentrantEventSync = CComSharedMutex>
class IRowsetNotifyCP :
   public IConnectionPointImpl<
      T,
      piid = &__uuidof(IRowsetNotify),
      CComDynamicUnkArray DynamicUnkArray>,
   public ReentrantEventSync
```

### <a name="parameters"></a>Parámetros

*T*<br/>
Una clase derivada de `IRowsetNotifyCP`.

*ReentrantEventSync*<br/>
Una clase mutex que admite la reentrada (el valor predeterminado es `CComSharedMutex`). Una exclusión mutua es un objeto de sincronización que permite que un subproceso tenga acceso mutuamente exclusivo a un recurso.

*piid*<br/>
Un puntero de identificador de interfaz (`IID*`) para una interfaz de punto de conexión `IRowsetNotify`. El valor predeterminado es `&__uuidof(IRowsetNotify)`.

*DynamicUnkArray*<br/>
Matriz de tipo [CComDynamicUnkArray](../../atl/reference/ccomdynamicunkarray-class.md), que es una matriz asignada dinámicamente de `IUnknown` punteros a las interfaces de receptor de cliente.

## <a name="requirements"></a>Requisitos

**Encabezado:** atldb.h

## <a name="members"></a>Members

### <a name="methods"></a>Métodos

|||
|-|-|
|[Fire_OnFieldChange](#onfieldchange)|Notifica al consumidor un cambio en el valor de una columna.|
|[Fire_OnRowChange](#onrowchange)|Notifica al consumidor un cambio que afecta a las filas.|
|[Fire_OnRowsetChange](#onrowsetchange)|Notifica al consumidor un cambio que afecta a todo el conjunto de filas.|

## <a name="remarks"></a>Observaciones

`IRowsetNotifyCP` implementa funciones de difusión para informar a los agentes de escucha en el punto de conexión `IID_IRowsetNotify` de los cambios en el contenido del conjunto de filas.

Tenga en cuenta que también debe implementar y registrar `IRowsetNotify` en el consumidor (también conocido como "receptor") con [irowsetnotifyimpl (](../../data/oledb/irowsetnotifyimpl-class.md) para que el consumidor pueda controlar las notificaciones. Vea [recibir notificaciones](../../data/oledb/receiving-notifications.md) sobre la implementación de la interfaz de punto de conexión en el consumidor.

Para obtener información detallada sobre la implementación de notificaciones, vea el tema sobre las notificaciones de soporte técnico en [creación de un proveedor actualizable](../../data/oledb/creating-an-updatable-provider.md).

## <a name="irowsetnotifycpfire_onfieldchange"></a><a name="onfieldchange"></a>IRowsetNotifyCP:: Fire_OnFieldChange

Difunde un evento [OnFieldChange](/previous-versions/windows/desktop/ms715961(v=vs.85)) para notificar a los consumidores de un cambio en el valor de una columna.

### <a name="syntax"></a>Sintaxis

```cpp
HRESULT Fire_OnFieldChange(IRowset* pRowset,
   HROW hRow,
   DBORDINAL cColumns,
   DBORDINAL* rgColumns,
   DBREASON eReason,
   DBEVENTPHASE ePhase,
   BOOL fCantDeny);
```

#### <a name="parameters"></a>Parámetros

Vea [IRowsetNotify:: OnFieldChange](/previous-versions/windows/desktop/ms715961(v=vs.85)) en la *Referencia del programador de OLE DB*.

## <a name="irowsetnotifycpfire_onrowchange"></a><a name="onrowchange"></a>IRowsetNotifyCP:: Fire_OnRowChange

Difunde un evento [OnRowChange](/previous-versions/windows/desktop/ms722694(v=vs.85)) a todos los agentes de escucha en el punto de conexión `IID_IRowsetNotify` para notificar a los consumidores de un cambio que afecte a las filas.

### <a name="syntax"></a>Sintaxis

```cpp
HRESULT Fire_OnRowChange(IRowset* pRowset,
   DBCOUNTITEM cRows,
   const HROW rghRows[],
   DBREASON eReason,
   DBEVENTPHASE ePhase,
   BOOL fCantDeny);
```

#### <a name="parameters"></a>Parámetros

Vea [IRowsetNotify:: OnRowChange](/previous-versions/windows/desktop/ms722694(v=vs.85)) en la *Referencia del programador de OLE DB*.

## <a name="irowsetnotifycpfire_onrowsetchange"></a><a name="onrowsetchange"></a>IRowsetNotifyCP:: Fire_OnRowsetChange

Difunde un evento [OnRowsetChange](/previous-versions/windows/desktop/ms722669(v=vs.85)) en todos los agentes de escucha del punto de conexión `IID_IRowsetNotify` para notificar a los consumidores de un cambio que afecta a todo el conjunto de filas.

### <a name="syntax"></a>Sintaxis

```cpp
HRESULT Fire_OnRowsetChange(IRowset* pRowset,
   DBREASON eReason,
   DBEVENTPHASE ePhase,
   BOOL fCantDeny);
```

#### <a name="parameters"></a>Parámetros

Vea [IRowsetNotify:: OnRowsetChange](/previous-versions/windows/desktop/ms722669(v=vs.85)) en la *Referencia del programador de OLE DB*.

## <a name="see-also"></a>Consulte también

[Plantillas de proveedores OLE DB](../../data/oledb/ole-db-provider-templates-cpp.md)<br/>
[Arquitectura de plantillas de proveedores OLE DB](../../data/oledb/ole-db-provider-template-architecture.md)<br/>
[Notificaciones (COM)](/windows/win32/com/notifications)<br/>
[BEGIN_CONNECTION_POINT_MAP](../../atl/reference/connection-point-macros.md#begin_connection_point_map)<br/>
[END_CONNECTION_POINT_MAP](../../atl/reference/connection-point-macros.md#end_connection_point_map)<br/>
[CONNECTION_POINT_ENTRY](../../atl/reference/connection-point-macros.md#connection_point_entry)<br/>
[Crear un proveedor actualizable](../../data/oledb/creating-an-updatable-provider.md)