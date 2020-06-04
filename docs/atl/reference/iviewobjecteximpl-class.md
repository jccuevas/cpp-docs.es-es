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
ms.openlocfilehash: 59c5657dcd892544f7e790b52325cb9ecba0dd56
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/14/2020
ms.locfileid: "81326342"
---
# <a name="iviewobjecteximpl-class"></a>Clase IViewObjectExImpl

Esta clase `IUnknown` implementa y proporciona implementaciones predeterminadas de las interfaces [IViewObject](/windows/win32/api/oleidl/nn-oleidl-iviewobject), [IViewObject2](/windows/win32/api/oleidl/nn-oleidl-iviewobject2)e [IViewObjectEx](/windows/win32/api/ocidl/nn-ocidl-iviewobjectex) .

> [!IMPORTANT]
> Esta clase y sus miembros no se pueden usar en aplicaciones que se ejecutan en Windows Runtime.

## <a name="syntax"></a>Sintaxis

```
template<class T>
class ATL_NO_VTABLE IViewObjectExImpl
   : public IViewObjectEx
```

#### <a name="parameters"></a>Parámetros

*T*<br/>
Su clase, derivada `IViewObjectExImpl`de .

## <a name="members"></a>Miembros

### <a name="public-methods"></a>Métodos públicos

|Nombre|Descripción|
|----------|-----------------|
|[IViewObjectExImpl::Draw](#draw)|Dibuja una representación del control en un contexto de dispositivo.|
|[IViewObjectExImpl::Freeze](#freeze)|Congela la representación dibujada de un control `Unfreeze`para que no cambie hasta un archivo . La implementación de ATL devuelve E_NOTIMPL.|
|[IViewObjectExImpl::GetAdvise](#getadvise)|Recupera una conexión de receptor de aviso existente en el control, si hay una.|
|[IViewObjectExImpl::GetColorSet](#getcolorset)|Devuelve la paleta lógica utilizada por el control para dibujar. La implementación de ATL devuelve E_NOTIMPL.|
|[IViewObjectExImpl::GetExtent](#getextent)|Recupera el tamaño de visualización del control en unidades HIMETRIC (0,01 milímetros por unidad) del miembro de datos de clase de control [CComControlBase::m_sizeExtent](../../atl/reference/ccomcontrolbase-class.md#m_sizeextent).|
|[IViewObjectExImpl::GetNaturalExtent](#getnaturalextent)|Proporciona sugerencias de tamaño del contenedor para que el objeto lo use a medida que el usuario cambia su tamaño.|
|[IViewObjectExImpl::GetRect](#getrect)|Devuelve un rectángulo que describe un aspecto de dibujo solicitado. La implementación de ATL devuelve E_NOTIMPL.|
|[IViewObjectExImpl::GetViewStatus](#getviewstatus)|Devuelve información sobre la opacidad del objeto y qué aspectos de dibujo se admiten.|
|[IViewObjectExImpl::QueryHitPoint](#queryhitpoint)|Comprueba si el punto especificado está en el rectángulo especificado `pHitResult`y devuelve un valor [HITRESULT](/windows/win32/api/ocidl/ne-ocidl-hitresult) en .|
|[IViewObjectExImpl::QueryHitRect](#queryhitrect)|Comprueba si el rectángulo de visualización del control se superpone a cualquier `pHitResult`punto del rectángulo de ubicación especificado y devuelve un valor HITRESULT en .|
|[IViewObjectExImpl::SetAdvise](#setadvise)|Configura una conexión entre el control y un receptor de avisos para que se pueda notificar al receptor sobre los cambios en la vista del control.|
|[IViewObjectExImpl::Unfreeze](#unfreeze)|Descongela la representación dibujada del control. La implementación de ATL devuelve E_NOTIMPL.|

## <a name="remarks"></a>Observaciones

Las interfaces [IViewObject](/windows/win32/api/oleidl/nn-oleidl-iviewobject), [IViewObject2](/windows/win32/api/oleidl/nn-oleidl-iviewobject2)e [IViewObjectEx](/windows/win32/api/ocidl/nn-ocidl-iviewobjectex) permiten que un control se muestre directamente y cree y administre un receptor advise para notificar al contenedor de los cambios en la pantalla del control. La `IViewObjectEx` interfaz proporciona compatibilidad con funciones de control extendidas, como el dibujo sin parpadeos, los controles no rectangulares y transparentes y las pruebas de posicionamiento (por ejemplo, qué tan cerca debe tenerse en cuenta un clic del ratón en el control). Clase `IViewObjectExImpl` proporciona una implementación predeterminada de `IUnknown` estas interfaces e implementaciones mediante el envío de información al dispositivo de volcado en compilaciones de depuración.

## <a name="inheritance-hierarchy"></a>Jerarquía de herencia

`IViewObjectEx`

`IViewObjectExImpl`

## <a name="requirements"></a>Requisitos

**Encabezado:** atlctl.h

## <a name="iviewobjecteximpldraw"></a><a name="draw"></a>IViewObjectExImpl::Draw

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

### <a name="remarks"></a>Observaciones

Este método `CComControl::OnDrawAdvanced` llama a lo que `OnDraw` a su vez llama al método de la clase de control. Un `OnDraw` método se agrega automáticamente a la clase de control al crear el control con el Asistente para controles ATL. El valor predeterminado `OnDraw` del asistente dibuja un rectángulo con la etiqueta "ATL 3.0".

Consulte [IViewObject::Draw](/windows/win32/api/oleidl/nf-oleidl-iviewobject-draw) en el Windows SDK.

## <a name="iviewobjecteximplfreeze"></a><a name="freeze"></a>IViewObjectExImpl::Freeze

Congela la representación dibujada de un control `Unfreeze`para que no cambie hasta un archivo . La implementación de ATL devuelve E_NOTIMPL.

```
STDMETHOD(Freeze)(
    DWORD /* dwAspect */,
    LONG /* lindex */,
    void* /* pvAspect */,
    DWORD* /* pdwFreeze */);
```

### <a name="remarks"></a>Observaciones

Consulte [IViewObject::Freeze](/windows/win32/api/oleidl/nf-oleidl-iviewobject-freeze) en el Windows SDK.

## <a name="iviewobjecteximplgetadvise"></a><a name="getadvise"></a>IViewObjectExImpl::GetAdvise

Recupera una conexión de receptor de aviso existente en el control, si hay una.

```
STDMETHOD(GetAdvise)(
    DWORD* /* pAspects */,
    DWORD* /* pAdvf */,
    IAdviseSink** /* ppAdvSink */);
```

### <a name="remarks"></a>Observaciones

El receptor de aviso se almacena en el miembro de datos de clase de control [CComControlBase::m_spAdviseSink](../../atl/reference/ccomcontrolbase-class.md#m_spadvisesink).

Consulte [IViewObject::GetAdvise](/windows/win32/api/oleidl/nf-oleidl-iviewobject-getadvise) en el Windows SDK.

## <a name="iviewobjecteximplgetcolorset"></a><a name="getcolorset"></a>IViewObjectExImpl::GetColorSet

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

### <a name="remarks"></a>Observaciones

Vea [IViewObject::GetColorSet](/windows/win32/api/oleidl/nf-oleidl-iviewobject-getcolorset) en el Windows SDK.

## <a name="iviewobjecteximplgetextent"></a><a name="getextent"></a>IViewObjectExImpl::GetExtent

Recupera el tamaño de visualización del control en unidades HIMETRIC (0,01 milímetros por unidad) del miembro de datos de clase de control [CComControlBase::m_sizeExtent](../../atl/reference/ccomcontrolbase-class.md#m_sizeextent).

```
STDMETHOD(GetExtent)(
    DWORD /* dwDrawAspect */,
    LONG /* lindex */,
    DVTARGETDEVICE* /* ptd */,
    LPSIZEL* lpsizel);
```

### <a name="remarks"></a>Observaciones

Consulte [IViewObject2::GetExtent](/windows/win32/api/oleidl/nf-oleidl-iviewobject2-getextent) en el Windows SDK.

## <a name="iviewobjecteximplgetnaturalextent"></a><a name="getnaturalextent"></a>IViewObjectExImpl::GetNaturalExtent

Proporciona sugerencias de tamaño del contenedor para que el objeto lo use a medida que el usuario cambia su tamaño.

```
STDMETHOD(GetNaturalExtent)(
    DWORD dwAspect,
    LONG /* lindex */,
    DVTARGETDEVICE* /* ptd */,
    HDC /* hicTargetDevice */,
    DVEXTENTINFO* pExtentInfo,
    LPSIZEL psizel);
```

### <a name="remarks"></a>Observaciones

Si `dwAspect` es DVASPECT_CONTENT y *pExtentInfo->dwExtentMode* está DVEXTENT_CONTENT, establece * `psizel` en el miembro de datos de la clase de control [CComControlBase::m_sizeNatural](../../atl/reference/ccomcontrolbase-class.md#m_sizenatural). De lo contrario, devuelve un error HRESULT.

Consulte [IViewObjectEx::GetNaturalExtent](/windows/win32/api/ocidl/nf-ocidl-iviewobjectex-getnaturalextent) en el Windows SDK.

## <a name="iviewobjecteximplgetrect"></a><a name="getrect"></a>IViewObjectExImpl::GetRect

Devuelve un rectángulo que describe un aspecto de dibujo solicitado. La implementación de ATL devuelve E_NOTIMPL.

```
STDMETHOD(GetRect)(DWORD /* dwAspect */, LPRECTL /* pRect */);
```

### <a name="remarks"></a>Observaciones

Consulte [IViewObjectEx::GetRect](/windows/win32/api/ocidl/nf-ocidl-iviewobjectex-getrect) en el Windows SDK.

## <a name="iviewobjecteximplgetviewstatus"></a><a name="getviewstatus"></a>IViewObjectExImpl::GetViewStatus

Devuelve información sobre la opacidad del objeto y qué aspectos de dibujo se admiten.

```
STDMETHOD(GetViewStatus)(DWORD* pdwStatus);
```

### <a name="remarks"></a>Observaciones

De forma predeterminada, `pdwStatus` ATL establece para indicar que el control admite VIEWSTATUS_OPAQUE (los valores posibles están en la enumeración [VIEWSTATUS).](/windows/win32/api/ocidl/ne-ocidl-viewstatus)

Consulte [IViewObjectEx::GetViewStatus](/windows/win32/api/ocidl/nf-ocidl-iviewobjectex-getviewstatus) en el Windows SDK.

## <a name="iviewobjecteximplqueryhitpoint"></a><a name="queryhitpoint"></a>IViewObjectExImpl::QueryHitPoint

Comprueba si el punto especificado está en el rectángulo especificado `pHitResult`y devuelve un valor [HITRESULT](/windows/win32/api/ocidl/ne-ocidl-hitresult) en .

```
STDMETHOD(QueryHitPoint)(
    DWORD dwAspect,
    LPCRECT pRectBounds,
    POINT ptlLoc,
    LONG /* lCloseHit */,
    DWORD* /* pHitResult */);
```

### <a name="remarks"></a>Observaciones

El valor puede ser HITRESULT_HIT o HITRESULT_OUTSIDE.

Si `dwAspect` es igual [DVASPECT_CONTENT](/windows/win32/api/wtypes/ne-wtypes-dvaspect), el método devuelve S_OK. De lo contrario, el método devuelve E_FAIL.

Consulte [IViewObjectEx::QueryHitPoint](/windows/win32/api/ocidl/nf-ocidl-iviewobjectex-queryhitpoint) en el Windows SDK.

## <a name="iviewobjecteximplqueryhitrect"></a><a name="queryhitrect"></a>IViewObjectExImpl::QueryHitRect

Comprueba si el rectángulo de visualización del control se superpone a cualquier `pHitResult`punto del rectángulo de ubicación especificado y devuelve un valor [HITRESULT](/windows/win32/api/ocidl/ne-ocidl-hitresult) en .

```
STDMETHOD(QueryHitRect)(
    DWORD dwAspect,
    LPCRECT pRectBounds,
    LPRECT prcLoc,
    LONG /* lCloseHit */,
    DWORD* /* pHitResult */);
```

### <a name="remarks"></a>Observaciones

El valor puede ser HITRESULT_HIT o HITRESULT_OUTSIDE.

Si `dwAspect` es igual [DVASPECT_CONTENT](/windows/win32/api/wtypes/ne-wtypes-dvaspect), el método devuelve S_OK. De lo contrario, el método devuelve E_FAIL.

Consulte [IViewObjectEx::QueryHitRect](/windows/win32/api/ocidl/nf-ocidl-iviewobjectex-queryhitrect) en el Windows SDK.

## <a name="iviewobjecteximplsetadvise"></a><a name="setadvise"></a>IViewObjectExImpl::SetAdvise

Configura una conexión entre el control y un receptor de avisos para que se pueda notificar al receptor sobre los cambios en la vista del control.

```
STDMETHOD(SetAdvise)(
    DWORD /* aspects */,
    DWORD /* advf */,
    IAdviseSink* pAdvSink);
```

### <a name="remarks"></a>Observaciones

El puntero a la [IAdviseSink](/windows/win32/api/objidl/nn-objidl-iadvisesink) interfaz en el receptor advise se almacena en el miembro de datos de clase de control [CComControlBase::m_spAdviseSink](ccomcontrolbase-class.md#m_spadvisesink).

Consulte [IViewObject::SetAdvise](/windows/win32/api/oleidl/nf-oleidl-iviewobject-setadvise) en el Windows SDK.

## <a name="iviewobjecteximplunfreeze"></a><a name="unfreeze"></a>IViewObjectExImpl::Unfreeze

Descongela la representación dibujada del control. La implementación de ATL devuelve E_NOTIMPL.

```
STDMETHOD(Unfreeze)(DWORD /* dwFreeze */);
```

### <a name="remarks"></a>Observaciones

Consulte [IViewObject::Unfreeze](/windows/win32/api/oleidl/nf-oleidl-iviewobject-unfreeze) en el Windows SDK.

## <a name="iworkerthreadclientclosehandle"></a><a name="closehandle"></a>IWorkerThreadClient::CloseHandle

Implemente este método para cerrar el identificador asociado a este objeto.

```
HRESULT CloseHandle(HANDLE hHandle);
```

### <a name="parameters"></a>Parámetros

*hHandle*<br/>
El mango que se va a cerrar.

### <a name="return-value"></a>Valor devuelto

Devuelve S_OK en caso de éxito o un error HRESULT en caso de error.

### <a name="remarks"></a>Observaciones

El identificador pasado a este método se asoció anteriormente a este objeto mediante una llamada a [CWorkerThread::AddHandle](../../atl/reference/cworkerthread-class.md#addhandle).

### <a name="example"></a>Ejemplo

El código siguiente muestra `IWorkerThreadClient::CloseHandle`una implementación simple de .

[!code-cpp[NVC_ATL_Utilities#135](../../atl/codesnippet/cpp/iviewobjecteximpl-class_1.cpp)]

## <a name="iworkerthreadclientexecute"></a><a name="execute"></a>IWorkerThreadClient::Ejecutar

Implemente este método para ejecutar código cuando se señale el identificador asociado a este objeto.

```
HRESULT Execute(DWORD_PTR dwParam, HANDLE hObject);
```

### <a name="parameters"></a>Parámetros

*dwParam*<br/>
El parámetro de usuario.

*hObject*<br/>
El mango que se ha señalado.

### <a name="return-value"></a>Valor devuelto

Devuelve S_OK en caso de éxito o un error HRESULT en caso de error.

### <a name="remarks"></a>Observaciones

El identificador y DWORD/pointer pasados a este método se asociaron previamente a este objeto mediante una llamada a [CWorkerThread::AddHandle](../../atl/reference/cworkerthread-class.md#addhandle).

### <a name="example"></a>Ejemplo

El código siguiente muestra `IWorkerThreadClient::Execute`una implementación simple de .

[!code-cpp[NVC_ATL_Utilities#136](../../atl/codesnippet/cpp/iviewobjecteximpl-class_2.cpp)]

## <a name="see-also"></a>Consulte también

[Clase CComControl](../../atl/reference/ccomcontrol-class.md)<br/>
[Interfaces de controles ActiveX](/windows/win32/com/activex-controls-interfaces)<br/>
[Tutorial](../../atl/active-template-library-atl-tutorial.md)<br/>
[Creación de un proyecto ATL](../../atl/reference/creating-an-atl-project.md)<br/>
[Información general de clases](../../atl/atl-class-overview.md)
