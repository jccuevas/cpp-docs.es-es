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
ms.openlocfilehash: 6fb5d9f2bcbdeda61f32947bf339d134c4924b72
ms.sourcegitcommit: fcb48824f9ca24b1f8bd37d647a4d592de1cc925
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 08/15/2019
ms.locfileid: "69495650"
---
# <a name="ipointerinactiveimpl-class"></a>Clase IPointerInactiveImpl

Esta clase implementa `IUnknown` los métodos de la interfaz [IPointerInactive](/windows/win32/api/ocidl/nn-ocidl-ipointerinactive) .

> [!IMPORTANT]
>  Esta clase y sus miembros no se pueden usar en aplicaciones que se ejecutan en el Windows Runtime.

## <a name="syntax"></a>Sintaxis

```
template<class T>
class IPointerInactiveImpl
```

#### <a name="parameters"></a>Parámetros

*T*<br/>
La clase, derivada de `IPointerInactiveImpl`.

## <a name="members"></a>Miembros

### <a name="public-methods"></a>Métodos públicos

|NOMBRE|DESCRIPCIÓN|
|----------|-----------------|
|[IPointerInactiveImpl::GetActivationPolicy](#getactivationpolicy)|Recupera la Directiva de activación actual del objeto. La implementación de ATL devuelve E_NOTIMPL.|
|[IPointerInactiveImpl::OnInactiveMouseMove](#oninactivemousemove)|Notifica al objeto que el puntero del mouse ha desplace sobre él, lo que indica que el objeto puede desencadenar eventos del mouse. La implementación de ATL devuelve E_NOTIMPL.|
|[IPointerInactiveImpl::OnInactiveSetCursor](#oninactivesetcursor)|Establece el puntero del mouse para el objeto inactivo. La implementación de ATL devuelve E_NOTIMPL.|

## <a name="remarks"></a>Comentarios

Un objeto inactivo es uno que simplemente se carga o se ejecuta. A diferencia de un objeto activo, un objeto inactivo no puede recibir los mensajes de teclado y del mouse de Windows. Por lo tanto, los objetos inactivos usan menos recursos y suelen ser más eficaces.

La interfaz [IPointerInactive](/windows/win32/api/ocidl/nn-ocidl-ipointerinactive) permite que un objeto admita un nivel mínimo de interacción con el mouse mientras permanece inactivo. Esta funcionalidad es especialmente útil para los controles.

La `IPointerInactiveImpl` clase implementa los `IPointerInactive` métodos simplemente devolviendo E_NOTIMPL. Sin embargo, implementa `IUnknown` enviando información al dispositivo de volcado en las compilaciones de depuración.

**Artículos relacionados** [Tutorial de ATL](../../atl/active-template-library-atl-tutorial.md), [crear un proyecto ATL](../../atl/reference/creating-an-atl-project.md)

## <a name="inheritance-hierarchy"></a>Jerarquía de herencia

`IPointerInactive`

`IPointerInactiveImpl`

## <a name="requirements"></a>Requisitos

**Encabezado:** atlctl. h

##  <a name="getactivationpolicy"></a>  IPointerInactiveImpl::GetActivationPolicy

Recupera la Directiva de activación actual del objeto.

```
HRESULT GetActivationPolicy(DWORD* pdwPolicy);
```

### <a name="return-value"></a>Valor devuelto

Devuelve E_NOTIMPL.

### <a name="remarks"></a>Comentarios

Vea [IPointerInactive:: GetActivationPolicy](/windows/win32/api/ocidl/nf-ocidl-ipointerinactive-getactivationpolicy) en el Windows SDK.

##  <a name="oninactivemousemove"></a>  IPointerInactiveImpl::OnInactiveMouseMove

Notifica al objeto que el puntero del mouse ha desplace sobre él, lo que indica que el objeto puede desencadenar eventos del mouse.

```
HRESULT OnInactiveMouseMove(
    LPCRECT pRectBounds,
    long x,
    long y,
    DWORD dwMouseMsg);
```

### <a name="return-value"></a>Valor devuelto

Devuelve E_NOTIMPL.

### <a name="remarks"></a>Comentarios

Vea [IPointerInactive:: OnInactiveMouseMove](/windows/win32/api/ocidl/nf-ocidl-ipointerinactive-oninactivemousemove) en el Windows SDK.

##  <a name="oninactivesetcursor"></a>  IPointerInactiveImpl::OnInactiveSetCursor

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

### <a name="remarks"></a>Comentarios

Vea [IPointerInactive:: OnInactiveSetCursor](/windows/win32/api/ocidl/nf-ocidl-ipointerinactive-oninactivesetcursor) en el Windows SDK.

## <a name="see-also"></a>Vea también

[Información general sobre clases](../../atl/atl-class-overview.md)
