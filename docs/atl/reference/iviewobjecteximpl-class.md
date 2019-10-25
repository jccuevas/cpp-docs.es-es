---
title: Clase IViewObjectExImpl
ms.date: 11/04/2016
f1_keywords:
- IViewObjectExImpl
- ATLCTL/ATL::IViewObjectExImpl
- ATLCTL/ATL::IViewObjectExImpl::Draw
- ATLCTL/ATL::IViewObjectExImpl::Freeze
- ATLCTL/ATL::IViewObjectExImpl::GetAdvise
- ATLCTL/ATL::IViewObjectExImpl::GetColorSet
- ATLCTL/ATL::IViewObjectExImpl::GetExtent
- ATLCTL/ATL::IViewObjectExImpl::GetNaturalExtent
- ATLCTL/ATL::IViewObjectExImpl::GetRect
- ATLCTL/ATL::IViewObjectExImpl::GetViewStatus
- ATLCTL/ATL::IViewObjectExImpl::QueryHitPoint
- ATLCTL/ATL::IViewObjectExImpl::QueryHitRect
- ATLCTL/ATL::IViewObjectExImpl::SetAdvise
- ATLCTL/ATL::IViewObjectExImpl::Unfreeze
helpviewer_keywords:
- ActiveX controls [C++], drawing
- IViewObjectEx ATL implementation
- advise sinks
- IViewObjectExImpl class
ms.assetid: ad6de760-1ee5-4883-b033-ae57beffc369
ms.openlocfilehash: 3aead41f317d175eac9dcb094aa2070d82dc6185
ms.sourcegitcommit: fcb48824f9ca24b1f8bd37d647a4d592de1cc925
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 08/15/2019
ms.locfileid: "69495501"
---
# <a name="iviewobjecteximpl-class"></a>Clase IViewObjectExImpl

Esta `IUnknown` clase implementa y proporciona implementaciones predeterminadas de las interfaces [IViewObject](/windows/win32/api/oleidl/nn-oleidl-iviewobject), [IViewObject2](/windows/win32/api/oleidl/nn-oleidl-iviewobject2)y [IViewObjectEx](/windows/win32/api/ocidl/nn-ocidl-iviewobjectex) .

> [!IMPORTANT]
>  Esta clase y sus miembros no se pueden usar en aplicaciones que se ejecutan en el Windows Runtime.

## <a name="syntax"></a>Sintaxis

```
template<class T>
class ATL_NO_VTABLE IViewObjectExImpl
   : public IViewObjectEx
```

#### <a name="parameters"></a>Parámetros

*T*<br/>
La clase, derivada de `IViewObjectExImpl`.

## <a name="members"></a>Miembros

### <a name="public-methods"></a>Métodos públicos

|NOMBRE|DESCRIPCIÓN|
|----------|-----------------|
|[IViewObjectExImpl::Draw](#draw)|Dibuja una representación del control en un contexto de dispositivo.|
|[IViewObjectExImpl::Freeze](#freeze)|Inmoviliza la representación dibujada de un control para que no cambie hasta un `Unfreeze`. La implementación de ATL devuelve E_NOTIMPL.|
|[IViewObjectExImpl::GetAdvise](#getadvise)|Recupera una conexión del receptor de consulta existente en el control, si existe.|
|[IViewObjectExImpl::GetColorSet](#getcolorset)|Devuelve la paleta lógica utilizada por el control para dibujar. La implementación de ATL devuelve E_NOTIMPL.|
|[IViewObjectExImpl::GetExtent](#getextent)|Recupera el tamaño de presentación del control en unidades HIMETRIC (0,01 milímetro por unidad) del miembro de datos de la clase de control [CComControlBase:: m_sizeExtent](../../atl/reference/ccomcontrolbase-class.md#m_sizeextent).|
|[IViewObjectExImpl::GetNaturalExtent](#getnaturalextent)|Proporciona sugerencias de tamaño del contenedor para el objeto que se va a usar cuando el usuario lo cambie.|
|[IViewObjectExImpl::GetRect](#getrect)|Devuelve un rectángulo que describe un aspecto de dibujo solicitado. La implementación de ATL devuelve E_NOTIMPL.|
|[IViewObjectExImpl::GetViewStatus](#getviewstatus)|Devuelve información sobre la opacidad del objeto y qué aspectos del dibujo se admiten.|
|[IViewObjectExImpl::QueryHitPoint](#queryhitpoint)|Comprueba si el punto especificado está en el rectángulo especificado y devuelve un valor [HITRESULT](/windows/win32/api/ocidl/ne-ocidl-hitresult) en `pHitResult`.|
|[IViewObjectExImpl::QueryHitRect](#queryhitrect)|Comprueba si el rectángulo de presentación del control se superpone a cualquier punto del rectángulo de ubicación especificado y devuelve un valor `pHitResult`de HITRESULT en.|
|[IViewObjectExImpl::SetAdvise](#setadvise)|Configura una conexión entre el control y un receptor de notificaciones para que el receptor pueda recibir notificaciones sobre los cambios en la vista del control.|
|[IViewObjectExImpl::Unfreeze](#unfreeze)|Libera la representación dibujada del control. La implementación de ATL devuelve E_NOTIMPL.|

## <a name="remarks"></a>Comentarios

Las interfaces [IViewObject](/windows/win32/api/oleidl/nn-oleidl-iviewobject), [IViewObject2](/windows/win32/api/oleidl/nn-oleidl-iviewobject2)y [IViewObjectEx](/windows/win32/api/ocidl/nn-ocidl-iviewobjectex) permiten que un control se muestre directamente, y para crear y administrar un receptor de notificaciones para notificar al contenedor de cambios en la pantalla del control. La `IViewObjectEx` interfaz proporciona compatibilidad con características de control extendido, como dibujos sin parpadeo, controles no rectangulares y transparentes, y pruebas de posicionamiento (por ejemplo, cómo se debe considerar el cierre de un clic del mouse en el control). La `IViewObjectExImpl` clase proporciona una implementación predeterminada de estas interfaces e `IUnknown` implementa enviando información al dispositivo de volcado en las compilaciones de depuración.

## <a name="inheritance-hierarchy"></a>Jerarquía de herencia

`IViewObjectEx`

`IViewObjectExImpl`

## <a name="requirements"></a>Requisitos

**Encabezado:** atlctl. h

##  <a name="draw"></a>  IViewObjectExImpl::Draw

Dibuja una representación del control en un contexto de dispositivo.

```
STDMETHOD(Draw)(
    DWORD dwDrawAspect,
    LONG lindex,
    void* pvAspect,
    DVTARGETDEVICE* ptd,
    HDC hicTargetDev,
    LPCRECTL prcBounds,
    LPCRECTL prcWBounds,
    BOOL(_stdcall* /* pfnContinue*/) (DWORD_PTR dwContinue),
    DWORD_PTR /* dwContinue */);
```

### <a name="remarks"></a>Comentarios

Este método llama `CComControl::OnDrawAdvanced` a, que a su vez llama al `OnDraw` método de la clase de control. Un `OnDraw` método se agrega automáticamente a la clase de control al crear el control con el Asistente para controles ATL. De forma predeterminada `OnDraw` , el asistente dibuja un rectángulo con la etiqueta "ATL 3,0".

Vea [IViewObject::D RAW](/windows/win32/api/oleidl/nf-oleidl-iviewobject-draw) en el Windows SDK.

##  <a name="freeze"></a>  IViewObjectExImpl::Freeze

Inmoviliza la representación dibujada de un control para que no cambie hasta un `Unfreeze`. La implementación de ATL devuelve E_NOTIMPL.

```
STDMETHOD(Freeze)(
    DWORD /* dwAspect */,
    LONG /* lindex */,
    void* /* pvAspect */,
    DWORD* /* pdwFreeze */);
```

### <a name="remarks"></a>Comentarios

Vea [IViewObject:: Freeze](/windows/win32/api/oleidl/nf-oleidl-iviewobject-freeze) en el Windows SDK.

##  <a name="getadvise"></a>  IViewObjectExImpl::GetAdvise

Recupera una conexión del receptor de consulta existente en el control, si existe.

```
STDMETHOD(GetAdvise)(
    DWORD* /* pAspects */,
    DWORD* /* pAdvf */,
    IAdviseSink** /* ppAdvSink */);
```

### <a name="remarks"></a>Comentarios

El receptor de consulta se almacena en el miembro de datos de la clase de control [CComControlBase:: m_spAdviseSink](../../atl/reference/ccomcontrolbase-class.md#m_spadvisesink).

Vea [IViewObject:: GetAdvise](/windows/win32/api/oleidl/nf-oleidl-iviewobject-getadvise) en el Windows SDK.

##  <a name="getcolorset"></a>  IViewObjectExImpl::GetColorSet

Devuelve la paleta lógica utilizada por el control para dibujar. La implementación de ATL devuelve E_NOTIMPL.

```
STDMETHOD(GetColorSet)(
    DWORD /* dwAspect */,
    LONG /* lindex */,
    void* /* pvAspect */,
    DVTARGETDEVICE* /* ptd */,
    HDC /* hicTargetDevice */,
    LOGPALETTE** /* ppColorSet */);
```

### <a name="remarks"></a>Comentarios

Vea [IViewObject:: GetColorSet](/windows/win32/api/oleidl/nf-oleidl-iviewobject-getcolorset) en el Windows SDK.

##  <a name="getextent"></a>  IViewObjectExImpl::GetExtent

Recupera el tamaño de presentación del control en unidades HIMETRIC (0,01 milímetro por unidad) del miembro de datos de la clase de control [CComControlBase:: m_sizeExtent](../../atl/reference/ccomcontrolbase-class.md#m_sizeextent).

```
STDMETHOD(GetExtent)(
    DWORD /* dwDrawAspect */,
    LONG /* lindex */,
    DVTARGETDEVICE* /* ptd */,
    LPSIZEL* lpsizel);
```

### <a name="remarks"></a>Comentarios

Vea [IViewObject2:: GetExtent](/windows/win32/api/oleidl/nf-oleidl-iviewobject2-getextent) en el Windows SDK.

##  <a name="getnaturalextent"></a>  IViewObjectExImpl::GetNaturalExtent

Proporciona sugerencias de tamaño del contenedor para el objeto que se va a usar cuando el usuario lo cambie.

```
STDMETHOD(GetNaturalExtent)(
    DWORD dwAspect,
    LONG /* lindex */,
    DVTARGETDEVICE* /* ptd */,
    HDC /* hicTargetDevice */,
    DVEXTENTINFO* pExtentInfo,
    LPSIZEL psizel);
```

### <a name="remarks"></a>Comentarios

Si `dwAspect` es DVASPECT_CONTENT y *pExtentInfo-> dwExtentMode* es DVEXTENT_CONTENT, establece * `psizel` en el miembro de datos de la clase de control [CComControlBase:: m_sizeNatural](../../atl/reference/ccomcontrolbase-class.md#m_sizenatural). De lo contrario, devuelve un error HRESULT.

Vea [IViewObjectEx:: GetNaturalExtent](/windows/win32/api/ocidl/nf-ocidl-iviewobjectex-getnaturalextent) en el Windows SDK.

##  <a name="getrect"></a>  IViewObjectExImpl::GetRect

Devuelve un rectángulo que describe un aspecto de dibujo solicitado. La implementación de ATL devuelve E_NOTIMPL.

```
STDMETHOD(GetRect)(DWORD /* dwAspect */, LPRECTL /* pRect */);
```

### <a name="remarks"></a>Comentarios

Vea [IViewObjectEx:: GetRect](/windows/win32/api/ocidl/nf-ocidl-iviewobjectex-getrect) en el Windows SDK.

##  <a name="getviewstatus"></a>  IViewObjectExImpl::GetViewStatus

Devuelve información sobre la opacidad del objeto y qué aspectos del dibujo se admiten.

```
STDMETHOD(GetViewStatus)(DWORD* pdwStatus);
```

### <a name="remarks"></a>Comentarios

De forma predeterminada, ATL `pdwStatus` establece para indicar que el control admite VIEWSTATUS_OPAQUE (los valores posibles están en la enumeración [VIEWSTATUS](/windows/win32/api/ocidl/ne-ocidl-viewstatus) ).

Vea [IViewObjectEx:: GetViewStatus](/windows/win32/api/ocidl/nf-ocidl-iviewobjectex-getviewstatus) en el Windows SDK.

##  <a name="queryhitpoint"></a>  IViewObjectExImpl::QueryHitPoint

Comprueba si el punto especificado está en el rectángulo especificado y devuelve un valor [HITRESULT](/windows/win32/api/ocidl/ne-ocidl-hitresult) en `pHitResult`.

```
STDMETHOD(QueryHitPoint)(
    DWORD dwAspect,
    LPCRECT pRectBounds,
    POINT ptlLoc,
    LONG /* lCloseHit */,
    DWORD* /* pHitResult */);
```

### <a name="remarks"></a>Comentarios

El valor puede ser HITRESULT_HIT o HITRESULT_OUTSIDE.

Si `dwAspect` es igual a [DVASPECT_CONTENT](/windows/win32/api/wtypes/ne-wtypes-dvaspect), el método devuelve S_OK. De lo contrario, el método devuelve E_FAIL.

Vea [IViewObjectEx:: QueryHitPoint](/windows/win32/api/ocidl/nf-ocidl-iviewobjectex-queryhitpoint) en el Windows SDK.

##  <a name="queryhitrect"></a>  IViewObjectExImpl::QueryHitRect

Comprueba si el rectángulo de presentación del control se superpone a cualquier punto del rectángulo de ubicación especificado y devuelve un valor [HITRESULT](/windows/win32/api/ocidl/ne-ocidl-hitresult) en `pHitResult`.

```
STDMETHOD(QueryHitRect)(
    DWORD dwAspect,
    LPCRECT pRectBounds,
    LPRECT prcLoc,
    LONG /* lCloseHit */,
    DWORD* /* pHitResult */);
```

### <a name="remarks"></a>Comentarios

El valor puede ser HITRESULT_HIT o HITRESULT_OUTSIDE.

Si `dwAspect` es igual a [DVASPECT_CONTENT](/windows/win32/api/wtypes/ne-wtypes-dvaspect), el método devuelve S_OK. De lo contrario, el método devuelve E_FAIL.

Vea [IViewObjectEx:: QueryHitRect](/windows/win32/api/ocidl/nf-ocidl-iviewobjectex-queryhitrect) en el Windows SDK.

##  <a name="setadvise"></a>  IViewObjectExImpl::SetAdvise

Configura una conexión entre el control y un receptor de notificaciones para que el receptor pueda recibir notificaciones sobre los cambios en la vista del control.

```
STDMETHOD(SetAdvise)(
    DWORD /* aspects */,
    DWORD /* advf */,
    IAdviseSink* pAdvSink);
```

### <a name="remarks"></a>Comentarios

El puntero a la interfaz [IAdviseSink](/windows/win32/api/objidl/nn-objidl-iadvisesink) en el receptor de notificaciones se almacena en el miembro de datos de la clase de control [CComControlBase:: m_spAdviseSink](ccomcontrolbase-class.md#m_spadvisesink).

Vea [IViewObject:: SetAdvise](/windows/win32/api/oleidl/nf-oleidl-iviewobject-setadvise) en el Windows SDK.

##  <a name="unfreeze"></a>  IViewObjectExImpl::Unfreeze

Libera la representación dibujada del control. La implementación de ATL devuelve E_NOTIMPL.

```
STDMETHOD(Unfreeze)(DWORD /* dwFreeze */);
```

### <a name="remarks"></a>Comentarios

Vea [IViewObject:: unfreeze](/windows/win32/api/oleidl/nf-oleidl-iviewobject-unfreeze) en el Windows SDK.

##  <a name="closehandle"></a>  IWorkerThreadClient::CloseHandle

Implemente este método para cerrar el identificador asociado a este objeto.

```
HRESULT CloseHandle(HANDLE hHandle);
```

### <a name="parameters"></a>Parámetros

*hHandle*<br/>
Identificador que se va a cerrar.

### <a name="return-value"></a>Valor devuelto

Devuelve S_OK si se ejecuta correctamente o un error HRESULT en caso de error.

### <a name="remarks"></a>Comentarios

El identificador pasado a este método se asoció previamente con este objeto mediante una llamada a [CWorkerThread:: AddHandle](../../atl/reference/cworkerthread-class.md#addhandle).

### <a name="example"></a>Ejemplo

En el código siguiente se muestra una implementación `IWorkerThreadClient::CloseHandle`simple de.

[!code-cpp[NVC_ATL_Utilities#135](../../atl/codesnippet/cpp/iviewobjecteximpl-class_1.cpp)]

##  <a name="execute"></a>  IWorkerThreadClient::Execute

Implemente este método para ejecutar el código cuando se Señalice el identificador asociado a este objeto.

```
HRESULT Execute(DWORD_PTR dwParam, HANDLE hObject);
```

### <a name="parameters"></a>Parámetros

*dwParam*<br/>
Parámetro de usuario.

*hObject*<br/>
Identificador que se ha señalado.

### <a name="return-value"></a>Valor devuelto

Devuelve S_OK si se ejecuta correctamente o un error HRESULT en caso de error.

### <a name="remarks"></a>Comentarios

El identificador y el puntero DWORD/que se pasan a este método se asociaron previamente a este objeto mediante una llamada a [CWorkerThread:: AddHandle](../../atl/reference/cworkerthread-class.md#addhandle).

### <a name="example"></a>Ejemplo

En el código siguiente se muestra una implementación `IWorkerThreadClient::Execute`simple de.

[!code-cpp[NVC_ATL_Utilities#136](../../atl/codesnippet/cpp/iviewobjecteximpl-class_2.cpp)]

## <a name="see-also"></a>Vea también

[CComControl (clase)](../../atl/reference/ccomcontrol-class.md)<br/>
[Interfaces de controles ActiveX](/windows/win32/com/activex-controls-interfaces)<br/>
[Tutorial](../../atl/active-template-library-atl-tutorial.md)<br/>
[Creación de un proyecto ATL](../../atl/reference/creating-an-atl-project.md)<br/>
[Información general sobre clases](../../atl/atl-class-overview.md)
