---
title: Clase IPointerInactiveImpl
ms.date: 11/04/2016
f1_keywords:
- IPointerInactiveImpl
- ATLCTL/ATL::IPointerInactiveImpl
- ATLCTL/ATL::IPointerInactiveImpl::GetActivationPolicy
- ATLCTL/ATL::IPointerInactiveImpl::OnInactiveMouseMove
- ATLCTL/ATL::IPointerInactiveImpl::OnInactiveSetCursor
helpviewer_keywords:
- IPointerInactive ATL implementation
- inactive objects
- IPointerInactiveImpl class
ms.assetid: e1fe9ea6-d38a-4527-9112-eb344771e0b7
ms.openlocfilehash: 229b8c6803aa7b3817cb3d95474bde0502829f8b
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/14/2020
ms.locfileid: "81326444"
---
# <a name="ipointerinactiveimpl-class"></a>Clase IPointerInactiveImpl

Esta clase `IUnknown` implementa y el [IPointerInactive](/windows/win32/api/ocidl/nn-ocidl-ipointerinactive) métodos de interfaz.

> [!IMPORTANT]
> Esta clase y sus miembros no se pueden usar en aplicaciones que se ejecutan en Windows Runtime.

## <a name="syntax"></a>Sintaxis

```
template<class T>
class IPointerInactiveImpl
```

#### <a name="parameters"></a>Parámetros

*T*<br/>
Su clase, derivada `IPointerInactiveImpl`de .

## <a name="members"></a>Miembros

### <a name="public-methods"></a>Métodos públicos

|Nombre|Descripción|
|----------|-----------------|
|[IPointerInactiveImpl::GetActivationPolicy](#getactivationpolicy)|Recupera la directiva de activación actual para el objeto. La implementación de ATL devuelve E_NOTIMPL.|
|[IPointerInactiveImpl::OnInactiveMouseMove](#oninactivemousemove)|Notifica al objeto que el puntero del mouse se ha movido sobre él, lo que indica que el objeto puede desencadenar eventos del mouse. La implementación de ATL devuelve E_NOTIMPL.|
|[IPointerInactiveImpl::OnInactiveSetCursor](#oninactivesetcursor)|Establece el puntero del mouse para el objeto inactivo. La implementación de ATL devuelve E_NOTIMPL.|

## <a name="remarks"></a>Observaciones

Un objeto inactivo es uno que simplemente se carga o se ejecuta. A diferencia de un objeto activo, un objeto inactivo no puede recibir mensajes de teclado y mouse de Windows. Por lo tanto, los objetos inactivos utilizan menos recursos y suelen ser más eficaces.

La interfaz [IPointerInactive](/windows/win32/api/ocidl/nn-ocidl-ipointerinactive) permite que un objeto admita un nivel mínimo de interacción del mouse mientras permanece inactivo. Esta funcionalidad es especialmente útil para los controles.

Clase `IPointerInactiveImpl` implementa `IPointerInactive` los métodos simplemente devolviendo E_NOTIMPL. Sin embargo, `IUnknown` se implementa enviando información al dispositivo de volcado en compilaciones de depuración.

**Artículos relacionados** [Tutorial ATL](../../atl/active-template-library-atl-tutorial.md), [Creación de un proyecto ATL](../../atl/reference/creating-an-atl-project.md)

## <a name="inheritance-hierarchy"></a>Jerarquía de herencia

`IPointerInactive`

`IPointerInactiveImpl`

## <a name="requirements"></a>Requisitos

**Encabezado:** atlctl.h

## <a name="ipointerinactiveimplgetactivationpolicy"></a><a name="getactivationpolicy"></a>IPointerInactiveImpl::GetActivationPolicy

Recupera la directiva de activación actual para el objeto.

```
HRESULT GetActivationPolicy(DWORD* pdwPolicy);
```

### <a name="return-value"></a>Valor devuelto

Devuelve E_NOTIMPL.

### <a name="remarks"></a>Observaciones

Consulte [IPointerInactive::GetActivationPolicy](/windows/win32/api/ocidl/nf-ocidl-ipointerinactive-getactivationpolicy) en el Windows SDK.

## <a name="ipointerinactiveimploninactivemousemove"></a><a name="oninactivemousemove"></a>IPointerInactiveImpl::OnInactiveMouseMove

Notifica al objeto que el puntero del mouse se ha movido sobre él, lo que indica que el objeto puede desencadenar eventos del mouse.

```
HRESULT OnInactiveMouseMove(
    LPCRECT pRectBounds,
    long x,
    long y,
    DWORD dwMouseMsg);
```

### <a name="return-value"></a>Valor devuelto

Devuelve E_NOTIMPL.

### <a name="remarks"></a>Observaciones

Consulte [IPointerInactive::OnInactiveMouseMove](/windows/win32/api/ocidl/nf-ocidl-ipointerinactive-oninactivemousemove) en el Windows SDK.

## <a name="ipointerinactiveimploninactivesetcursor"></a><a name="oninactivesetcursor"></a>IPointerInactiveImpl::OnInactiveSetCursor

Establece el puntero del mouse para el objeto inactivo.

```
HRESULT OnInactiveSetCursor(
    LPCRECT pRectBounds,
    long x,
    long y,
    DWORD dwMouseMsg,
    BOOL fSetAlways);
```

### <a name="return-value"></a>Valor devuelto

Devuelve E_NOTIMPL.

### <a name="remarks"></a>Observaciones

Consulte [IPointerInactive::OnInactiveSetCursor](/windows/win32/api/ocidl/nf-ocidl-ipointerinactive-oninactivesetcursor) en el Windows SDK.

## <a name="see-also"></a>Consulte también

[Información general de clases](../../atl/atl-class-overview.md)
