---
title: IDispEventImpl (clase)
ms.date: 11/04/2016
f1_keywords:
- IDispEventImpl
- ATLCOM/ATL::IDispEventImpl
- ATLCOM/ATL::IDispEventImpl::IDispEventImpl
- ATLCOM/ATL::IDispEventImpl::GetFuncInfoFromId
- ATLCOM/ATL::IDispEventImpl::GetIDsOfNames
- ATLCOM/ATL::IDispEventImpl::GetTypeInfo
- ATLCOM/ATL::IDispEventImpl::GetTypeInfoCount
- ATLCOM/ATL::IDispEventImpl::GetUserDefinedType
helpviewer_keywords:
- IDispEventImpl class
ms.assetid: a64b5288-35cb-4638-aad6-2d15b1c7cf7b
ms.openlocfilehash: e82a397b6d2abb66f773908c72a287c979e5ae1d
ms.sourcegitcommit: fcb48824f9ca24b1f8bd37d647a4d592de1cc925
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 08/15/2019
ms.locfileid: "69495929"
---
# <a name="idispeventimpl-class"></a>IDispEventImpl (clase)

Esta clase proporciona implementaciones de los `IDispatch` métodos.

> [!IMPORTANT]
>  Esta clase y sus miembros no se pueden usar en aplicaciones que se ejecutan en el Windows Runtime.

## <a name="syntax"></a>Sintaxis

```
template <UINT nID, class T,
    const IID* pdiid = &IID_NULL,
    const GUID* plibid = &GUID_NULL,
    WORD wMajor = 0,
    WORD wMinor = 0,
    class tihclass = CcomTypeInfoHolder>
class ATL_NO_VTABLE IDispEventImpl : public IDispEventSimpleImpl<nID, T, pdiid>
```

#### <a name="parameters"></a>Parámetros

*nID*<br/>
Identificador único para el objeto de origen. Cuando `IDispEventImpl` es la clase base de un control compuesto, utilice el identificador de recurso del control contenido deseado para este parámetro. En otros casos, use un entero positivo arbitrario.

*T*<br/>
Clase del usuario, que se deriva de `IDispEventImpl`.

*pdiid*<br/>
Puntero al IID de la interfaz dispinterface de eventos implementada por esta clase. Esta interfaz debe definirse en la biblioteca de tipos indicada por *plibid*, *wMajor*y *wMinor*.

*plibid*<br/>
Puntero a la biblioteca de tipos que define la interfaz de envío a la que apunta *pdiid*. Si **&AMP; GUID_NULL**, la biblioteca de tipos se cargará desde el objeto que origina los eventos.

*wMajor*<br/>
La versión principal de la biblioteca de tipos. El valor predeterminado es 0.

*wMinor*<br/>
La versión secundaria de la biblioteca de tipos. El valor predeterminado es 0.

*tihclass*<br/>
Clase usada para administrar la información de tipo para *T*. El valor predeterminado es una clase de tipo `CComTypeInfoHolder`; sin embargo, puede invalidar este parámetro de plantilla proporcionando una clase de un tipo distinto `CComTypeInfoHolder`de.

## <a name="members"></a>Miembros

### <a name="public-typedefs"></a>Definiciones de tipos públicas

|NOMBRE|DESCRIPCIÓN|
|----------|-----------------|
|[IDispEventImpl::_tihclass](../../atl/reference/idispeventimpl-class.md)|Clase usada para administrar la información de tipo. De forma predeterminada `CComTypeInfoHolder`,.|

### <a name="public-constructors"></a>Constructores públicos

|NOMBRE|DESCRIPCIÓN|
|----------|-----------------|
|[IDispEventImpl::IDispEventImpl](#idispeventimpl)|El constructor.|

### <a name="public-methods"></a>Métodos públicos

|NOMBRE|DESCRIPCIÓN|
|----------|-----------------|
|[IDispEventImpl::GetFuncInfoFromId](#getfuncinfofromid)|Busca el índice de función para el identificador de envío especificado.|
|[IDispEventImpl::GetIDsOfNames](#getidsofnames)|Asigna un solo miembro y un conjunto opcional de nombres de argumento a un conjunto correspondiente de DISPID enteros.|
|[IDispEventImpl::GetTypeInfo](#gettypeinfo)|Recupera la información de tipo de un objeto.|
|[IDispEventImpl::GetTypeInfoCount](#gettypeinfocount)|Recupera el número de interfaces de información de tipo.|
|[IDispEventImpl::GetUserDefinedType](#getuserdefinedtype)|Recupera el tipo básico de un tipo definido por el usuario.|

## <a name="remarks"></a>Comentarios

`IDispEventImpl`proporciona una manera de implementar una interfaz dispinterface de eventos sin necesidad de proporcionar código de implementación para todos los métodos y eventos de esa interfaz. `IDispEventImpl`proporciona implementaciones de los `IDispatch` métodos. Solo tiene que proporcionar implementaciones para los eventos que le interesa controlar.

`IDispEventImpl`funciona junto con el mapa del receptor de eventos en la clase para enrutar los eventos a la función de controlador adecuada. Para usar esta clase:

Agregue una macro [SINK_ENTRY](composite-control-macros.md#sink_entry) o [SINK_ENTRY_EX](composite-control-macros.md#sink_entry_ex) al mapa del receptor de eventos para cada evento de cada objeto que desee controlar. Cuando se `IDispEventImpl` usa como clase base de un control compuesto, se puede llamar a [AtlAdviseSinkMap](connection-point-global-functions.md#atladvisesinkmap) para establecer e interrumpir la conexión con los orígenes de eventos para todas las entradas de la asignación del receptor de eventos. En otros casos, o para un control mayor, llame a [DispEventAdvise](idispeventsimpleimpl-class.md#dispeventadvise) para establecer la conexión entre el objeto de origen y la clase base. Llame a [DispEventUnadvise](idispeventsimpleimpl-class.md#dispeventunadvise) para interrumpir la conexión.

Debe derivar de `IDispEventImpl` (mediante un valor único para *nID*) para cada objeto para el que necesite controlar eventos. Puede reutilizar la clase base desaconsejando un objeto de origen y, a continuación, avisar contra un objeto de origen diferente, pero el número máximo de objetos de origen que puede controlar un solo objeto al mismo tiempo está `IDispEventImpl` limitado por el número de clases base.

`IDispEventImpl`proporciona la misma funcionalidad que [IDispEventSimpleImpl](../../atl/reference/idispeventsimpleimpl-class.md), salvo que obtiene información de tipo sobre la interfaz de una biblioteca de tipos en lugar de que se proporcione como un puntero a una estructura [_ATL_FUNC_INFO](../../atl/reference/atl-func-info-structure.md) . Use `IDispEventSimpleImpl` cuando no tenga una biblioteca de tipos que describa la interfaz de eventos o desee evitar la sobrecarga asociada con el uso de la biblioteca de tipos.

> [!NOTE]
> `IDispEventImpl`y `IDispEventSimpleImpl` proporcionan su propia implementación de `IUnknown::QueryInterface` que permite `IDispEventImpl` que `IDispEventSimpleImpl` cada una de las clases base actúen como una identidad com independiente mientras se sigue permitiendo el acceso directo a los miembros de clase en el objeto com principal.

La implementación de ATL ATL de receptores de eventos ActiveX solo admite valores devueltos de tipo HRESULT o void de los métodos de control de eventos; no se admite ningún otro valor devuelto y su comportamiento es indefinido.

Para obtener más información, consulte [compatibilidad con IDispEventImpl](../../atl/supporting-idispeventimpl.md).

## <a name="inheritance-hierarchy"></a>Jerarquía de herencia

`_IDispEvent`

`_IDispEventLocator`

[IDispEventSimpleImpl](../../atl/reference/idispeventsimpleimpl-class.md)

`IDispEventImpl`

## <a name="requirements"></a>Requisitos

**Encabezado:** atlcom. h

##  <a name="getfuncinfofromid"></a>  IDispEventImpl::GetFuncInfoFromId

Busca el índice de función para el identificador de envío especificado.

```
HRESULT GetFuncInfoFromId(
    const IID& iid,
    DISPID dispidMember,
    LCID lcid,
    _ATL_FUNC_INFO& info);
```

### <a name="parameters"></a>Parámetros

*iid*<br/>
de Referencia al identificador de la función.

*dispidMember*<br/>
de IDENTIFICADOR de envío de la función.

*lcid*<br/>
de Contexto de la configuración regional del identificador de función.

*info*<br/>
de Estructura que indica cómo se llama a la función.

### <a name="return-value"></a>Valor devuelto

Valor HRESULT estándar.

##  <a name="getidsofnames"></a>  IDispEventImpl::GetIDsOfNames

Asigna un solo miembro y un conjunto opcional de nombres de argumento a un conjunto correspondiente de DISPID enteros, que se puede usar en las llamadas posteriores a [IDispatch:: Invoke](/windows/win32/api/oaidl/nf-oaidl-idispatch-invoke).

```
STDMETHOD(GetIDsOfNames)(
    REFIID riid,
    LPOLESTR* rgszNames,
    UINT cNames,
    LCID lcid,
    DISPID* rgdispid);
```

### <a name="remarks"></a>Comentarios

Vea [IDispatch:: GetIDsOfNames](/windows/win32/api/oaidl/nf-oaidl-idispatch-getidsofnames) en el Windows SDK.

##  <a name="gettypeinfo"></a>  IDispEventImpl::GetTypeInfo

Recupera la información de tipo de un objeto, que se puede usar después para obtener la información de tipo de una interfaz.

```
STDMETHOD(GetTypeInfo)(
    UINT itinfo,
    LCID lcid,
    ITypeInfo** pptinfo);
```

### <a name="remarks"></a>Comentarios

##  <a name="gettypeinfocount"></a>  IDispEventImpl::GetTypeInfoCount

Recupera el número de interfaces de información de tipo que proporciona un objeto (0 ó 1).

```
STDMETHOD(GetTypeInfoCount)(UINT* pctinfo);
```

### <a name="remarks"></a>Comentarios

Vea [IDispatch:: GetTypeInfoCount](/windows/win32/api/oaidl/nf-oaidl-idispatch-gettypeinfocount) en el Windows SDK.

##  <a name="getuserdefinedtype"></a>  IDispEventImpl::GetUserDefinedType

Recupera el tipo básico de un tipo definido por el usuario.

```
VARTYPE GetUserDefinedType(
    ITypeInfo* pTI,
    HREFTYPE hrt);
```

### <a name="parameters"></a>Parámetros

*pTI*<br/>
de Puntero a la interfaz [ITypeInfo](/windows/win32/api/oaidl/nn-oaidl-itypeinfo) que contiene el tipo definido por el usuario.

*hrt*<br/>
de Identificador de la descripción de tipo que se va a recuperar.

### <a name="return-value"></a>Valor devuelto

Tipo de variante.

### <a name="remarks"></a>Comentarios

Vea [ITypeInfo:: GetRefTypeInfo](/windows/win32/api/oaidl/nf-oaidl-itypeinfo-getreftypeinfo).

##  <a name="idispeventimpl"></a>  IDispEventImpl::IDispEventImpl

El constructor. Almacena los valores de los parámetros de plantilla de clase *plibid*, *pdiid*, *wMajor*y *wMinor*.

```
IDispEventImpl();
```

##  <a name="tihclass"></a>  IDispEventImpl::tihclass

Esta definición de tipo es una instancia del parámetro de plantilla de clase *tihclass*.

```
typedef tihclass _tihclass;
```

### <a name="remarks"></a>Comentarios

De forma predeterminada, la clase `CComTypeInfoHolder`es. `CComTypeInfoHolder`administra la información de tipo para la clase.

## <a name="see-also"></a>Vea también

[_ATL_FUNC_INFO (estructura)](../../atl/reference/atl-func-info-structure.md)<br/>
[IDispatchImpl (clase)](../../atl/reference/idispatchimpl-class.md)<br/>
[IDispEventSimpleImpl (clase)](../../atl/reference/idispeventsimpleimpl-class.md)<br/>
[SINK_ENTRY](composite-control-macros.md#sink_entry)<br/>
[SINK_ENTRY_EX](composite-control-macros.md#sink_entry_ex)<br/>
[SINK_ENTRY_INFO](composite-control-macros.md#sink_entry_info)<br/>
[Información general sobre clases](../../atl/atl-class-overview.md)
