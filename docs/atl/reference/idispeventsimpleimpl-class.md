---
title: Clase IDispEventSimpleImpl
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
ms.openlocfilehash: 779e143094760c7bd868ad33f590f7fd8f004762
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/14/2020
ms.locfileid: "81329731"
---
# <a name="idispeventsimpleimpl-class"></a>Clase IDispEventSimpleImpl

Esta clase proporciona implementaciones de los `IDispatch` métodos, sin obtener información de tipo de una biblioteca de tipos.

> [!IMPORTANT]
> Esta clase y sus miembros no se pueden usar en aplicaciones que se ejecutan en Windows Runtime.

## <a name="syntax"></a>Sintaxis

```
template <UINT nID, class T, const IID* pdiid>
class ATL_NO_VTABLE IDispEventSimpleImpl : public _IDispEventLocator<nID, pdiid>
```

#### <a name="parameters"></a>Parámetros

*nID*<br/>
Identificador único para el objeto de origen. Cuando `IDispEventSimpleImpl` es la clase base para un control compuesto, utilice el identificador de recurso del control contenido deseado para este parámetro. En otros casos, utilice un entero positivo arbitrario.

*T*<br/>
La clase del usuario, que `IDispEventSimpleImpl`se deriva de .

*pdiid*<br/>
El puntero al IID de la interfaz dispinterface de eventos implementada por esta clase.

## <a name="members"></a>Miembros

### <a name="public-methods"></a>Métodos públicos

|Nombre|Descripción|
|----------|-----------------|
|[IDispEventSimpleImpl::Advise](#advise)|Establece una conexión con el origen de eventos predeterminado.|
|[IDispEventSimpleImpl::DispEventAdvise](#dispeventadvise)|Establece una conexión con el origen de eventos.|
|[IDispEventSimpleImpl::DispEventUnadvise](#dispeventunadvise)|Rompe la conexión con el origen de eventos.|
|[IDispEventSimpleImpl::GetIDsOfNames](#getidsofnames)|Devuelve E_NOTIMPL.|
|[IDispEventSimpleImpl::GetTypeInfo](#gettypeinfo)|Devuelve E_NOTIMPL.|
|[IDispEventSimpleImpl::GetTypeInfoCount](#gettypeinfocount)|Devuelve E_NOTIMPL.|
|[IDispEventSimpleImpl::Invoke](#invoke)|Llama a los controladores de eventos enumerados en el mapa del receptor de eventos.|
|[IDispEventSimpleImpl::Unadvise](#unadvise)|Rompe la conexión con el origen de eventos predeterminado.|

## <a name="remarks"></a>Observaciones

`IDispEventSimpleImpl`proporciona una manera de implementar una interfaz dispinterface de eventos sin necesidad de proporcionar código de implementación para cada método o evento en esa interfaz. `IDispEventSimpleImpl`proporciona implementaciones `IDispatch` de los métodos. Solo necesita proporcionar implementaciones para los eventos que está interesado en controlar.

`IDispEventSimpleImpl`funciona junto con el mapa de receptor es de eventos de la clase para enrutar eventos a la función de controlador adecuada. Para utilizar esta clase:

- Agregue una macro [SINK_ENTRY_INFO](composite-control-macros.md#sink_entry_info) al mapa del receptor de eventos para cada evento en cada objeto que desee controlar.

- Proporcione información de tipo para cada evento pasando un puntero a una estructura [_ATL_FUNC_INFO](../../atl/reference/atl-func-info-structure.md) como parámetro para cada entrada. En la plataforma x86, el `_ATL_FUNC_INFO.cc` valor debe CC_CDECL con el método de llamada de función de devolución de llamada de __stdcall.

- Llame a [DispEventAdvise](#dispeventadvise) para establecer la conexión entre el objeto de origen y la clase base.

- Llame a [DispEventUnadvise](#dispeventunadvise) para interrumpir la conexión.

Debe derivar `IDispEventSimpleImpl` de (mediante un valor único para *nID*) para cada objeto para el que necesita controlar eventos. Puede reutilizar la clase base desaconsejando un objeto de origen y, a continuación, aconsejando a un objeto de origen diferente, pero `IDispEventSimpleImpl` el número máximo de objetos de origen que puede controlar un único objeto a la vez está limitado por el número de clases base.

`IDispEventSimplImpl`proporciona la misma funcionalidad que [IDispEventImpl](../../atl/reference/idispeventimpl-class.md), excepto que no obtiene información de tipo sobre la interfaz de una biblioteca de tipos. Los asistentes generan código `IDispEventImpl`basado solo `IDispEventSimpleImpl` en , pero puede usarlo agregando el código a mano. Se `IDispEventSimpleImpl` usa cuando no tiene una biblioteca de tipos que describa la interfaz de eventos o desee evitar la sobrecarga asociada con el uso de la biblioteca de tipos.

> [!NOTE]
> `IDispEventImpl`y `IDispEventSimpleImpl` proporcionar su `IUnknown::QueryInterface` propia `IDispEventImpl` implementación de habilitar cada clase base para `IDispEventSimpleImpl` actuar como una identidad COM independiente mientras que todavía permite el acceso directo a los miembros de clase en el objeto COM principal.

La implementación de CE ATL de receptores de eventos ActiveX solo admite valores devueltos de tipo HRESULT o void de los métodos del controlador de eventos; cualquier otro valor devuelto no es compatible y su comportamiento es indefinido.

Para obtener más información, consulte [Compatibilidad con IDispEventImpl](../../atl/supporting-idispeventimpl.md).

## <a name="inheritance-hierarchy"></a>Jerarquía de herencia

`_IDispEvent`

`_IDispEventLocator`

`IDispEventSimpleImpl`

## <a name="requirements"></a>Requisitos

**Encabezado:** atlcom.h

## <a name="idispeventsimpleimpladvise"></a><a name="advise"></a>IDispEventSimpleImpl::Advise

Llame a este método para establecer una conexión con el origen de eventos representado por *pUnk*.

```
HRESULT Advise(IUnknown* pUnk);
```

### <a name="parameters"></a>Parámetros

*Punk*<br/>
[en] Un puntero `IUnknown` a la interfaz del objeto de origen de eventos.

### <a name="return-value"></a>Valor devuelto

S_OK o cualquier valor HRESULT de error.

### <a name="remarks"></a>Observaciones

Una vez establecida la conexión, los eventos desencadenados desde *pUnk* se enrutarán a los controladores de la clase mediante el mapa del receptor de eventos.

> [!NOTE]
> Si la clase deriva `IDispEventSimpleImpl` de varias clases, deberá desambiguar las llamadas a este método examinando la llamada con la clase base concreta que le interesa.

`Advise`establece una conexión con el origen de eventos predeterminado, obtiene el IID del origen de eventos predeterminado del objeto según lo determinado por [AtlGetObjectSourceInterface](composite-control-global-functions.md#atlgetobjectsourceinterface).

## <a name="idispeventsimpleimpldispeventadvise"></a><a name="dispeventadvise"></a>IDispEventSimpleImpl::DispEventAdvise

Llame a este método para establecer una conexión con el origen de eventos representado por *pUnk*.

```
HRESULT DispEventAdvise(IUnknown* pUnk  const IID* piid);
```

### <a name="parameters"></a>Parámetros

*Punk*<br/>
[en] Un puntero `IUnknown` a la interfaz del objeto de origen de eventos.

*piid*<br/>
Un puntero al IID del objeto de origen de eventos.

### <a name="return-value"></a>Valor devuelto

S_OK o cualquier valor HRESULT de error.

### <a name="remarks"></a>Observaciones

Posteriormente, los eventos desencadenados desde *pUnk* se enrutarán a los controladores de la clase mediante el mapa del receptor de eventos.

> [!NOTE]
> Si la clase deriva `IDispEventSimpleImpl` de varias clases, deberá desambiguar las llamadas a este método examinando la llamada con la clase base concreta que le interesa.

`DispEventAdvise`establece una conexión con el origen `pdiid`de eventos especificado en .

## <a name="idispeventsimpleimpldispeventunadvise"></a><a name="dispeventunadvise"></a>IDispEventSimpleImpl::DispEventUnadvise

Rompe la conexión con el origen de eventos representado por *pUnk*.

```
HRESULT DispEventUnadvise(IUnknown* pUnk  const IID* piid);
```

### <a name="parameters"></a>Parámetros

*Punk*<br/>
[en] Un puntero `IUnknown` a la interfaz del objeto de origen de eventos.

*piid*<br/>
Un puntero al IID del objeto de origen de eventos.

### <a name="return-value"></a>Valor devuelto

S_OK o cualquier valor HRESULT de error.

### <a name="remarks"></a>Observaciones

Una vez que se interrumpe la conexión, los eventos ya no se enrutarán a las funciones de controlador enumeradas en el mapa del receptor de eventos.

> [!NOTE]
> Si la clase deriva `IDispEventSimpleImpl` de varias clases, deberá desambiguar las llamadas a este método examinando la llamada con la clase base concreta que le interesa.

`DispEventAdvise`interrumpe una conexión que se estableció `pdiid`con el origen de eventos especificado en .

## <a name="idispeventsimpleimplgetidsofnames"></a><a name="getidsofnames"></a>IDispEventSimpleImpl::GetIDsOfNames

Esta implementación de `IDispatch::GetIDsOfNames` E_NOTIMPL.

```
STDMETHOD(GetIDsOfNames)(
    REFIID /* riid */,
    LPOLESTR* /* rgszNames */,
    UINT /* cNames */,
    LCID /* lcid */,
    DISPID* /* rgdispid */);
```

### <a name="remarks"></a>Observaciones

Consulte [IDispatch::GetIDsOfNames](/windows/win32/api/oaidl/nf-oaidl-idispatch-getidsofnames) en el Windows SDK.

## <a name="idispeventsimpleimplgettypeinfo"></a><a name="gettypeinfo"></a>IDispEventSimpleImpl::GetTypeInfo

Esta implementación de `IDispatch::GetTypeInfo` E_NOTIMPL.

```
STDMETHOD(GetTypeInfo)(
    UINT /* itinfo */,
    LCID /* lcid */,
    ITypeInfo** /* pptinfo */);
```

### <a name="remarks"></a>Observaciones

Consulte [IDispatch::GetTypeInfo](/windows/win32/api/oaidl/nf-oaidl-idispatch-gettypeinfo) en el Windows SDK.

## <a name="idispeventsimpleimplgettypeinfocount"></a><a name="gettypeinfocount"></a>IDispEventSimpleImpl::GetTypeInfoCount

Esta implementación de `IDispatch::GetTypeInfoCount` E_NOTIMPL.

```
STDMETHOD(GetTypeInfoCount)(UINT* /* pctinfo */);
```

### <a name="remarks"></a>Observaciones

Vea [IDispatch::GetTypeInfoCount](/windows/win32/api/oaidl/nf-oaidl-idispatch-gettypeinfocount) en el Windows SDK.

## <a name="idispeventsimpleimplinvoke"></a><a name="invoke"></a>IDispEventSimpleImpl::Invoke

Esta implementación de `IDispatch::Invoke` llamadas a los controladores de eventos enumerados en el mapa del receptor de eventos.

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

### <a name="remarks"></a>Observaciones

Consulte [IDispatch::Invoke](/windows/win32/api/oaidl/nf-oaidl-idispatch-invoke).

## <a name="idispeventsimpleimplunadvise"></a><a name="unadvise"></a>IDispEventSimpleImpl::Unadvise

Rompe la conexión con el origen de eventos representado por *pUnk*.

```
HRESULT Unadvise(IUnknown* pUnk);
```

### <a name="parameters"></a>Parámetros

*Punk*<br/>
[en] Un puntero `IUnknown` a la interfaz del objeto de origen de eventos.

### <a name="return-value"></a>Valor devuelto

S_OK o cualquier valor HRESULT de error.

### <a name="remarks"></a>Observaciones

Una vez que se interrumpe la conexión, los eventos ya no se enrutarán a las funciones de controlador enumeradas en el mapa del receptor de eventos.

> [!NOTE]
> Si la clase deriva `IDispEventSimpleImpl` de varias clases, deberá desambiguar las llamadas a este método examinando la llamada con la clase base concreta que le interesa.

`Unadvise`interrumpe una conexión que se estableció con `pdiid`el origen de eventos predeterminado especificado en .

`Unavise`rompe una conexión con el origen de eventos predeterminado, obtiene el IID del origen de eventos predeterminado del objeto según lo determinado por [AtlGetObjectSourceInterface](composite-control-global-functions.md#atlgetobjectsourceinterface).

## <a name="see-also"></a>Consulte también

[Estructura _ATL_FUNC_INFO](../../atl/reference/atl-func-info-structure.md)<br/>
[Clase IDispatchImpl](../../atl/reference/idispatchimpl-class.md)<br/>
[Clase IDispEventImpl](../../atl/reference/idispeventimpl-class.md)<br/>
[SINK_ENTRY_INFO](composite-control-macros.md#sink_entry_info)<br/>
[Información general de clases](../../atl/atl-class-overview.md)
