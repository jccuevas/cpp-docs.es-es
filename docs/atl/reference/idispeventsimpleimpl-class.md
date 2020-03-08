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
ms.sourcegitcommit: 3e8fa01f323bc5043a48a0c18b855d38af3648d4
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 03/06/2020
ms.locfileid: "78864765"
---
# <a name="idispeventsimpleimpl-class"></a>IDispEventSimpleImpl (clase)

Esta clase proporciona implementaciones de los métodos `IDispatch`, sin obtener información de tipos de una biblioteca de tipos.

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

## <a name="members"></a>Members

### <a name="public-methods"></a>Métodos públicos

|Nombre|Descripción|
|----------|-----------------|
|[IDispEventSimpleImpl:: Advise](#advise)|Establece una conexión con el origen de eventos predeterminado.|
|[IDispEventSimpleImpl::D ispEventAdvise](#dispeventadvise)|Establece una conexión con el origen del evento.|
|[IDispEventSimpleImpl::D ispEventUnadvise](#dispeventunadvise)|Interrumpe la conexión con el origen del evento.|
|[IDispEventSimpleImpl:: GetIDsOfNames](#getidsofnames)|Devuelve E_NOTIMPL.|
|[IDispEventSimpleImpl:: GetTypeInfo](#gettypeinfo)|Devuelve E_NOTIMPL.|
|[IDispEventSimpleImpl:: GetTypeInfoCount](#gettypeinfocount)|Devuelve E_NOTIMPL.|
|[IDispEventSimpleImpl:: Invoke](#invoke)|Llama a los controladores de eventos enumerados en el mapa del receptor de eventos.|
|[IDispEventSimpleImpl:: unaconseje](#unadvise)|Interrumpe la conexión con el origen de eventos predeterminado.|

## <a name="remarks"></a>Observaciones

`IDispEventSimpleImpl` proporciona una manera de implementar una interfaz dispinterface de eventos sin necesidad de proporcionar código de implementación para todos los métodos y eventos de esa interfaz. `IDispEventSimpleImpl` proporciona implementaciones de los métodos de `IDispatch`. Solo tiene que proporcionar implementaciones para los eventos que le interesa controlar.

`IDispEventSimpleImpl` funciona junto con el mapa del receptor de eventos en la clase para enrutar los eventos a la función de controlador adecuada. Para usar esta clase:

- Agregue una macro [SINK_ENTRY_INFO](composite-control-macros.md#sink_entry_info) a la asignación del receptor de eventos para cada evento de cada objeto que desee controlar.

- Proporcione información de tipo para cada evento pasando un puntero a una estructura de [_ATL_FUNC_INFO](../../atl/reference/atl-func-info-structure.md) como un parámetro a cada entrada. En la plataforma x86, el valor `_ATL_FUNC_INFO.cc` debe ser CC_CDECL con la función de devolución de llamada método de __stdcall.

- Llame a [DispEventAdvise](#dispeventadvise) para establecer la conexión entre el objeto de origen y la clase base.

- Llame a [DispEventUnadvise](#dispeventunadvise) para interrumpir la conexión.

Debe derivar de `IDispEventSimpleImpl` (con un valor único para *nID*) para cada objeto para el que necesite controlar eventos. Puede reutilizar la clase base desaconsejando un objeto de origen y, a continuación, avisar contra un objeto de origen diferente, pero el número máximo de objetos de origen que puede controlar un solo objeto al mismo tiempo está limitado por el número de clases base `IDispEventSimpleImpl`.

`IDispEventSimplImpl` proporciona la misma funcionalidad que [IDispEventImpl](../../atl/reference/idispeventimpl-class.md), salvo que no obtiene información de tipo sobre la interfaz de una biblioteca de tipos. Los asistentes generan código basado únicamente en `IDispEventImpl`, pero puede usar `IDispEventSimpleImpl` agregando el código manualmente. Use `IDispEventSimpleImpl` si no tiene una biblioteca de tipos que describa la interfaz de eventos o desea evitar la sobrecarga asociada con el uso de la biblioteca de tipos.

> [!NOTE]
> `IDispEventImpl` y `IDispEventSimpleImpl` proporcionan su propia implementación de `IUnknown::QueryInterface` que permite que cada `IDispEventImpl` o `IDispEventSimpleImpl` clase base actúe como una identidad COM independiente y, al mismo tiempo, permitir el acceso directo a miembros de clase en el objeto COM principal.

La implementación de ATL ATL de receptores de eventos ActiveX solo admite valores devueltos de tipo HRESULT o void de los métodos de control de eventos; no se admite ningún otro valor devuelto y su comportamiento es indefinido.

Para obtener más información, consulte [compatibilidad con IDispEventImpl](../../atl/supporting-idispeventimpl.md).

## <a name="inheritance-hierarchy"></a>Jerarquía de herencia

`_IDispEvent`

`_IDispEventLocator`

`IDispEventSimpleImpl`

## <a name="requirements"></a>Requisitos

**Encabezado:** atlcom. h

##  <a name="advise"></a>IDispEventSimpleImpl:: Advise

Llame a este método para establecer una conexión con el origen del evento representado por *pUnk*.

```
HRESULT Advise(IUnknown* pUnk);
```

### <a name="parameters"></a>Parámetros

*pUnk*<br/>
de Puntero a la interfaz `IUnknown` del objeto de origen del evento.

### <a name="return-value"></a>Valor devuelto

S_OK o cualquier valor HRESULT de error.

### <a name="remarks"></a>Observaciones

Una vez establecida la conexión, los eventos desencadenados desde *pUnk* se enrutarán a los controladores de la clase mediante el mapa del receptor de eventos.

> [!NOTE]
>  Si la clase se deriva de varias clases `IDispEventSimpleImpl`, deberá eliminar la ambigüedad de las llamadas a este método mediante el ámbito de la llamada con la clase base concreta que le interese.

`Advise` establece una conexión con el origen de eventos predeterminado, obtiene el IID del origen de eventos predeterminado del objeto determinado por [AtlGetObjectSourceInterface](composite-control-global-functions.md#atlgetobjectsourceinterface).

##  <a name="dispeventadvise"></a>IDispEventSimpleImpl::D ispEventAdvise

Llame a este método para establecer una conexión con el origen del evento representado por *pUnk*.

```
HRESULT DispEventAdvise(IUnknown* pUnk  const IID* piid);
```

### <a name="parameters"></a>Parámetros

*pUnk*<br/>
de Puntero a la interfaz `IUnknown` del objeto de origen del evento.

*piid*<br/>
Puntero al IID del objeto de origen del evento.

### <a name="return-value"></a>Valor devuelto

S_OK o cualquier valor HRESULT de error.

### <a name="remarks"></a>Observaciones

Posteriormente, los eventos desencadenados desde *pUnk* se enrutarán a los controladores de la clase mediante la asignación del receptor de eventos.

> [!NOTE]
>  Si la clase se deriva de varias clases `IDispEventSimpleImpl`, deberá eliminar la ambigüedad de las llamadas a este método mediante el ámbito de la llamada con la clase base concreta que le interese.

`DispEventAdvise` establece una conexión con el origen de eventos especificado en `pdiid`.

##  <a name="dispeventunadvise"></a>IDispEventSimpleImpl::D ispEventUnadvise

Interrumpe la conexión con el origen del evento representado por *pUnk*.

```
HRESULT DispEventUnadvise(IUnknown* pUnk  const IID* piid);
```

### <a name="parameters"></a>Parámetros

*pUnk*<br/>
de Puntero a la interfaz `IUnknown` del objeto de origen del evento.

*piid*<br/>
Puntero al IID del objeto de origen del evento.

### <a name="return-value"></a>Valor devuelto

S_OK o cualquier valor HRESULT de error.

### <a name="remarks"></a>Observaciones

Una vez interrumpida la conexión, los eventos ya no se enrutarán a las funciones de controlador enumeradas en el mapa del receptor de eventos.

> [!NOTE]
>  Si la clase se deriva de varias clases `IDispEventSimpleImpl`, deberá eliminar la ambigüedad de las llamadas a este método mediante el ámbito de la llamada con la clase base concreta que le interese.

`DispEventAdvise` interrumpe una conexión que se estableció con el origen de eventos especificado en `pdiid`.

##  <a name="getidsofnames"></a>IDispEventSimpleImpl:: GetIDsOfNames

Esta implementación de `IDispatch::GetIDsOfNames` devuelve E_NOTIMPL.

```
STDMETHOD(GetIDsOfNames)(
    REFIID /* riid */,
    LPOLESTR* /* rgszNames */,
    UINT /* cNames */,
    LCID /* lcid */,
    DISPID* /* rgdispid */);
```

### <a name="remarks"></a>Observaciones

Vea [IDispatch:: GetIDsOfNames](/windows/win32/api/oaidl/nf-oaidl-idispatch-getidsofnames) en el Windows SDK.

##  <a name="gettypeinfo"></a>IDispEventSimpleImpl:: GetTypeInfo

Esta implementación de `IDispatch::GetTypeInfo` devuelve E_NOTIMPL.

```
STDMETHOD(GetTypeInfo)(
    UINT /* itinfo */,
    LCID /* lcid */,
    ITypeInfo** /* pptinfo */);
```

### <a name="remarks"></a>Observaciones

Vea [IDispatch:: GetTypeInfo](/windows/win32/api/oaidl/nf-oaidl-idispatch-gettypeinfo) en el Windows SDK.

##  <a name="gettypeinfocount"></a>IDispEventSimpleImpl:: GetTypeInfoCount

Esta implementación de `IDispatch::GetTypeInfoCount` devuelve E_NOTIMPL.

```
STDMETHOD(GetTypeInfoCount)(UINT* /* pctinfo */);
```

### <a name="remarks"></a>Observaciones

Vea [IDispatch:: GetTypeInfoCount](/windows/win32/api/oaidl/nf-oaidl-idispatch-gettypeinfocount) en el Windows SDK.

##  <a name="invoke"></a>IDispEventSimpleImpl:: Invoke

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

### <a name="remarks"></a>Observaciones

Vea [IDispatch:: Invoke](/windows/win32/api/oaidl/nf-oaidl-idispatch-invoke).

##  <a name="unadvise"></a>IDispEventSimpleImpl:: unaconseje

Interrumpe la conexión con el origen del evento representado por *pUnk*.

```
HRESULT Unadvise(IUnknown* pUnk);
```

### <a name="parameters"></a>Parámetros

*pUnk*<br/>
de Puntero a la interfaz `IUnknown` del objeto de origen del evento.

### <a name="return-value"></a>Valor devuelto

S_OK o cualquier valor HRESULT de error.

### <a name="remarks"></a>Observaciones

Una vez interrumpida la conexión, los eventos ya no se enrutarán a las funciones de controlador enumeradas en el mapa del receptor de eventos.

> [!NOTE]
>  Si la clase se deriva de varias clases `IDispEventSimpleImpl`, deberá eliminar la ambigüedad de las llamadas a este método mediante el ámbito de la llamada con la clase base concreta que le interese.

`Unadvise` interrumpe una conexión que se estableció con el origen de eventos predeterminado especificado en `pdiid`.

`Unavise` interrumpe una conexión con el origen de eventos predeterminado, obtiene el IID del origen de eventos predeterminado del objeto determinado por [AtlGetObjectSourceInterface](composite-control-global-functions.md#atlgetobjectsourceinterface).

## <a name="see-also"></a>Consulte también

[_ATL_FUNC_INFO (estructura)](../../atl/reference/atl-func-info-structure.md)<br/>
[IDispatchImpl (clase)](../../atl/reference/idispatchimpl-class.md)<br/>
[IDispEventImpl (clase)](../../atl/reference/idispeventimpl-class.md)<br/>
[SINK_ENTRY_INFO](composite-control-macros.md#sink_entry_info)<br/>
[Información general sobre clases](../../atl/atl-class-overview.md)
