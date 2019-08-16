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
ms.openlocfilehash: 3ceb436e4f20a17ecd086fb68f9c1cfdcbe0be3e
ms.sourcegitcommit: fcb48824f9ca24b1f8bd37d647a4d592de1cc925
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 08/15/2019
ms.locfileid: "69495904"
---
# <a name="idispeventsimpleimpl-class"></a>IDispEventSimpleImpl (clase)

Esta clase proporciona implementaciones de los `IDispatch` métodos, sin obtener información de tipos de una biblioteca de tipos.

> [!IMPORTANT]
>  Esta clase y sus miembros no se pueden usar en aplicaciones que se ejecutan en el Windows Runtime.

## <a name="syntax"></a>Sintaxis

```
template <UINT nID, class T, const IID* pdiid>
class ATL_NO_VTABLE IDispEventSimpleImpl : public _IDispEventLocator<nID, pdiid>
```

#### <a name="parameters"></a>Parámetros

*nID*<br/>
Identificador único para el objeto de origen. Cuando `IDispEventSimpleImpl` es la clase base de un control compuesto, utilice el identificador de recurso del control contenido deseado para este parámetro. En otros casos, use un entero positivo arbitrario.

*T*<br/>
Clase del usuario, que se deriva de `IDispEventSimpleImpl`.

*pdiid*<br/>
Puntero al IID de la interfaz dispinterface de eventos implementada por esta clase.

## <a name="members"></a>Miembros

### <a name="public-methods"></a>Métodos públicos

|NOMBRE|DESCRIPCIÓN|
|----------|-----------------|
|[IDispEventSimpleImpl::Advise](#advise)|Establece una conexión con el origen de eventos predeterminado.|
|[IDispEventSimpleImpl::DispEventAdvise](#dispeventadvise)|Establece una conexión con el origen del evento.|
|[IDispEventSimpleImpl::DispEventUnadvise](#dispeventunadvise)|Interrumpe la conexión con el origen del evento.|
|[IDispEventSimpleImpl::GetIDsOfNames](#getidsofnames)|Devuelve E_NOTIMPL.|
|[IDispEventSimpleImpl::GetTypeInfo](#gettypeinfo)|Devuelve E_NOTIMPL.|
|[IDispEventSimpleImpl::GetTypeInfoCount](#gettypeinfocount)|Devuelve E_NOTIMPL.|
|[IDispEventSimpleImpl::Invoke](#invoke)|Llama a los controladores de eventos enumerados en el mapa del receptor de eventos.|
|[IDispEventSimpleImpl::Unadvise](#unadvise)|Interrumpe la conexión con el origen de eventos predeterminado.|

## <a name="remarks"></a>Comentarios

`IDispEventSimpleImpl`proporciona una manera de implementar una interfaz dispinterface de eventos sin necesidad de proporcionar código de implementación para todos los métodos y eventos de esa interfaz. `IDispEventSimpleImpl`proporciona implementaciones de los `IDispatch` métodos. Solo tiene que proporcionar implementaciones para los eventos que le interesa controlar.

`IDispEventSimpleImpl`funciona junto con el mapa del receptor de eventos en la clase para enrutar los eventos a la función de controlador adecuada. Para usar esta clase:

- Agregue una macro [SINK_ENTRY_INFO](composite-control-macros.md#sink_entry_info) al mapa del receptor de eventos para cada evento de cada objeto que desee controlar.

- Proporcione información de tipo para cada evento pasando un puntero a una estructura [_ATL_FUNC_INFO](../../atl/reference/atl-func-info-structure.md) como parámetro a cada entrada. En la plataforma x86, el `_ATL_FUNC_INFO.cc` valor debe ser CC_CDECL con el método de llamada a la función de devolución de llamada de _ _ Stdcall.

- Llame a [DispEventAdvise](#dispeventadvise) para establecer la conexión entre el objeto de origen y la clase base.

- Llame a [DispEventUnadvise](#dispeventunadvise) para interrumpir la conexión.

Debe derivar de `IDispEventSimpleImpl` (mediante un valor único para *nID*) para cada objeto para el que necesite controlar eventos. Puede reutilizar la clase base desaconsejando un objeto de origen y, a continuación, avisar contra un objeto de origen diferente, pero el número máximo de objetos de origen que puede controlar un solo objeto al mismo tiempo está `IDispEventSimpleImpl` limitado por el número de clases base.

`IDispEventSimplImpl`proporciona la misma funcionalidad que [IDispEventImpl](../../atl/reference/idispeventimpl-class.md), salvo que no obtiene información de tipo sobre la interfaz de una biblioteca de tipos. Los asistentes generan código basado únicamente en `IDispEventImpl`, pero puede usar `IDispEventSimpleImpl` agregando el código manualmente. Use `IDispEventSimpleImpl` cuando no tenga una biblioteca de tipos que describa la interfaz de eventos o desee evitar la sobrecarga asociada con el uso de la biblioteca de tipos.

> [!NOTE]
> `IDispEventImpl`y `IDispEventSimpleImpl` proporcionan su propia implementación de `IUnknown::QueryInterface` que permite `IDispEventImpl` que `IDispEventSimpleImpl` cada una de las clases base actúen como una identidad com independiente mientras se sigue permitiendo el acceso directo a los miembros de clase en el objeto com principal.

La implementación de ATL ATL de receptores de eventos ActiveX solo admite valores devueltos de tipo HRESULT o void de los métodos de control de eventos; no se admite ningún otro valor devuelto y su comportamiento es indefinido.

Para obtener más información, consulte [compatibilidad con IDispEventImpl](../../atl/supporting-idispeventimpl.md).

## <a name="inheritance-hierarchy"></a>Jerarquía de herencia

`_IDispEvent`

`_IDispEventLocator`

`IDispEventSimpleImpl`

## <a name="requirements"></a>Requisitos

**Encabezado:** atlcom. h

##  <a name="advise"></a>  IDispEventSimpleImpl::Advise

Llame a este método para establecer una conexión con el origen del evento representado por *pUnk*.

```
HRESULT Advise(IUnknown* pUnk);
```

### <a name="parameters"></a>Parámetros

*pUnk*<br/>
de Puntero a la `IUnknown` interfaz del objeto de origen del evento.

### <a name="return-value"></a>Valor devuelto

S_OK o cualquier valor HRESULT de error.

### <a name="remarks"></a>Comentarios

Una vez establecida la conexión, los eventos desencadenados desde *pUnk* se enrutarán a los controladores de la clase mediante el mapa del receptor de eventos.

> [!NOTE]
>  Si la clase se deriva de varias `IDispEventSimpleImpl` clases, deberá eliminar la ambigüedad de las llamadas a este método mediante el ámbito de la llamada con la clase base concreta que le interese.

`Advise`establece una conexión con el origen de eventos predeterminado, obtiene el IID del origen de eventos predeterminado del objeto determinado por [AtlGetObjectSourceInterface](composite-control-global-functions.md#atlgetobjectsourceinterface).

##  <a name="dispeventadvise"></a>  IDispEventSimpleImpl::DispEventAdvise

Llame a este método para establecer una conexión con el origen del evento representado por *pUnk*.

```
HRESULT DispEventAdvise(IUnknown* pUnk  const IID* piid);
```

### <a name="parameters"></a>Parámetros

*pUnk*<br/>
de Puntero a la `IUnknown` interfaz del objeto de origen del evento.

*piid*<br/>
Puntero al IID del objeto de origen del evento.

### <a name="return-value"></a>Valor devuelto

S_OK o cualquier valor HRESULT de error.

### <a name="remarks"></a>Comentarios

Posteriormente, los eventos desencadenados desde *pUnk* se enrutarán a los controladores de la clase mediante la asignación del receptor de eventos.

> [!NOTE]
>  Si la clase se deriva de varias `IDispEventSimpleImpl` clases, deberá eliminar la ambigüedad de las llamadas a este método mediante el ámbito de la llamada con la clase base concreta que le interese.

`DispEventAdvise`establece una conexión con el origen de eventos especificado `pdiid`en.

##  <a name="dispeventunadvise"></a>  IDispEventSimpleImpl::DispEventUnadvise

Interrumpe la conexión con el origen del evento representado por *pUnk*.

```
HRESULT DispEventUnadvise(IUnknown* pUnk  const IID* piid);
```

### <a name="parameters"></a>Parámetros

*pUnk*<br/>
de Puntero a la `IUnknown` interfaz del objeto de origen del evento.

*piid*<br/>
Puntero al IID del objeto de origen del evento.

### <a name="return-value"></a>Valor devuelto

S_OK o cualquier valor HRESULT de error.

### <a name="remarks"></a>Comentarios

Una vez interrumpida la conexión, los eventos ya no se enrutarán a las funciones de controlador enumeradas en el mapa del receptor de eventos.

> [!NOTE]
>  Si la clase se deriva de varias `IDispEventSimpleImpl` clases, deberá eliminar la ambigüedad de las llamadas a este método mediante el ámbito de la llamada con la clase base concreta que le interese.

`DispEventAdvise`interrumpe una conexión que se estableció con el origen de eventos especificado `pdiid`en.

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

Vea [IDispatch:: GetIDsOfNames](/windows/win32/api/oaidl/nf-oaidl-idispatch-getidsofnames) en el Windows SDK.

##  <a name="gettypeinfo"></a>  IDispEventSimpleImpl::GetTypeInfo

Esta implementación de `IDispatch::GetTypeInfo` devuelve E_NOTIMPL.

```
STDMETHOD(GetTypeInfo)(
    UINT /* itinfo */,
    LCID /* lcid */,
    ITypeInfo** /* pptinfo */);
```

### <a name="remarks"></a>Comentarios

Vea [IDispatch:: GetTypeInfo](/windows/win32/api/oaidl/nf-oaidl-idispatch-gettypeinfo) en el Windows SDK.

##  <a name="gettypeinfocount"></a>  IDispEventSimpleImpl::GetTypeInfoCount

Esta implementación de `IDispatch::GetTypeInfoCount` devuelve E_NOTIMPL.

```
STDMETHOD(GetTypeInfoCount)(UINT* /* pctinfo */);
```

### <a name="remarks"></a>Comentarios

Vea [IDispatch:: GetTypeInfoCount](/windows/win32/api/oaidl/nf-oaidl-idispatch-gettypeinfocount) en el Windows SDK.

##  <a name="invoke"></a>  IDispEventSimpleImpl::Invoke

Esta implementación de `IDispatch::Invoke` llama a los controladores de eventos enumerados en el mapa del receptor de eventos.

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

Vea [IDispatch:: Invoke](/windows/win32/api/oaidl/nf-oaidl-idispatch-invoke).

##  <a name="unadvise"></a>  IDispEventSimpleImpl::Unadvise

Interrumpe la conexión con el origen del evento representado por *pUnk*.

```
HRESULT Unadvise(IUnknown* pUnk);
```

### <a name="parameters"></a>Parámetros

*pUnk*<br/>
de Puntero a la `IUnknown` interfaz del objeto de origen del evento.

### <a name="return-value"></a>Valor devuelto

S_OK o cualquier valor HRESULT de error.

### <a name="remarks"></a>Comentarios

Una vez interrumpida la conexión, los eventos ya no se enrutarán a las funciones de controlador enumeradas en el mapa del receptor de eventos.

> [!NOTE]
>  Si la clase se deriva de varias `IDispEventSimpleImpl` clases, deberá eliminar la ambigüedad de las llamadas a este método mediante el ámbito de la llamada con la clase base concreta que le interese.

`Unadvise`interrumpe una conexión que se estableció con el origen de eventos predeterminado especificado `pdiid`en.

`Unavise`interrumpe una conexión con el origen de eventos predeterminado y obtiene el IID del origen de eventos predeterminado del objeto, según lo determinado por [AtlGetObjectSourceInterface](composite-control-global-functions.md#atlgetobjectsourceinterface).

## <a name="see-also"></a>Vea también

[_ATL_FUNC_INFO (estructura)](../../atl/reference/atl-func-info-structure.md)<br/>
[IDispatchImpl (clase)](../../atl/reference/idispatchimpl-class.md)<br/>
[IDispEventImpl (clase)](../../atl/reference/idispeventimpl-class.md)<br/>
[SINK_ENTRY_INFO](composite-control-macros.md#sink_entry_info)<br/>
[Información general sobre clases](../../atl/atl-class-overview.md)
