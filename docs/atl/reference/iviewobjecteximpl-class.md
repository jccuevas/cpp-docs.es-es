---
title: IViewObjectExImpl (clase)
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
ms.openlocfilehash: 4ed7a7e4a6070ba52c54c4dace687111cf7d33d8
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/23/2019
ms.locfileid: "62198218"
---
# <a name="iviewobjecteximpl-class"></a>IViewObjectExImpl (clase)

Esta clase implementa `IUnknown` y proporciona implementaciones predeterminadas de la [IViewObject](/windows/desktop/api/oleidl/nn-oleidl-iviewobject), [IViewObject2](/windows/desktop/api/oleidl/nn-oleidl-iviewobject2), y [IViewObjectEx](/windows/desktop/api/ocidl/nn-ocidl-iviewobjectex) interfaces.

> [!IMPORTANT]
>  Esta clase y sus miembros no se puede usar en aplicaciones que se ejecutan en el tiempo de ejecución de Windows.

## <a name="syntax"></a>Sintaxis

```
template<class T>
class ATL_NO_VTABLE IViewObjectExImpl
   : public IViewObjectEx
```

#### <a name="parameters"></a>Parámetros

*T*<br/>
La clase derivada de `IViewObjectExImpl`.

## <a name="members"></a>Miembros

### <a name="public-methods"></a>Métodos públicos

|Name|Descripción|
|----------|-----------------|
|[IViewObjectExImpl::Draw](#draw)|Dibuja una representación del control en un contexto de dispositivo.|
|[IViewObjectExImpl::Freeze](#freeze)|Se bloquea la representación de un control dibujada por lo que no cambiará hasta un `Unfreeze`. La implementación de ATL devuelve E_NOTIMPL.|
|[IViewObjectExImpl::GetAdvise](#getadvise)|Recupera una conexión de receptor de consulta existente en el control, si hay alguno.|
|[IViewObjectExImpl::GetColorSet](#getcolorset)|Devuelve la paleta lógica que se usa para dibujar el control. La implementación de ATL devuelve E_NOTIMPL.|
|[IViewObjectExImpl::GetExtent](#getextent)|Recupera el tamaño del control para mostrar en unidades HIMETRIC (0,01 milímetro por unidad) desde el miembro de datos de la clase de control [CComControlBase::m_sizeExtent](../../atl/reference/ccomcontrolbase-class.md#m_sizeextent).|
|[IViewObjectExImpl::GetNaturalExtent](#getnaturalextent)|Proporciona sugerencias de ajuste de tamaño del contenedor para el objeto que se va a usar cuando el usuario cambie el tamaño.|
|[IViewObjectExImpl::GetRect](#getrect)|Devuelve un rectángulo que describe un aspecto de dibujo solicitado. La implementación de ATL devuelve E_NOTIMPL.|
|[IViewObjectExImpl::GetViewStatus](#getviewstatus)|Devuelve información acerca de la opacidad del objeto y qué aspectos de dibujo se admiten.|
|[IViewObjectExImpl::QueryHitPoint](#queryhitpoint)|Comprueba si el punto especificado está en el rectángulo especificado y devuelve un [HITRESULT](/windows/desktop/api/ocidl/ne-ocidl-taghitresult) valor en `pHitResult`.|
|[IViewObjectExImpl::QueryHitRect](#queryhitrect)|Comprueba si el rectángulo de presentación del control se superpone a cualquier punto en el rectángulo de la ubicación especificada y devuelve un valor HITRESULT en `pHitResult`.|
|[IViewObjectExImpl::SetAdvise](#setadvise)|Establece una conexión entre el control y un receptor con notificación de modo que el receptor puede recibir notificaciones de cambios en la vista del control.|
|[IViewObjectExImpl::Unfreeze](#unfreeze)|Libera la representación del control dibujada. La implementación de ATL devuelve E_NOTIMPL.|

## <a name="remarks"></a>Comentarios

El [IViewObject](/windows/desktop/api/oleidl/nn-oleidl-iviewobject), [IViewObject2](/windows/desktop/api/oleidl/nn-oleidl-iviewobject2), y [IViewObjectEx](/windows/desktop/api/ocidl/nn-ocidl-iviewobjectex) interfaces permiten un control para que se muestre directamente y crear y administrar un receptor con notificación para notificar a la contenedor de los cambios en la presentación del control. El `IViewObjectEx` interfaz proporciona compatibilidad con características de control extendido como dibujo parpadeo, controles transparentes y no rectangulares y prueba de posicionamiento (por ejemplo, cómo cerrar un clic del mouse debe ser a tener en cuenta en el control). Clase `IViewObjectExImpl` proporciona una implementación predeterminada de estas interfaces e implementa `IUnknown` mediante el envío de información para el volcado de memoria se basa el dispositivo en modo de depuración.

## <a name="inheritance-hierarchy"></a>Jerarquía de herencia

`IViewObjectEx`

`IViewObjectExImpl`

## <a name="requirements"></a>Requisitos

**Encabezado:** atlctl.h

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

Este método llama a `CComControl::OnDrawAdvanced` que a su vez llama a la clase control `OnDraw` método. Un `OnDraw` método se agrega automáticamente a la clase del control cuando se crea el control con el Asistente para controles ATL. Valor predeterminado del asistente `OnDraw` dibuja un rectángulo con la etiqueta "ATL 3.0".

Consulte [IViewObject::Draw](/windows/desktop/api/oleidl/nf-oleidl-iviewobject-draw) en el SDK de Windows.

##  <a name="freeze"></a>  IViewObjectExImpl::Freeze

Se bloquea la representación de un control dibujada por lo que no cambiará hasta un `Unfreeze`. La implementación de ATL devuelve E_NOTIMPL.

```
STDMETHOD(Freeze)(
    DWORD /* dwAspect */,
    LONG /* lindex */,
    void* /* pvAspect */,
    DWORD* /* pdwFreeze */);
```

### <a name="remarks"></a>Comentarios

Consulte [IViewObject::Freeze](/windows/desktop/api/oleidl/nf-oleidl-iviewobject-freeze) en el SDK de Windows.

##  <a name="getadvise"></a>  IViewObjectExImpl::GetAdvise

Recupera una conexión de receptor de consulta existente en el control, si hay alguno.

```
STDMETHOD(GetAdvise)(
    DWORD* /* pAspects */,
    DWORD* /* pAdvf */,
    IAdviseSink** /* ppAdvSink */);
```

### <a name="remarks"></a>Comentarios

El receptor de consulta se almacena en el miembro de datos de la clase de control [CComControlBase::m_spAdviseSink](../../atl/reference/ccomcontrolbase-class.md#m_spadvisesink).

Consulte [IViewObject::GetAdvise](/windows/desktop/api/oleidl/nf-oleidl-iviewobject-getadvise) en el SDK de Windows.

##  <a name="getcolorset"></a>  IViewObjectExImpl::GetColorSet

Devuelve la paleta lógica que se usa para dibujar el control. La implementación de ATL devuelve E_NOTIMPL.

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

Consulte [IViewObject::GetColorSet](/windows/desktop/api/oleidl/nf-oleidl-iviewobject-getcolorset) en el SDK de Windows.

##  <a name="getextent"></a>  IViewObjectExImpl::GetExtent

Recupera el tamaño del control para mostrar en unidades HIMETRIC (0,01 milímetro por unidad) desde el miembro de datos de la clase de control [CComControlBase::m_sizeExtent](../../atl/reference/ccomcontrolbase-class.md#m_sizeextent).

```
STDMETHOD(GetExtent)(
    DWORD /* dwDrawAspect */,
    LONG /* lindex */,
    DVTARGETDEVICE* /* ptd */,
    LPSIZEL* lpsizel);
```

### <a name="remarks"></a>Comentarios

Consulte [IViewObject2::GetExtent](/windows/desktop/api/oleidl/nf-oleidl-iviewobject2-getextent) en el SDK de Windows.

##  <a name="getnaturalextent"></a>  IViewObjectExImpl::GetNaturalExtent

Proporciona sugerencias de ajuste de tamaño del contenedor para el objeto que se va a usar cuando el usuario cambie el tamaño.

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

Si `dwAspect` es DVASPECT_CONTENT y *pExtentInfo -> dwExtentMode* DVEXTENT_CONTENT, se establece * `psizel` al miembro de datos de la clase control [CComControlBase::m_sizeNatural](../../atl/reference/ccomcontrolbase-class.md#m_sizenatural). En caso contrario, devuelve un HRESULT de error.

Consulte [IViewObjectEx::GetNaturalExtent](/windows/desktop/api/ocidl/nf-ocidl-iviewobjectex-getnaturalextent) en el SDK de Windows.

##  <a name="getrect"></a>  IViewObjectExImpl::GetRect

Devuelve un rectángulo que describe un aspecto de dibujo solicitado. La implementación de ATL devuelve E_NOTIMPL.

```
STDMETHOD(GetRect)(DWORD /* dwAspect */, LPRECTL /* pRect */);
```

### <a name="remarks"></a>Comentarios

Consulte [IViewObjectEx::GetRect](/windows/desktop/api/ocidl/nf-ocidl-iviewobjectex-getrect) en el SDK de Windows.

##  <a name="getviewstatus"></a>  IViewObjectExImpl::GetViewStatus

Devuelve información acerca de la opacidad del objeto y qué aspectos de dibujo se admiten.

```
STDMETHOD(GetViewStatus)(DWORD* pdwStatus);
```

### <a name="remarks"></a>Comentarios

De forma predeterminada, Establece ATL `pdwStatus` para indicar que el control admite VIEWSTATUS_OPAQUE (los valores posibles son en el [VIEWSTATUS](/windows/desktop/api/ocidl/ne-ocidl-tagviewstatus) enumeración).

Consulte [IViewObjectEx::GetViewStatus](/windows/desktop/api/ocidl/nf-ocidl-iviewobjectex-getviewstatus) en el SDK de Windows.

##  <a name="queryhitpoint"></a>  IViewObjectExImpl::QueryHitPoint

Comprueba si el punto especificado está en el rectángulo especificado y devuelve un [HITRESULT](/windows/desktop/api/ocidl/ne-ocidl-taghitresult) valor en `pHitResult`.

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

Si `dwAspect` es igual a [DVASPECT_CONTENT](/windows/desktop/api/wtypes/ne-wtypes-tagdvaspect), el método devuelve S_OK. En caso contrario, el método devuelve E_FAIL.

Consulte [IViewObjectEx::QueryHitPoint](/windows/desktop/api/ocidl/nf-ocidl-iviewobjectex-queryhitpoint) en el SDK de Windows.

##  <a name="queryhitrect"></a>  IViewObjectExImpl::QueryHitRect

Comprueba si el rectángulo de presentación del control se superpone a cualquier punto en el rectángulo de la ubicación especificada y devuelve un [HITRESULT](/windows/desktop/api/ocidl/ne-ocidl-taghitresult) valor en `pHitResult`.

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

Si `dwAspect` es igual a [DVASPECT_CONTENT](/windows/desktop/api/wtypes/ne-wtypes-tagdvaspect), el método devuelve S_OK. En caso contrario, el método devuelve E_FAIL.

Consulte [IViewObjectEx::QueryHitRect](/windows/desktop/api/ocidl/nf-ocidl-iviewobjectex-queryhitrect) en el SDK de Windows.

##  <a name="setadvise"></a>  IViewObjectExImpl::SetAdvise

Establece una conexión entre el control y un receptor con notificación de modo que el receptor puede recibir notificaciones de cambios en la vista del control.

```
STDMETHOD(SetAdvise)(
    DWORD /* aspects */,
    DWORD /* advf */,
    IAdviseSink* pAdvSink);
```

### <a name="remarks"></a>Comentarios

El puntero a la [IAdviseSink](/windows/desktop/api/objidl/nn-objidl-iadvisesink) interfaz en el receptor de notificaciones se almacena en el miembro de datos de la clase de control [CComControlBase::m_spAdviseSink](ccomcontrolbase-class.md#m_spadvisesink).

Consulte [IViewObject::SetAdvise](/windows/desktop/api/oleidl/nf-oleidl-iviewobject-setadvise) en el SDK de Windows.

##  <a name="unfreeze"></a>  IViewObjectExImpl::Unfreeze

Libera la representación del control dibujada. La implementación de ATL devuelve E_NOTIMPL.

```
STDMETHOD(Unfreeze)(DWORD /* dwFreeze */);
```

### <a name="remarks"></a>Comentarios

Consulte [IViewObject::Unfreeze](/windows/desktop/api/oleidl/nf-oleidl-iviewobject-unfreeze) en el SDK de Windows.

##  <a name="closehandle"></a>  IWorkerThreadClient::CloseHandle

Implemente este método para cerrar el identificador asociado a este objeto.

```
HRESULT CloseHandle(HANDLE hHandle);
```

### <a name="parameters"></a>Parámetros

*hHandle*<br/>
El identificador al cerrarse.

### <a name="return-value"></a>Valor devuelto

Devuelva S_OK si funciona correctamente, o un error HRESULT en caso de error.

### <a name="remarks"></a>Comentarios

El identificador pasado a este método se asoció anteriormente con este objeto mediante una llamada a [CWorkerThread::AddHandle](../../atl/reference/cworkerthread-class.md#addhandle).

### <a name="example"></a>Ejemplo

El código siguiente muestra una implementación simple de `IWorkerThreadClient::CloseHandle`.

[!code-cpp[NVC_ATL_Utilities#135](../../atl/codesnippet/cpp/iviewobjecteximpl-class_1.cpp)]

##  <a name="execute"></a>  IWorkerThreadClient::Execute

Implemente este método para ejecutar código cuando se señaliza el identificador asociado a este objeto.

```
HRESULT Execute(DWORD_PTR dwParam, HANDLE hObject);
```

### <a name="parameters"></a>Parámetros

*dwParam*<br/>
El parámetro de usuario.

*hObject*<br/>
El identificador que se convertirá en señalado.

### <a name="return-value"></a>Valor devuelto

Devuelva S_OK si funciona correctamente, o un error HRESULT en caso de error.

### <a name="remarks"></a>Comentarios

El identificador y el DWORD/puntero pasado a este método estaban asociados anteriormente con este objeto mediante una llamada a [CWorkerThread::AddHandle](../../atl/reference/cworkerthread-class.md#addhandle).

### <a name="example"></a>Ejemplo

El código siguiente muestra una implementación simple de `IWorkerThreadClient::Execute`.

[!code-cpp[NVC_ATL_Utilities#136](../../atl/codesnippet/cpp/iviewobjecteximpl-class_2.cpp)]

## <a name="see-also"></a>Vea también

[CComControl (clase)](../../atl/reference/ccomcontrol-class.md)<br/>
[Interfaces de controles ActiveX](/windows/desktop/com/activex-controls-interfaces)<br/>
[Tutorial](../../atl/active-template-library-atl-tutorial.md)<br/>
[Creación de un proyecto ATL](../../atl/reference/creating-an-atl-project.md)<br/>
[Información general de clases](../../atl/atl-class-overview.md)
