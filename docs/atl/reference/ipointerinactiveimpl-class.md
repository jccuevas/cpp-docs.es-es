---
title: IPointerInactiveImpl (clase) | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-atl
ms.topic: reference
f1_keywords:
- IPointerInactiveImpl
- ATLCTL/ATL::IPointerInactiveImpl
- ATLCTL/ATL::IPointerInactiveImpl::GetActivationPolicy
- ATLCTL/ATL::IPointerInactiveImpl::OnInactiveMouseMove
- ATLCTL/ATL::IPointerInactiveImpl::OnInactiveSetCursor
dev_langs:
- C++
helpviewer_keywords:
- IPointerInactive ATL implementation
- inactive objects
- IPointerInactiveImpl class
ms.assetid: e1fe9ea6-d38a-4527-9112-eb344771e0b7
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: f53b75466a4fe623de9c1f0fd6f0ff768cf55f47
ms.sourcegitcommit: 92dbc4b9bf82fda96da80846c9cfcdba524035af
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/05/2018
ms.locfileid: "43760317"
---
# <a name="ipointerinactiveimpl-class"></a>IPointerInactiveImpl (clase)

Esta clase implementa `IUnknown` y [IPointerInactive](/windows/desktop/api/ocidl/nn-ocidl-ipointerinactive) métodos de interfaz.

> [!IMPORTANT]
>  Esta clase y sus miembros no se puede usar en aplicaciones que se ejecutan en el tiempo de ejecución de Windows.

## <a name="syntax"></a>Sintaxis

```
template<class T>
class IPointerInactiveImpl
```

#### <a name="parameters"></a>Parámetros

*T*  
La clase derivada de `IPointerInactiveImpl`.

## <a name="members"></a>Miembros

### <a name="public-methods"></a>Métodos públicos

|Name|Descripción|
|----------|-----------------|
|[IPointerInactiveImpl::GetActivationPolicy](#getactivationpolicy)|Recupera la directiva de activación actual para el objeto. La implementación de ATL devuelve E_NOTIMPL.|
|[IPointerInactiveImpl::OnInactiveMouseMove](#oninactivemousemove)|Notifica el objeto que se ha desplazado el puntero del mouse sobre él, que indica el objeto puede desencadenar los eventos del mouse. La implementación de ATL devuelve E_NOTIMPL.|
|[IPointerInactiveImpl::OnInactiveSetCursor](#oninactivesetcursor)|Establece el puntero del mouse para el objeto inactivo. La implementación de ATL devuelve E_NOTIMPL.|

## <a name="remarks"></a>Comentarios

Un objeto inactivo es aquel que es simplemente carga o se ejecuta. A diferencia de un objeto activo, un objeto inactivo no puede recibir mensajes de teclado y mouse de Windows. Por lo tanto, los objetos inactivos utilizan menos recursos y suelen ser más están.

El [IPointerInactive](/windows/desktop/api/ocidl/nn-ocidl-ipointerinactive) interfaz permite que un objeto admitir un nivel mínimo de interacción con el mouse mientras permanecen inactivos. Esta funcionalidad es especialmente útil para los controles.

Clase `IPointerInactiveImpl` implementa el `IPointerInactive` métodos devolviendo simplemente E_NOTIMPL. Sin embargo, implementa `IUnknown` mediante el envío de información para el volcado de memoria se basa el dispositivo en modo de depuración.

**Artículos relacionados con** [Tutorial de ATL](../../atl/active-template-library-atl-tutorial.md), [crear un proyecto ATL](../../atl/reference/creating-an-atl-project.md)

## <a name="inheritance-hierarchy"></a>Jerarquía de herencia

`IPointerInactive`

`IPointerInactiveImpl`

## <a name="requirements"></a>Requisitos

**Encabezado:** atlctl.h

##  <a name="getactivationpolicy"></a>  IPointerInactiveImpl::GetActivationPolicy

Recupera la directiva de activación actual para el objeto.

```
HRESULT GetActivationPolicy(DWORD* pdwPolicy);
```

### <a name="return-value"></a>Valor devuelto

Devuelve E_NOTIMPL.

### <a name="remarks"></a>Comentarios

Consulte [IPointerInactive::GetActivationPolicy](/windows/desktop/api/ocidl/nf-ocidl-ipointerinactive-getactivationpolicy) en el SDK de Windows.

##  <a name="oninactivemousemove"></a>  IPointerInactiveImpl::OnInactiveMouseMove

Notifica el objeto que se ha desplazado el puntero del mouse sobre él, que indica el objeto puede desencadenar los eventos del mouse.

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

Consulte [IPointerInactive::OnInactiveMouseMove](/windows/desktop/api/ocidl/nf-ocidl-ipointerinactive-oninactivemousemove) en el SDK de Windows.

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

Consulte [IPointerInactive::OnInactiveSetCursor](/windows/desktop/api/ocidl/nf-ocidl-ipointerinactive-oninactivesetcursor) en el SDK de Windows.

## <a name="see-also"></a>Vea también

[Información general de clases](../../atl/atl-class-overview.md)
