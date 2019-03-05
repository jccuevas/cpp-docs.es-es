---
title: IDispEventSimpleImpl (clase)
ms.date: 11/04/2016
f1_keywords:
- IDispEventSimpleImpl
- ATLCOM/ATL::IDispEventSimpleImpl
- ATLCOM/ATL::IDispEventSimpleImpl::Advise
- ATLCOM/ATL::IDispEventSimpleImpl::DispEventAdvise
- ATLCOM/ATL::IDispEventSimpleImpl::DispEventUnadvise
- ATLCOM/ATL::IDispEventSimpleImpl::GetIDsOfNames
- ATLCOM/ATL::IDispEventSimpleImpl::GetTypeInfo
- ATLCOM/ATL::IDispEventSimpleImpl::GetTypeInfoCount
- ATLCOM/ATL::IDispEventSimpleImpl::Invoke
- ATLCOM/ATL::IDispEventSimpleImpl::Unadvise
helpviewer_keywords:
- IDispEventSimpleImpl class
ms.assetid: 971d82b7-a921-47fa-a4d8-909bed377ab0
ms.openlocfilehash: 1578518b8918f59b1da54f474e82cf899f3c76f6
ms.sourcegitcommit: c3093251193944840e3d0a068ecc30e6449624ba
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 03/04/2019
ms.locfileid: "57285547"
---
# <a name="idispeventsimpleimpl-class"></a>IDispEventSimpleImpl (clase)

Esta clase proporciona las implementaciones de la `IDispatch` métodos sin obtener información de tipo de una biblioteca de tipos.

> [!IMPORTANT]
>  Esta clase y sus miembros no se puede usar en aplicaciones que se ejecutan en el tiempo de ejecución de Windows.

## <a name="syntax"></a>Sintaxis

```
template <UINT nID, class T, const IID* pdiid>
class ATL_NO_VTABLE IDispEventSimpleImpl : public _IDispEventLocator<nID, pdiid>
```

#### <a name="parameters"></a>Parámetros

*nID*<br/>
Un identificador único para el objeto de origen. Cuando `IDispEventSimpleImpl` es la clase base para un control compuesto, utilice el identificador de recurso del control contenido deseado para este parámetro. En otros casos, utilice un entero positivo.

*T*<br/>
La clase del usuario, que se deriva de `IDispEventSimpleImpl`.

*pdiid*<br/>
El puntero para el IID de la interfaz dispinterface de evento implementado por esta clase.

## <a name="members"></a>Miembros

### <a name="public-methods"></a>Métodos públicos

|Name|Descripción|
|----------|-----------------|
|[IDispEventSimpleImpl::Advise](#advise)|Establece una conexión con el origen del evento de forma predeterminada.|
|[IDispEventSimpleImpl::DispEventAdvise](#dispeventadvise)|Establece una conexión con el origen del evento.|
|[IDispEventSimpleImpl::DispEventUnadvise](#dispeventunadvise)|Interrumpe la conexión con el origen del evento.|
|[IDispEventSimpleImpl::GetIDsOfNames](#getidsofnames)|Devuelve E_NOTIMPL.|
|[IDispEventSimpleImpl::GetTypeInfo](#gettypeinfo)|Devuelve E_NOTIMPL.|
|[IDispEventSimpleImpl::GetTypeInfoCount](#gettypeinfocount)|Devuelve E_NOTIMPL.|
|[IDispEventSimpleImpl::Invoke](#invoke)|Las llamadas a los controladores de eventos en el evento muestran mapa de receptores.|
|[IDispEventSimpleImpl::Unadvise](#unadvise)|Interrumpe la conexión con el origen del evento de forma predeterminada.|

## <a name="remarks"></a>Comentarios

`IDispEventSimpleImpl` Proporciona una manera de implementar una interfaz dispinterface de evento sin necesidad de proporcionar código de implementación para cada método o evento en esa interfaz. `IDispEventSimpleImpl` proporciona implementaciones de la `IDispatch` métodos. Solo deberá proporcionar implementaciones para los eventos que está interesado en el control.

`IDispEventSimpleImpl` funciona junto con el mapa de receptores de eventos en la clase para enrutar eventos a la función de controlador adecuado. Para usar esta clase:

- Agregar un [macro SINK_ENTRY_INFO](composite-control-macros.md#sink_entry_info) macro al mapa de receptores de eventos para cada evento en cada objeto que desea administrar.

- Proporcionar información de tipo para cada evento pasando un puntero a un [_ATL_FUNC_INFO](../../atl/reference/atl-func-info-structure.md) estructura como parámetro para cada entrada. En el x86 plataforma, el `_ATL_FUNC_INFO.cc` valor debe ser CC_CDECL con la función de devolución de llamada llamando al método de __stdcall.

- Llame a [DispEventAdvise](#dispeventadvise) para establecer la conexión entre el objeto de origen y la clase base.

- Llame a [DispEventUnadvise](#dispeventunadvise) para interrumpir la conexión.

Debe derivar de `IDispEventSimpleImpl` (con un valor único para *nID*) para cada objeto para el que necesita controlar los eventos. Puede volver a usar la clase base por desaconsejar con objeto de un origen que avisa de, a continuación, en un objeto de origen diferente, pero el número máximo de objetos de origen que pueden controlarse mediante un único objeto al mismo tiempo está limitado por el número de `IDispEventSimpleImpl` clases base.

`IDispEventSimplImpl` proporciona la misma funcionalidad que [IDispEventImpl](../../atl/reference/idispeventimpl-class.md), excepto en que no se obtiene información de tipo de la interfaz desde una biblioteca de tipos. Los asistentes generan código que se basa solo en `IDispEventImpl`, pero puede usar `IDispEventSimpleImpl` agregando el código a mano. Use `IDispEventSimpleImpl` cuando no tiene una biblioteca de tipos que describe la interfaz de eventos o desea evitar la sobrecarga asociada con el uso de la biblioteca de tipos.

> [!NOTE]
> `IDispEventImpl` y `IDispEventSimpleImpl` proporcionar su propia implementación de `IUnknown::QueryInterface` habilitar cada `IDispEventImpl` o `IDispEventSimpleImpl` clase para que actúe como una identidad de COM independiente mientras sigue permitiendo el acceso directo a los miembros de clase en el objeto COM principal base.

Implementación de ATL de CE de ActiveX eventos receptores solo admite valores devueltos de tipo HRESULT o void desde los métodos de controlador de eventos; no se admite ningún otro tipo de valor devuelto y su comportamiento es indefinido.

Para obtener más información, consulte [admitir IDispEventImpl](../../atl/supporting-idispeventimpl.md).

## <a name="inheritance-hierarchy"></a>Jerarquía de herencia

`_IDispEvent`

`_IDispEventLocator`

`IDispEventSimpleImpl`

## <a name="requirements"></a>Requisitos

**Encabezado:** atlcom.h

##  <a name="advise"></a>  IDispEventSimpleImpl::Advise

Llame a este método para establecer una conexión con el origen del evento representado por *pUnk*.

```
HRESULT Advise(IUnknown* pUnk);
```

### <a name="parameters"></a>Parámetros

*pUnk*<br/>
[in] Un puntero a la `IUnknown` interfaz del objeto de origen del evento.

### <a name="return-value"></a>Valor devuelto

S_OK o cualquier valor HRESULT de error.

### <a name="remarks"></a>Comentarios

Una vez establecida la conexión, los eventos desencadenan desde *pUnk* se enrutará a los controladores en la clase por medio de la asignación de receptor de eventos.

> [!NOTE]
>  Si la clase se deriva de varios `IDispEventSimpleImpl` clases, deberá eliminar la ambigüedad de llamadas a este método por el ámbito de la llamada con la clase base concreta que está interesado.

`Advise` establece una conexión con el origen del evento de forma predeterminada, obtiene el IID del origen del evento predeterminado del objeto según lo determinado por [AtlGetObjectSourceInterface](composite-control-global-functions.md#atlgetobjectsourceinterface).

##  <a name="dispeventadvise"></a>  IDispEventSimpleImpl::DispEventAdvise

Llame a este método para establecer una conexión con el origen del evento representado por *pUnk*.

```
HRESULT DispEventAdvise(IUnknown* pUnk  const IID* piid);
```

### <a name="parameters"></a>Parámetros

*pUnk*<br/>
[in] Un puntero a la `IUnknown` interfaz del objeto de origen del evento.

*piid*<br/>
Un puntero a lo IID del objeto de origen del evento.

### <a name="return-value"></a>Valor devuelto

S_OK o cualquier valor HRESULT de error.

### <a name="remarks"></a>Comentarios

Posteriormente, los eventos desencadenan desde *pUnk* se enrutará a los controladores en la clase por medio de la asignación de receptor de eventos.

> [!NOTE]
>  Si la clase se deriva de varios `IDispEventSimpleImpl` clases, deberá eliminar la ambigüedad de llamadas a este método por el ámbito de la llamada con la clase base concreta que está interesado.

`DispEventAdvise` establece una conexión con el origen del evento especificado en `pdiid`.

##  <a name="dispeventunadvise"></a>  IDispEventSimpleImpl::DispEventUnadvise

Interrumpe la conexión con el origen del evento representado por *pUnk*.

```
HRESULT DispEventUnadvise(IUnknown* pUnk  const IID* piid);
```

### <a name="parameters"></a>Parámetros

*pUnk*<br/>
[in] Un puntero a la `IUnknown` interfaz del objeto de origen del evento.

*piid*<br/>
Un puntero a lo IID del objeto de origen del evento.

### <a name="return-value"></a>Valor devuelto

S_OK o cualquier valor HRESULT de error.

### <a name="remarks"></a>Comentarios

Una vez que la conexión se interrumpe, eventos ya no se enrutarán a las funciones de controlador enumeradas en el mapa de receptores de eventos.

> [!NOTE]
>  Si la clase se deriva de varios `IDispEventSimpleImpl` clases, deberá eliminar la ambigüedad de llamadas a este método por el ámbito de la llamada con la clase base concreta que está interesado.

`DispEventAdvise` interrumpe una conexión que se ha establecido con el origen del evento especificado en `pdiid`.

##  <a name="getidsofnames"></a>  IDispEventSimpleImpl::GetIDsOfNames

Esta implementación de `IDispatch::GetIDsOfNames` devuelve E_NOTIMPL.

```
STDMETHOD(GetIDsOfNames)(
    REFIID /* riid */,
    LPOLESTR* /* rgszNames */,
    UINT /* cNames */,
    LCID /* lcid */,
    DISPID* /* rgdispid */);
```

### <a name="remarks"></a>Comentarios

Consulte [IDispatch:: GetIDsOfNames](/windows/desktop/api/oaidl/nf-oaidl-idispatch-getidsofnames) en el SDK de Windows.

##  <a name="gettypeinfo"></a>  IDispEventSimpleImpl::GetTypeInfo

Esta implementación de `IDispatch::GetTypeInfo` devuelve E_NOTIMPL.

```
STDMETHOD(GetTypeInfo)(
    UINT /* itinfo */,
    LCID /* lcid */,
    ITypeInfo** /* pptinfo */);
```

### <a name="remarks"></a>Comentarios

Consulte [IDispatch:: GetTypeInfo](/windows/desktop/api/oaidl/nf-oaidl-idispatch-gettypeinfo) en el SDK de Windows.

##  <a name="gettypeinfocount"></a>  IDispEventSimpleImpl::GetTypeInfoCount

Esta implementación de `IDispatch::GetTypeInfoCount` devuelve E_NOTIMPL.

```
STDMETHOD(GetTypeInfoCount)(UINT* /* pctinfo */);
```

### <a name="remarks"></a>Comentarios

Consulte [IDispatch:: GetTypeInfoCount](/windows/desktop/api/oaidl/nf-oaidl-idispatch-gettypeinfocount) en el SDK de Windows.

##  <a name="invoke"></a>  IDispEventSimpleImpl::Invoke

Esta implementación de `IDispatch::Invoke` llama a los controladores de eventos enumeran en el evento de mapa de receptores.

```
STDMETHOD(Invoke)(
    DISPID dispidMember,
    REFIID /* riid */,
    LCID lcid,
    WORD /* wFlags */,
    DISPPARMS* pdispparams,
    VARIANT* pvarResult,
    EXCEPINFO* /* pexcepinfo */,
    UINT* /* puArgErr */);
```

### <a name="remarks"></a>Comentarios

Consulte [IDispatch:: Invoke](/windows/desktop/api/oaidl/nf-oaidl-idispatch-invoke).

##  <a name="unadvise"></a>  IDispEventSimpleImpl::Unadvise

Interrumpe la conexión con el origen del evento representado por *pUnk*.

```
HRESULT Unadvise(IUnknown* pUnk);
```

### <a name="parameters"></a>Parámetros

*pUnk*<br/>
[in] Un puntero a la `IUnknown` interfaz del objeto de origen del evento.

### <a name="return-value"></a>Valor devuelto

S_OK o cualquier valor HRESULT de error.

### <a name="remarks"></a>Comentarios

Una vez que la conexión se interrumpe, eventos ya no se enrutarán a las funciones de controlador enumeradas en el mapa de receptores de eventos.

> [!NOTE]
>  Si la clase se deriva de varios `IDispEventSimpleImpl` clases, deberá eliminar la ambigüedad de llamadas a este método por el ámbito de la llamada con la clase base concreta que está interesado.

`Unadvise` interrumpe una conexión que se ha establecido con el origen de eventos predeterminado especificado en `pdiid`.

`Unavise` los saltos de una conexión con el origen del evento de forma predeterminada, obtiene el IID del origen del evento predeterminado del objeto según lo determinado por [AtlGetObjectSourceInterface](composite-control-global-functions.md#atlgetobjectsourceinterface).

## <a name="see-also"></a>Vea también

[_ATL_FUNC_INFO (estructura)](../../atl/reference/atl-func-info-structure.md)<br/>
[IDispatchImpl (clase)](../../atl/reference/idispatchimpl-class.md)<br/>
[IDispEventImpl (clase)](../../atl/reference/idispeventimpl-class.md)<br/>
[SINK_ENTRY_INFO](composite-control-macros.md#sink_entry_info)<br/>
[Información general de clases](../../atl/atl-class-overview.md)
